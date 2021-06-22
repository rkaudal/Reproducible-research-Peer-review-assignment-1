# Kaudal_Reproducible-research-Peer-review-assignment-1

# Introduction
We can collect a large amount of data about personal movement using activity monitoring devices such as a Fitbit, Nike Fuelband, or Jawbone Up. Such devices are part of the “quantified self” movement – a group of enthusiasts who take measurements about themselves regularly to improve their health, to find patterns in their behavior, or equally they are tech geeks. However these data remain under-utilized 1. because the raw data are hard to obtain 2. there is a lack of statistical methods and software for processing and interpreting the data.
In this assignment we make use of data from a personal activity monitoring device. Such device collects data at 5 minute intervals through out the day. The data comprises of two months of data from an anonymous individual collected during the months of October and November, 2012 and include the number of steps taken in 5 minute intervals each day.
You can download the data for this assignment from the course web site:
Dataset: Activity monitoring data [52K]
Variable definition
     steps: Number of steps taking in a 5-minute interval (missing values are coded as NA
     date: The date on which the measurement was taken in YYYY-MM-DD format
     interval: Identifier for the 5-minute interval in which measurement was taken
The dataset is in a comma-separated-value (CSV) file and there are a total of 17,568 observations in this dataset.
# Review criteria 
Here is how the review will be performed
# Repo
Provide Valid GitHub URL 
There should at least be one commit beyond the original fork
Also provide Valid SHA-1
This SHA-1 should corresponds to a specific commit
# Commit containing full submission
Here are the commit that should accompany with full submission
1. Code for reading in the dataset and/or processing the data
2. Histogram of the total number of steps taken each day
3. Mean and median number of steps taken each day
4. Time series plot of the average number of steps taken
5. The 5-minute interval that, on average, contains the maximum number of steps
6. Code to describe and show a strategy for imputing missing data
7. Histogram of the total number of steps taken each day after missing values are imputed
8. Panel plot comparing the average number of steps taken per 5-minute interval across weekdays and weekends
9. All of the R code needed to reproduce the results (numbers, plots, etc.) in the report
# Assignment
We will take multiple steps to complete this assignment. We will write a report that answers the questions which are posed below. The final assignment will be submitted as a single R markdown document that can be processed by knitr and be transformed into an HTML file.Following are the advices while you write down the code for the report 1. Making sure that full code is written that could generate the output presented. 2. Always use echo = TRUE so that other will be able to read the code. As this assignment will be evaluated via peer assessment it is imperative that peer evaluators are able to review the code for your analysis.
We can choose any plotting system in R (i.e., base, lattice, ggplot2) in order to make a plot.
We need to Fork/clone the GitHub repository created for this assignment. We will submit this assignment by pushing completed files into our forked repository on GitHub. This assignment submission should link to the URL to our GitHub repository and the SHA-1 commit ID to our repository state.
NOTE: The GitHub repository also contains the dataset for the assignment so we do not have to download the data separately.

Here are the directions that could guide to complete this assignment
 Loading and preprocessing the data
 Show any code that is needed to
                                 Load the data (i.e. read.csv())
                                 Process/transform the data (if necessary) into a format suitable for your analysis

1. What is mean total number of steps taken per day?

For this part of the assignment, you can ignore the missing values in the dataset.
a. Calculate the total number of steps taken per day
b. Make a histogram of the total number of steps taken each day
c. Calculate and report the mean and median of the total number of steps taken per day

2. What is the average daily activity pattern?
a. Make a time series plot (i.e.type = "l") of the 5-minute interval (x-axis) and the average number of steps taken, averaged across all days (y-axis)
b. Which 5-minute interval, on average across all the days in the dataset, contains the maximum number of steps?

3. Imputing missing values: Note that there are a number of days/intervals where there are missing values NA). The presence of missing days may introduce bias into somecalculations or summaries of the data.
a. Calculate and report the total number of missing values in the dataset (i.e. the total number of rows with NA\color{red}{\verb|NA|}NAs)
b. Devise a strategy for filling in all of the missing values in the dataset. The strategy does not need to be sophisticated. For example, you could use the mean/median for that day, or the mean for that 5-minute interval, etc.
c. Create a new dataset that is equal to the original dataset but with the missing data filled in.
d. Make a histogram of the total number of steps taken each day and Calculate and report the mean and median total number of steps taken per day. Do these values differ from the estimates from the first part of the assignment? What is the impact of imputing missing data on the estimates of the total daily number of steps?

4. Are there differences in activity patterns between weekdays and weekends?
 For this part the weekdays() function may be of some help here. Use the dataset with the filled-in missing values for this part.
 a. Create a new factor variable in the dataset with two levels – “weekday” and “weekend” indicating whether a given date is a weekday or weekend day.
 b. Make a panel plot containing a time series plot (i.e. type = "l") of the 5-minute interval (x-axis) and the average number of steps taken, averaged across all weekday days or weekend days (y-axis). See the README file in the GitHub repository to see an example of what this plot should look like using simulated data.

# Submitting the Assignment
In order to submit the assignment:
1. Commit completed PA1_template.Rmd file to the master branch of our git repository (we should already be on the master branch unless we created new ones). Commit our PA1_template.md and PA1_template.html files produced by processing our R markdown file with knit2html() function in R (from the knitr package) by running the function from the console. If our document has figures included (it should) then they should have been placed in the figure/ directory by default (unless we overrided the default). Add and commit the figure/ directory to your git repository so that the figures appear in the markdown file when it displays on github.Push master branch to GitHub.
    
2. Submit the URL to your GitHub repository for this assignment on the course web site.

3. In addition to submitting the URL for your GitHub repository, we will need to submit the 40 character SHA-1 hash (as string of numbers from 0-9 and letters from a-f) that identifies the repository commit that contains the version of the files we want to submit. We can do this in GitHub by doing the following
a. Going to your GitHub repository web page for this assignment
b. Click on the “?? commits” link where ?? is the number of commits we have in the repository. For example, if we made a total of 10 commits to this repository, the link should say “10 commits”.
c. We will see a list of commits that you have made to this repository. The most recent commit is at the very top. If this represents the version of the files we want to submit, then just click the “copy to clipboard” button on the right hand side that should appear when we hover over the SHA-1 hash. Paste this SHA-1 hash into the course web site when we submit our assignment. If we don't want to use the most recent commit, then go down and find the commit we want and copy the SHA-1 hash.
