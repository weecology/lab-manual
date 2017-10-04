This is a brain dump from shortly after I (Ethan) received the Moore Foundation grant (plus a few additions over the last year) for cool things to work on in the forecasting space. Feel free to add more ideas for work in this area.

## Projects

* Forecasting baselines for ecology
    * Develop predictions for S, N, E and n_i based on long-term average, last
      years value, and the most recent value w/lags (i.e., how does the value in
      one year predict the next year, the year after that, etc.)
* Comparing different levels of forecasting models
    * Compare baseline models, time-series only models (i.e., only the data on
      the dynamics of the response), exogenous predictors, and time-series +
      exogenous predictors
    * Do this across many time scales, since there will likely be a transition
      from baseline and time-series models doing well, to exogenous predictors
      being important, as the time scale increases. If this isn't the case it's
      likely a sign that the exogenous predictors are simply absorbing
      spatiotemporal variance rather than being meaningful predictors.
* Comparing process based and data-driven approaches
    * Species distribution models using hind-casting are an obvious starting
      point
    * Compare things like MaxEnt and Mistnet to models like those by Michael
      Kearney
* Do the parameters/predictions of SDMs change if we fit them at different years
  within a time-series.
    * So, is the BBS SDM for species x the same if we fit it
      in 1980, 1990, 2000, and 2010. If so that's a good sign, if not, it indicates
      that they aren't working very well.
    * This could be combined with hindcasting within the same time-series, since
      they are really commenting on the same thing.
	* See also Blois et al. 2013 in Ecography
* Try a big open online collaboration
    * One natural way to do this is to generate the question and the data and
      then invite folks to contribute models for forecasting. Instead of a
      competition it's a collaboration to find the best approaches to
      forecasting a particular outcome, coordinated via the modern web.
    * Could use or last allow an iterative system of model development like
      Mathworks uses.
    * Could expand on work out of UW/NWFSC (see Ward et al. 2014 
* Predicting BBS/CBC using eBird
  * this becomes an election (Nate Silver) style prediction. This was originally
  suggested by Andy Kleinhesselink
* Open forecasting project (competitiony)
    * One main paper setting up the goals and the forecasting and the data
    * Every group that wants to participate writes a small Methods + Results
      paper with their forecasting approaches and results
	* A central conclusion/synthesis paper discussing and comparing results
	* F1000 or PeerJ would probably go for something like this, and would
	support commenting and interaction among the authors of the different
	forecasts
* Paleo forecasting
    * Can we do forecasting evaluation, and make actual forecasts, at longer time-
      scales using paleo data
    * Can we combine paleo and modern data to improve our forecasts at intermediate
      time-scales
    * Neptune Sandbox Berlin (http://www.nsb-mfn-berlin.de/) has a database of paleo 
      forams. Might only be occurrence data, though.
* Iterative forecasting
    * Assess benefits and approaches to iterative forecasting by starting with a
      small chunk of time-series (in, say, BBS) and applying iterative tools as each
      new year of data comes in.

* Obs:pred plots/R^2 equivalent to AUC, but how does this compare to statis
* Look for spatial patterns in forecastability or performance of different
modeling approaches
* Phenology: Remote sensing (MODIS) + PhenoCam + National Phenology Network +
  Flux towers
* Track how models change over time to gain understanding of what we've learned
  about science [Melissa from #ecoforecast]

* sophisticated analysis of trends in time-series
    * increasing vs. decreasing vs. flat
    * are there rapid transitions?
* compare temporal environmental correlations in different portions of the
time-series
    * is relationship with environment the same 20 years ago as now?

## Factors relevant to ecological forecasting

Some of these can be measured, others may have to be inferred from the
data. There is a general expectation of interactions among the factors. e.g.,
the influence of species x on species y will depend on the climate, habitat,
etc.

* Climate
* Weather
* Land use
* Habitat type
* Soils (especially for plants, but these have run on influences for other
  organisms)
* Human population density
* Abundances of other species
  * within the same taxon
  * in other taxa (e.g., food, predators, habitat)
    * This will almost certainly needed to be predicated from non-spatially
      overlapping datasets so there will be additional measurement error
      coming in through the spatial prediction component
* Regional values of above + connectivity

## Modeling

* Is the simplest approach to incorporating both spatial and temporal data
  simply to include both spatial data (w/lags) and local temporal data and hand
  all of this to a ML algorithm and let it sort out the value of the spatial vs
  temporal data for making the prediction?
* The overall spatiotemporal modeling goal is to allow different components to
  be weighted differently, with weights fit to maximize prediction. Likely the
  dynamics of the localish sites will be more important than that
  spatial/dynamic components of sites further away.
* One really simple approach to this is just to have an indicator variable for
  local temporal vs. spatial (or non-local) data. That way at least the forms
  could differ.
* Look into Clark's (and others) "joint, dynamic" SDMs.
* In addition to the time-scale of the forecast being important for determining
  method, the time-span of the available data will also be important. If only
  short time-span data then simple time-series approaches (mean, naive) or
  spatial will be all that is possible. Can use these to do our best for full
  dataset predictions. As time-span of data gets longer more methods will become
  available and we need to figure out what works best.
* Model averaging would be a simple way to combine spatial and temporal
  forecasts. Measure how well they do at different time-scales for
  forecasting. Average the two models with a weight that changes as a function
  of time to forecast. This would provide a smooth transition from one to the
  other assuming that the hypothesis of relative importance of time vs space is
  as expected.
* Generate some high quality controls for investigator effects by using only
  time-series with the same investigator consistently through time
* Precise environmental variables at date of forecast are only available by
  forecasting them, which introduces another source of uncertainty, but measured
  values a few days/weeks/months out are available for short-term forecasting so
  models could be based on those values. This restricts to short-term
  forecasting but eliminates uncertainty.
* Add abundance in the previous year as a predictor to make spatial models state space models

## Blog posts

* Why we need to do more short-term forecasting in ecology
  * Evaluate our ability to make forecasts
  * Get better at forecasting by getting rapid feedback (citations from
    forecasting book that forecasters get better w/feedback)
* On testing ecological forecasting - separating the ecological modeling from
  the features
* Data-driven vs. theory driven approaches to forecasting in ecology
