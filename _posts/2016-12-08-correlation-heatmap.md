---
title: "Correlation Heat Map"
layout: default
---



## The Data
Let's use the `attitude` dataset that comes preloaded with R. We can read specifics in the R documentation (`?attitude`), but the data frame presents the aggregated results from questionnaires distributed in 30 departments at a financial organization. The data looks like this:


```r
head(attitude)
```

```
##   rating complaints privileges learning raises critical advance
## 1     43         51         30       39     61       92      45
## 2     63         64         51       54     63       73      47
## 3     71         70         68       69     76       86      48
## 4     61         63         45       47     54       84      35
## 5     81         78         56       66     71       83      47
## 6     43         55         49       44     54       49      34
```

## Correlation
We could be interested in correlations among the full dataset, or among a subset of variables. In both cases, use the base R function `cor` to calculate correlation coefficients (the default is the Pearson coefficient). To calculate the correlation among all columns:


```r
fullCorrelationMatrix <- cor(attitude)
fullCorrelationMatrix
```

```
##               rating complaints privileges  learning    raises  critical
## rating     1.0000000  0.8254176  0.4261169 0.6236782 0.5901390 0.1564392
## complaints 0.8254176  1.0000000  0.5582882 0.5967358 0.6691975 0.1877143
## privileges 0.4261169  0.5582882  1.0000000 0.4933310 0.4454779 0.1472331
## learning   0.6236782  0.5967358  0.4933310 1.0000000 0.6403144 0.1159652
## raises     0.5901390  0.6691975  0.4454779 0.6403144 1.0000000 0.3768830
## critical   0.1564392  0.1877143  0.1472331 0.1159652 0.3768830 1.0000000
## advance    0.1550863  0.2245796  0.3432934 0.5316198 0.5741862 0.2833432
##              advance
## rating     0.1550863
## complaints 0.2245796
## privileges 0.3432934
## learning   0.5316198
## raises     0.5741862
## critical   0.2833432
## advance    1.0000000
```

Select a subset of columns by position (column number) or variable name.


```r
partialCorrelationMatrix <- cor(attitude[c("rating","complaints","privileges")])
partialCorrelationMatrix
```

```
##               rating complaints privileges
## rating     1.0000000  0.8254176  0.4261169
## complaints 0.8254176  1.0000000  0.5582882
## privileges 0.4261169  0.5582882  1.0000000
```

```r
partialCorrelationMatrix <- cor(attitude[1:3])
partialCorrelationMatrix
```

```
##               rating complaints privileges
## rating     1.0000000  0.8254176  0.4261169
## complaints 0.8254176  1.0000000  0.5582882
## privileges 0.4261169  0.5582882  1.0000000
```

Then take a correlation matrix (eg. `partialCorrelationMatrix`) and reshape the data frame so that it's in _long format_; each possible variable type (or combination of) has its own row with columns for variables and another for values of those variables. There are a few ways of doing this, including `melt` in the `reshape2` package and `gather` in the `tidyr` package. This example uses the former. See more about `melt` [here](http://seananderson.ca/2013/10/19/reshape.html) and [here](http://www.cookbook-r.com/Manipulating_data/Converting_data_between_wide_and_long_format/). See what the _molten_ data frame looks like.


```r
require(reshape2)
```

```
## Loading required package: reshape2
```

```r
moltenCorrelationMatrix<-melt(partialCorrelationMatrix)
moltenCorrelationMatrix
```

```
##         Var1       Var2     value
## 1     rating     rating 1.0000000
## 2 complaints     rating 0.8254176
## 3 privileges     rating 0.4261169
## 4     rating complaints 0.8254176
## 5 complaints complaints 1.0000000
## 6 privileges complaints 0.5582882
## 7     rating privileges 0.4261169
## 8 complaints privileges 0.5582882
## 9 privileges privileges 1.0000000
```

Make sure that your first two columns are factors.


```r
moltenCorrelationMatrix$Var1<-as.factor(moltenCorrelationMatrix$Var1)
moltenCorrelationMatrix$Var2<-as.factor(moltenCorrelationMatrix$Var2)
```

Use `ggplot2` to create a basic heat map. The way this works is that `ggplot2` ascribes values from the data frame to the plot. In this case, the x- and y-axes are variable names and `fill` is the correlation coefficient. 


```r
require(ggplot2)
```

```
## Loading required package: ggplot2
```

```r
ggplot(data = moltenCorrelationMatrix) +
  geom_tile(aes(x = Var2, y = Var1, fill = value))
```

<img src="{{ site.url }}/images/correlation-heatmap-unnamed-chunk-7-1.png" title="plot of chunk unnamed-chunk-7" alt="plot of chunk unnamed-chunk-7" style="display: block; margin: auto;" />{: .center-image }

Ugh, it's so ugly! Ok, ok. Fine tune it so that your color gradient scales from (-1,1) and is intuitively appealing (blue,red). In this particular example, there's no negative correlations so nothing shows up blue.


```r
require(ggplot2)
ggplot(data = moltenCorrelationMatrix) +
  geom_tile(aes(x = Var2, y = Var1, fill = value)) + 
  scale_fill_gradient2(low = "blue", 
                       high = "red",
                       mid = "white", 
                       midpoint = 0, 
                       limit = c(-1,1),
                       name = "Correlation\n(Pearson)")
```

<img src="{{ site.url }}/images/correlation-heatmap-unnamed-chunk-8-1.png" title="plot of chunk unnamed-chunk-8" alt="plot of chunk unnamed-chunk-8" style="display: block; margin: auto;" />{: .center-image }
  
Fine tune the axes even more, adjusting the orientation of axis text, and suppress those pesky `Var1` and `Var2`.

<img src="{{ site.url }}/images/correlation-heatmap-unnamed-chunk-9-1.png" title="plot of chunk unnamed-chunk-9" alt="plot of chunk unnamed-chunk-9" style="display: block; margin: auto;" />{: .center-image }

Another thing I often want to do is reorganize the axes by values of a particular column. You can use different functions to do this, but you need to reorganize the levels underlying the factors Var1 or Var2. One example of how you would do this by hand:


```r
# rename to be succinct
m <- fullCorrelationMatrix 
m <- melt(m)

# change factor levels
m$Var1 <- factor(m$Var1, levels=(c("complaints","rating","learning",
                               "raises","advance","critical","privileges")))
m$Var2 <- factor(m$Var2, levels=(c("complaints","rating","learning",
                               "raises","advance","critical","privileges")))
out<-ggplot(data = m) +
  geom_tile(aes(x = Var2, y = Var1, fill = value)) + 
  scale_fill_gradient2(low = "blue", 
                       high = "red",
                       mid = "white", 
                       midpoint = 0, 
                       limit = c(-1,1),
                       name = "Correlation\n(Pearson)") +
  theme(axis.text.x = element_text(angle=45, vjust=1, size=11, hjust=1),
        axis.title.x=element_blank(), 
        axis.title.y=element_blank()) +
  coord_equal() + 
  scale_x_discrete(expand = c(0,0)) + 
  scale_y_discrete(expand = c(0,0))
out
```

<img src="{{ site.url }}/images/correlation-heatmap-unnamed-chunk-10-1.png" title="plot of chunk unnamed-chunk-10" alt="plot of chunk unnamed-chunk-10" style="display: block; margin: auto;" />{: .center-image }

There's the super-quick way of doing this, too. Here, `qplot` is a useful way of successfully implementing verbose `ggplot2` code while foregoing some of the detailed control. 

<img src="{{ site.url }}/images/correlation-heatmap-unnamed-chunk-11-1.png" title="plot of chunk unnamed-chunk-11" alt="plot of chunk unnamed-chunk-11" style="display: block; margin: auto;" />{: .center-image }

