Peer review assignment_1
Reproducible research

Setting up the library for the ggplot and lattice

```{r setup, include=FALSE}
knitr::opts_chunk$set(echo = TRUE)
library(gg_plot2)
library(lattice)
```

Setting up and preprocessing the data
```{r}
data <- read.csv(unzip("activity.zip", "activity.csv"))
data <- transform(data, date = as.Date(date))
```
......................................................................................................................................................

 What is mean total number of steps taken per day?

Create the variable name `present_data` which do not include missing values
```{r}
present_data <- data[!is.na(data[1]),]
```

We will define here some of the functions that could aid in the later calculations
```{r}
acquire_steps_per_day <- function(d) {
  steps_per_day <- tapply(d$steps, d$date, sum)
 steps_per_day <-
   data.frame(cbind(day = names(steps_per_day), steps = steps_per_day))
  steps_per_day <- transform(steps_per_day, day = as.Date(day))
  steps_per_day <- transform(steps_per_day, steps = as.numeric(as.character(steps)))
}




We will get the mean total number of steps taken per day:

get_steps_per_interval <- function(d) {
  steps_per_interval <- tapply(d$steps, d$interval, mean)
  
We will define the average_steps_per_interval to the data frame

  steps_per_interval <- 
    data.frame(cbind(interval = names(steps_per_interval), steps = steps_per_interval))
    steps_per_interval <- transform(steps_per_interval, interval = as.numeric(as.character(interval)))
  steps_per_interval <- transform(steps_per_interval, steps = as.numeric(as.character(steps)))
}
```

1. Calculate the total steps taken per day:
```{r}
total_steps_per_day_with_present_data <- get_steps_per_day(present_data)
```

2. A histogram of total steps taken per day:
```{r echo=FALSE}
gg_plot(total_steps_per_day_with_present_data, axes(x = day, y = steps)) + geom_bar(stat = 'identity') + ylab("total steps")
```

3. Calculate the mean and median of the total steps taken per day:
```{r}
mean_avaialble_steps <- mean(total_steps_per_day_with_present_data$steps)
median_available_steps <- median(total_steps_per_day_with_present_data$steps)
```

The mean and median of the total steps taken per day are 

`r formatC(mean_present_steps , small.mark=",")`
`r formatC(median_present_steps , small.mark=",")`

.............................................................................................................................................................................................................
 
 What is the average daily activity pattern?

```{r}
average_steps_per_interval_with_present_data <- get_steps_per_interval(present_data)
```
A plot of the average steps taken per interval:
```{r echo=FALSE}
plot(average_steps_per_interval_with_present_data$interval, average_steps_per_interval_with_present_data$steps, type = "l", xlab = "interval", ylab = "average steps")
```
..............................................................................................................................................................................................................

Find the interval that has the maximum average steps:

```{r}
is_max <-
  average_steps_per_interval_with_present_data$steps ==
    max(average_steps_per_interval_with_present_data$steps)
max_per_interval <- average_steps_per_interval_with_present_data[is_max,]
interval_for_max <- max_per_interval$interval
```
The interval with the maximum average steps is **`r interval_for_max`**

.........................................................................................................................................................

## Imputing missing values

Calcualte the total number of missing values in the databaset:
```{r}
total_missing_values <- sum(is.na(data$steps))
```

The total number of missing values is **`r total_missing_values`**.

.....................................................................................................................................................

Missing values is occupied by using the average available steps for a given interval and call it `occupied_data`:

```{r}
occupied_data <- data
na_indices <- which(is.na(occupied_data$steps))
average_steps <- average_steps_per_interval_with_present_data
for(i in na_indices) {
  interval <- occupied_data$interval[i]
  occupied_data$steps[i] <- ave_steps[ave_steps$interval ==interval,]$steps
}
```

A histogram of the total steps per day with the occupied in data:
```{r echo=FALSE}
total_steps_per_day_with_occupied_data <- get_steps_per_day(occupied_data)
gg_plot(total_steps_per_day_with_occupied_data, axes(x = day, y = steps)) +
  geom_bar(stat = "identity") +
  ylab("total steps")
```

Calculate the mean and medial total number of steps taken per day with the filled in data:
```{r}
mean_occupied_steps <- mean(total_steps_per_day_with_occupied_data$steps)
median_occupied_steps <- median(total_steps_per_day_with_occupied_data$steps)
```

 **`r formatC(mean_filled_steps, small.mark=",")`** 
 **`r formatC(median_filled_steps, small.mark=",")`** 

  **`r formatC(mean_avaialble_steps,  small.mark=",")`** and **`r formatC(median_available_steps , small.mark=",")`** 


......................................................................................................................................................
 Are there differences in activity patterns between weekdays and weekends?


```{r}
weekdays <- c("Monday", "Tuesday", "Wednesday", "Thursday", "Friday")
occupied_data$day_of_week <- weekdays(occupied_data$date)
occupied_data$type_of_day <-
  factor(occupied_data$day_of_week %in% weekdays_list,
         levels = c(FALSE, TRUE),
         labels = c("weekend", "weekday"))
```
......................................................................................................................................................
A panel plot that compares steps taken during a weekend vs. a weekday:

```{r echo=FALSE}
weekday_data <- filled_data[occupied_data$type_of_day == "weekday",]
weekend_data <- filled_data[occupied_data$type_of_day == "weekend",]
weekday_steps <- get_steps_per_interval(weekday_data)
weekend_steps <- get_steps_per_interval(weekend_data)
weekday_steps$type_of_day <- factor(TRUE, levels = c(FALSE, TRUE), labels = c("weekend", "weekday"))
weekend_steps$type_of_day <- factor(FALSE, levels = c(FALSE, TRUE), labels = c("weekend", "weekday"))
weekday_weekend_steps <- rbind(weekday_steps, weekend_steps)
xyplot(steps ~ interval | type_of_day, data = weekday_weekend_steps, layout = c(1,2), type = "l", xlab = "Interval", ylab = "Number of steps")




