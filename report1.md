# Are more selective or expensive colleges worth it?

As costs to attend college increase, an increasing number of high school seniors are left wondering if they should or must select a more affordable college. First of all, are more selective colleges more expensive? Second of all, do more selective or more expensive colleges help you make more money in the future relative to less selective or less expensive institutions?

To begin to answer these questions, I use data from the US Department of Education's College Scorecard to see if admissions rate, average cost of attendance, and graduates' mean earnings 10 years after graduation are correlated for colleges that predominantly award bachelor's degrees.

## Admission Rates vs. Average Cost of Attendance
Using a list of 1601 institutions with both valid average cost of attendance data and reported admission rates, I plot an institution's admission rate vs. its average cost of attendance.

![admVsCost](https://github.com/williamalu/data_science_college_scorecard/blob/master/images/admVsCost.png "admVsCost")

In the scatterplot, we see 4 main clusters of data. There are a lot of colleges that have a 100% admissions rate who have an average cost of attendance just under $20,000 a year. Right underneath that cluster is a cluster of colleges that cost about $20,000 a year with admissions rates ranging from 60% to 90%. There is another cluster of schools that range from $30,000 to $48,000 a year with admission rates from 50% to 80%. The last cluster is an interesting tail or panhandle on the bottom right of the scatterplot: schools that charge an average of just under $60,000 a year but have admission rates 40% and below.

The data have a Spearman's rank correlation of -0.211, which suggests a slight downward correlation. However, visually examining the scatterplot tells us that this does not mean very much. The cluster of expensive colleges with low admission rates in the bottom right of the scatterplot is worth exploring, because further analysis could potentially tell us whether or not those institutions are outliers. We do not have enough analysis to show that a low admimssion rate increases cost of attendance or vice versa, but a pattern exists that merits more analysis.

## Mean Earnings vs. Average Cost of Attendance
Using a list of 1712 colleges with both valid cost of attendance data and reported mean earnings data that meet National Student Loan Data System (NSLDS) and Treasury Department privacy standards, I plot an institution's graduates' mean earnings 10 years after graduation vs. its average cost of attendance.

![earningsVsCost](https://github.com/williamalu/data_science_college_scorecard/blob/master/images/earningsVsCost.png "earningsVsCost")

The scatterplot shows three main features in the data. There is a cluster of institutions that charge about $20,000 per year with graduates that make an average of around $40,000 a year 10 years after graduation. Another cluster of institutions charge $30,000 to $40,000 a year with graduates that also make about $40,000 a year 10 years after graduation. The last major feature is the group of institutions on the far right of the scatterplot -- schools that charge just under $60,000 per year but have graduates that make anywhere from $40,000 to almost $140,000 per year after graduation.

We can see here that there is a slight positive correlation between the mean earnings of an institution's graduates 10 years after graduation and an institution's average cost of attendance, which is consistent with a Spearman rank correlation of 0.355. There are definitely some institutions that charge their students more, but provide a commensurate return on investment. However, our data and analysis is still not sufficient to establish a general pattern of making more after graduation if you pay more for school and further analysis is required.

## Mean Earnings vs. Admission Rates
Using a list of 1510 institutions with both valid mean earnings data and reported admission rates, I plot an institution's graduates' mean earnings 10 years after graduation vs. its admission rate.

![earningsVsAdm](https://github.com/williamalu/data_science_college_scorecard/blob/master/images/earningsVsAdm.png "earningsVsAdm")

As the spread out data show, there is no correlation between more selective colleges and their graduates' future earnings. There is a cluster of institutions that have admission rates of 60% and 80% whose graduates earn between $40,000 and $60,000 a year 10 years after graduation, and the Spearman's rank correlation for the data is a weak -0.101.

There is, however, a pattern in the scattterplot that merits further investigation. There are a small number of colleges with very low admission rates that have graduates that earn substantially more than other colleges. For future investigation, I would group colleges into percentiles by their admission rates and then take the mean of each percentile's mean earnings to see if there is a broad pattern between selectivity and future earnings.

# Methodology

This analysis is based on data from the US Department of Education's College Scorecard. I combine data from 2 years: 2012-2013 and 2014-2015. The 2012-2013 dataset contains the latest mean earnings after graduation that I could find and 2014-2015 dataset contains information on whether or not institutions are still operating.

Whether or not an institution is still operating is important because the data are only meaningful if students can act using information the data give. This means that an institution that is no longer operating should be filtered from our dataset. Unfortunately, due to the way schools are identified in the College Scorecard data, some institutions that are still operating are dropped in the process of matching institutions between the 2012-2013 and 2014-2015 dataset. More details can be found in this [Jupyter notebook](https://github.com/williamalu/ThinkStats2/blob/master/code/report1.ipynb).

Because a person's degree of education significantly impacts their earning potential (e.g. a person with a PhD is likely to be paid more than someone with only a bachelor's degree), I decided to focus on institutions that predominantly award bachelor's degrees. This means that, if an institution offers bachelor's degrees, that the institution awards students bachelor's degrees more than other degrees. Selecting for those institutions brings our total list of institutions to 1976.

After filtering for the institutions' average cost of attendance data, admission rate data, and mean earnings data, I plotted their data in scatterplots and found their Pearson's correlations using a function from the ThinkStats2 library.

Further details of this analysis are in this [Jupyter notebook](https://github.com/williamalu/ThinkStats2/blob/master/code/report1.ipynb).