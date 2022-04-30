---
title: "Publication Quality Figures"
linkTitle: "Publication Figures"
type: book
summary: >
  How to make publication quality figures
weight: 1
---

Journals (often) have strict yet confusing requirements for how they want manuscript figures to look. Here are some tips for how to handle this. [Using R]

## Getting the right size/resolution

Journals often have size limits and recommended resolution for figures (e.g. no more than 6 in wide and 7 in tall, 600dpi resolution). Good news: if you use the ggplot2 package to make plots, you can then save your figures using [ggsave()](http://ggplot2.tidyverse.org/reference/ggsave.html)! There are options for width, height, and dpi. And since the resulting file will almost certainly be larger than the journal's size limit, use the argument compression='lzw' to make it smaller.

## Multi-part figures

I have found the package [multipanelfigure](https://cran.r-project.org/web/packages/multipanelfigure/multipanelfigure.pdf) to be very useful. It allows you to make a multi-part figure by putting together any kind of objects: ggplot figures, base R figures, pngs, whatever. There is a fairly easy to understand example on their [GitHub repo](https://github.com/cran/multipanelfigure), and I used it in [line 188 of this script](https://github.com/emchristensen/Extreme-events-LDA/blob/master/rodent_LDA_analysis.r). The general idea is you create a grid object with the function multi_panel_figure(), in which you specify things like size of columns/rows:

`grid_object <- multi_panel_figure(width = c(50,50), height = c(50,50))`

and then fill the grid one cell at a time

`grid_object %<>% fill_panel(ggplot_figure, row = 1, column = 1)`

`grid_object %<>% fill_panel(png_path, row = 1, column = 2)`

You can then use the function save_multi_panel_figure() which is similar to ggsave(), and again specify dpi and compression. Getting it to the right size is harder, I ended up playing around with column and row sizes until it fit. 