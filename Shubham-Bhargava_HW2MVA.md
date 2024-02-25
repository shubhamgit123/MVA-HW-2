Homework 2
================
Shubham Bhargava
2024-02-11

``` r
library(readxl)
News_Website_Dataset <- read_excel("News Website Dataset.xlsx")
#View(News_Website_Dataset)

# correlation  and coefficient B/W Total_revenue and Total Sessions
correlation_coefficient2 <- cor(News_Website_Dataset$Total_revenue, News_Website_Dataset$Total_Sessions)
print(correlation_coefficient2)
```

    ## [1] 1

``` r
plot(News_Website_Dataset$Total_Sessions, News_Website_Dataset$Total_revenue,
     xlab = "Total Sessions", ylab = "Total Revenue",
     main = "Scatter Plot of Total Revenue vs. Total Sessions")

abline(lm(News_Website_Dataset$Total_revenue ~ News_Website_Dataset$Total_Sessions), col = "green")
```

![](Shubham-Bhargava_HW2MVA_files/figure-gfm/unnamed-chunk-1-1.png)<!-- -->

``` r
correlation_coefficient <- cor(News_Website_Dataset$Total_revenue, News_Website_Dataset$Avg_Session_Duration)

plot(News_Website_Dataset$Avg_Session_Duration, News_Website_Dataset$Total_revenue,
     xlab = "Average Session Duration", ylab = "Total Revenue",
     main = "Scatter Plot of Total Revenue vs. Avg Session Duration")

abline(lm(News_Website_Dataset$Total_revenue ~ News_Website_Dataset$Avg_Session_Duration), col = "purple")
```

![](Shubham-Bhargava_HW2MVA_files/figure-gfm/unnamed-chunk-2-1.png)<!-- -->

``` r
print(paste("Correlation Coefficient between Total Revenue and Avg Session Duration:", correlation_coefficient))
```

    ## [1] "Correlation Coefficient between Total Revenue and Avg Session Duration: 0.536707214155583"

## Homework 2

<b>1. Bivariate Analysis:</b>
<p>
<b>Question :</b> What differences exist in total revenue between
various traffic sources?
</p>
<p>
<b>Visualization:</b> Box plot showing Total Revenue by Traffic Source
</p>

``` r
library(ggplot2)
ggplot(News_Website_Dataset, aes(x = Traffic_Source, y = Total_revenue, fill = Traffic_Source)) +
  geom_boxplot() +
  labs(title = "Total Revenue by Traffic Source",
       x = "Traffic Source",
       y = "Total Revenue")
```

![](Shubham-Bhargava_HW2MVA_files/figure-gfm/unnamed-chunk-3-1.png)<!-- -->
<p>
With certain traffic sources having larger median incomes than others,
the box plot illustrates differences in overall revenue across various
traffic sources.
</p>
<b>2. Univariate Analysis:</b>
<p>
<b>Question :</b> How is the overall revenue divided up?
</p>
<p>
<b>Visualization:</b> Histogram showing Total Revenue
</p>

``` r
library(ggplot2)
hist(News_Website_Dataset$Total_revenue, 
     main = "Distribution of Total Revenue",
     xlab = "Total Revenue",
     ylab = "Frequency",
     col = "purple",
     border = "yellow")
```

![](Shubham-Bhargava_HW2MVA_files/figure-gfm/unnamed-chunk-4-1.png)<!-- -->
<p>
The total income distribution is displayed in the histogram. This
indicates that income is dispersed to the right and resides primarily in
the lower ranges. Small gains are deemed to be excessive.
</p>
<b>3. Multivariate Analysis:</b>
<p>
<b>Question :</b>What differences exist in overall income between
various device categories and times of day?
</p>
<p>
<b>Visualization:</b> Line plot Showing Total Revenue by Time of Day,
color by Device Category
</p>

``` r
library(ggplot2)
ggplot(News_Website_Dataset, aes(x = Time_of_Day, y = Total_revenue, color = Device_Category)) +  geom_line(size = 2.5) +
  labs(title = "Total Revenue by Time of Day (Colored by Device Category)",
       x = "Time of Day",
       y = "Total Revenue")
```

    ## Warning: Using `size` aesthetic for lines was deprecated in ggplot2 3.4.0.
    ## ℹ Please use `linewidth` instead.
    ## This warning is displayed once every 8 hours.
    ## Call `lifecycle::last_lifecycle_warnings()` to see where this warning was
    ## generated.

![](Shubham-Bhargava_HW2MVA_files/figure-gfm/unnamed-chunk-5-1.png)<!-- -->
<p>
With a distinct device category represented by each line, the line plot
shows how total revenue changes during the day. Based on device usage
and time of day, it aids in identifying revenue trends.
</p>
