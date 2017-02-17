# Are more selective or expensive colleges worth it?

As costs to attend college increase, an increasing number of high school seniors are left wondering if they should or must select a more affordable college. First of all, are more selective colleges more expensive? Second of all, do more selective or more expensive colleges help you make more money in the future relative to less selective or less expensive institutions?

To begin to answer these questions, I use data from the US Department of Education's College Scorecard to see if admissions rate, average cost of attendance, and graduates' mean earnings 10 years after graduation are correlated for colleges that predominantly award bachelor's degrees. The data are not well correlated, as seen below.

## Admission Rates vs. Average Cost of Attendance
Using a list of 623 institutions with both valid average cost of attendance data and reported admission rates, I plot an institution's admission rate vs. its average cost of attendance.

![admVsCost](https://github.com/williamalu/data_science_college_scorecard/blob/master/images/admVsCost.png "admVsCost")

As you can see from the widely spread data, there is no correlation between admission rate and average cost of attendance. More selective colleges do not necessarily cost more than less selective colleges. On the flip side, less selective colleges are not necessarily cheaper than more selective colleges.

## Mean Earnings vs. Average Cost of Attendance
Using a list of 678 colleges with both valid cost of attendance data and reported mean earnings data that meet National Student Loan Data System (NSLDS) and Treasury Department privacy standards, I plot an institution's graduates' mean earnings 10 years after graduation vs. its average cost of attendance.

![earningsVsCost](https://github.com/williamalu/data_science_college_scorecard/blob/master/images/earningsVsCost.png "earningsVsCost")

Here, the data is clustered around graduates making around an average of $50,000 per year 10 years after graduation, regardless of their institution's average cost of attendance. There is no correlation between mean earnings and an institution's average cost of attendance.

## Mean Earnings vs. Admission Rates
Using a list of 1526 colleges with both valid cost of attendance data and reported admission rates, I plot an institution's mean earnings 10 years after graduation vs. its admission rate.

![earningsVsAdm](https://github.com/williamalu/data_science_college_scorecard/blob/master/images/earningsVsAdm.png "earningsVsAdm")

As the spread out data show, there is no correlation between more selective colleges and their graduates' future earnings. However, a pattern exists in the scatterplot that merits further investigation. There are a small number of colleges with very low admission rates that have graduates that earn substantially more than other colleges. For future investigation, I would group colleges into percentiles by their admission rates and then take the mean of each percentile's mean earnings to see if there is a broad pattern between selectivity and future earnings.

# Methodology

This analysis is based on data from the US Department of Education's College Scorecard. I combine data from 2 years: 2012-2013 and 2014-2015. The 2012-2013 dataset contains the latest mean earnings after graduation that I could find and 2014-2015 dataset contains information on whether or not institutions are still operating.

Whether or not an institution is still operating is important because the data are only meaningful if students can act using information the data give. This means that an institution that is no longer operating should be filtered from our dataset. After matching colleges from the 2014-2015 dataset with colleges in the 2012-2013 dataset, I filter out institutions that are no longer operating. Unfortunately, this also filters out institutions that exist in the 2012-2013 dataset but not the 2014-2015 dataset and therefore do not have this data. I use an institution's Office of Postsecondary Education ID (OPEID), an institution's 6 digit OPEID (OPEID6), and an institution's Integrated Postsecondary Education Data System unit ID (UNITID) to match institutions between the 2014-2015 and 2012-2013 datasets, and from year to year, some institutions' IDs change. For institutions that have all three ID numbers changed, I am unable to match their data between the 2012-2013 and 2014-2015 datasets. These schools are also dropped. Due to this filtering for operational institutions, I go from a list of 7794 institutions to a list of 6438.

Because a person's degree of education significantly impacts their earning potential (e.g. a person with a PhD is likely to be paid more than someone with only a bachelor's degree), I decided to focus on institutions that predominantly award bachelor's degrees. Selecting for those institutions brings our total list of institutions to 1991.

After filtering for the institutions' average cost of attendance data, admission rate data, and mean earnings data, I plotted their data in scatterplots and found their Pearson's correlations using a function from the ThinkStats2 library.

The details of this analysis are in this Jupyter notebook.
