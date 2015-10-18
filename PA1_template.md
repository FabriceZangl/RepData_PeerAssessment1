# Reproducible Research: Peer Assessment 1


## Loading and preprocessing the data
First part of the assignment 1 - Getting and Cleaning the data:

```r
url <- "https://d396qusza40orc.cloudfront.net/repdata%2Fdata%2Factivity.zip"
download.file(url, "Course5Assignment1.zip")
unzip("Course5Assignment1.zip")
df <- read.csv("activity.csv", sep=",", na.strings = "NA", stringsAsFactors = F, colClasses = c(steps = "numeric", date = "character", interval = "numeric"))
df$date <- as.Date(df$date, "%Y-%m-%d")
```


## What is mean total number of steps taken per day?
Second part of the assignment 1 - Reporting on the total number of steps:

- calculating the sum of steps per day
- plotting them into a histogram
- reporting the mean and median of the number of steps

```r
pivot_df <- aggregate(steps ~ date, df, sum)
head(pivot_df, 3)
```

```
##         date steps
## 1 2012-10-02   126
## 2 2012-10-03 11352
## 3 2012-10-04 12116
```

```r
barplot(pivot_df$steps, main = "Total Steps per Day", col="red", ylab="# of steps")
mean_df <- mean(pivot_df$steps)
print(paste("The MEAN of the total number of steps taken per day is ", mean_df,"(see green dotted line)."))
```

```
## [1] "The MEAN of the total number of steps taken per day is  10766.1886792453 (see green dotted line)."
```

```r
abline(h = mean_df, lwd = 3, lty = 3, col = "green")
```

![](PA1_template_files/figure-html/unnamed-chunk-2-1.png) 

```r
median_df <- median(pivot_df$steps)
print(paste("The MEDIAN of the total number of steps taken per day is ", median_df,"(see blue dashed line)."))
```

```
## [1] "The MEDIAN of the total number of steps taken per day is  10765 (see blue dashed line)."
```

```r
barplot(pivot_df$steps, main = "Total Steps per Day", col="red", ylab="# of steps")
abline(h = median_df, lwd = 2, lty = 2, col = "blue")
```

![](PA1_template_files/figure-html/unnamed-chunk-2-2.png) 


## What is the average daily activity pattern?
What is the average daily activity pattern?

1. Make a time series plot (i.e. type = "l") of the 5-minute interval (x-axis) and the average number of steps taken, averaged across all days (y-axis)

2. Which 5-minute interval, on average across all the days in the dataset, contains the maximum number of steps?



## Imputing missing values




## Are there differences in activity patterns between weekdays and weekends?


