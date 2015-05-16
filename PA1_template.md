# Reproducible Research: Peer Assessment 1


## Loading and preprocessing the data

```r
# load up our libraries
library(dplyr)
library(ggplot2)
```


```r
# unzip the data file
unzip("activity.zip")
# read the csv
data <- read.csv("activity.csv")
dataTable <- tbl_df(data)
```

## What is mean total number of steps taken per day?

For this part of the assignment, you can ignore the missing values in
the dataset.

1. Make a histogram of the total number of steps taken each day


```r
# ignore missing values
data2 <- data[complete.cases(data),]
# plot our histogram
g <- ggplot(data2, aes(date, steps))
g + geom_bar(stat="identity") + xlab("Date") + ylab("Total Steps") + ggtitle("Total Steps by Date") + theme(axis.text.x=element_text(angle=90,hjust=1,vjust=0.5))
```

![](PA1_template_files/figure-html/unnamed-chunk-3-1.png) 

2. Calculate and report the **mean** and **median** total number of steps taken per day


```r
# get a vector with total steps per day
totalStepsPerDay <- tapply(data2$steps, data2$date, sum)
# then we can calculate mean and median on it
meanSteps <- mean(totalStepsPerDay, na.rm = TRUE)
medianSteps <- median(totalStepsPerDay, na.rm = TRUE)
```

The mean is: **10766.19**   
The median is: **10765**





## What is the average daily activity pattern?



## Imputing missing values



## Are there differences in activity patterns between weekdays and weekends?
