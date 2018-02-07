
**Overview**

The basic idea of parallelization is the running of computational tasks simultaneously, as opposed to sequentially (or "in sequence" as opposed to "in parallel"). To do this, the computer needs to be able to split code into pieces that can run independently and then be joined back together as if they had been run sequentially.  The parts of the computer that run the pieces of code are processing units and are typically called "cores". 

The `doParallel` package is (as far as I'm currently aware) the most platform-general and robust parallel package available in R. There is more functionality for Unix-alikes in the `parallel` package (see link below), but that doesn't function on Windows machines. 

```
library(doParallel)
```

**Cores and Clusters** 

At the outset, it's important to know how many cores you have available, which the `detectCores()` function returns. However, the value returned includes "hyperthreaded cores" (aka "logical cores"), which include further computational divvyings of the physical cores.

```
detectCores()

detectCores(logical = FALSE)
```

Although hyperthreaded cores are available, they often do not show speed gains in R. However, as with everything parallel in R, it's best to actually test that on the problem you're working on, as there will be gains in certain situations.

At the user-interface level, we only interact at a single point, yet the code needs to access multiple cores at once. To achieve this, we have the concept of a "cluster", which represents a parallel set of copies of R running across multiple cores (including across physical sockets). We create a cluster using the `makeCluster` function and register the backend using the `registerDoParallel` function:

```
ncores <- detectCores(logical = FALSE)

cl <- makeCluster(floor(0.75 * ncores))
registerDoParallel(cl)

stopCluster(cl)
```

Here, I've stopped the cluster explicitly using `stopCluster`, which frees up the computational resources. The cluster will be automatically stopped when you end your R instance, but it's a good habitat to be in to stop any clusters you make (even if you don't register the backend).

**foreach and %dopar%**

Parallelization in `doParallel` happens via the combination of the `foreach` and `%dopar%` operators in a fashion similar to `for` loops. Rather than `for(variable in values) {expression}`, we have `foreach(variable = values, options) %dopar% {expression}`. Thus, the basic code block of a `foreach` parallel loop is

```
cl <- makeCluster(cores_for_cluster)
registerDoParallel(cl)
foreach(variable = values, options) %dopar% {
  expression
}
stopCluster(cl)
```

Note that there can be multiple variable arguments (*e.g.*, `foreach(i = 1:10, j = 11:20) %dopar% {}`), although no variables are recycled, so the smallest number of values across variables is used. 

Each of the instances of a `foreach` is referred to as a "task" (a key word, especially in terms of error checking, see link below).

An important distinction between `foreach` and `for` is that `foreach` returns a value (by default, a list), whereas `for` causes side effects. Compare the following:

```
cl <- makeCluster(floor(0.75 * ncores))
registerDoParallel(cl)
out <- foreach(i = 1:10) %dopar% {
  i + rnorm(1, i, i)
}
stopCluster(cl)
```
vs.

```
out <- vector("list", 10)
for(i in 1:10){
  out[[i]] <- i + rnorm(1, i, i)
```

`foreach` creates `out`; `for` modifies it. 

There are a handful of option arguments in `foreach` that are really critical for anything beyond trivial computation:
* `.packages` passes the libraries down to the cluster of Rs. If you don't include package names and you use a package-derived function, it won't work
* `.combine` dictates how the output is combined, defaulting to a list, but allowing lots of flexibility including mathematical operations. If needed, the `.init` option allows you to initialize the value (for example with 0 or 1).
* `.inorder` sets whether the combination happens based on the order of inputs. If the order isn't important, setting this to `FALSE` can give performance gains.
* `.errorhandling` determines what happens when a task fails (see link below for using `tryCatch` within tasks).

In addition to `%dopar%`, there is a sequential operator for use with `foreach`, and it is simply `%do%`. Replacing `%dopar%` with `%do%` will cause the code to run in-order, as if you did not initiate a cluster. Similarly, you can run `foreach` and `%dopar%` without having made a cluster, but the code will be run sequentially.

**Nesting foreach loops**

Nested loops can often be really powerful for computation. `doParallel` has a special operator that combines two `foreach` objects in a nested manner: `%:%`. This operator causes the outer most `foreach` to be evaluated over its variables' values, which are then passed down into the next innermost `foreach`. That `foreach` iterates over its variables' values for each value of the outer `foreach` variables.

```
out <- foreach(i = 1:10) %:%
         foreach(j = 1:100) %dopar% {
          i * j^3
         }
out
```

The `.combine` option is really important to pay attention to with nested `foreach` loops, as it will allow you to flexibly structure the data. The above version produces a list (length 10) of lists (length 100).

**References** 

* [example of foreach on Windows, including performance metrics](https://beckmw.wordpress.com/2014/01/21/a-brief-foray-into-parallel-processing-with-r/ )
* [software carpentry tutorial](http://resbaz.github.io/r-intermediate-gapminder/19-foreach.html)
* [parallel error compendium](https://github.com/tobigithub/R-parallel/wiki/R-parallel-Errors) 
* [setting up tryCatch inside foreach](https://stackoverflow.com/questions/39262612/r-show-error-and-warning-messages-in-foreach-dopar) 
* [real world example of parallelization utility: likelihood profiling](https://www3.nd.edu/~steve/computing_with_data/22_parallel/parallel_foreach.html)
* [real world example of parallelization utility: database querying](https://stochasticcoder.com/2016/01/12/r-using-doparallel-to-significantly-speedup-database-retrieval/) 
* [details of mc--- functions, useful for Unix-alikes](http://www2.stat.duke.edu/~cr173/Sta523_Fa14/parallelization.html)
* [example parallel speed test](https://github.com/benporter/parallel-speed-test-R )
