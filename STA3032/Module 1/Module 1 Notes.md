
Population
	collection of individual(s) in which we are interested.

Sample
	Subset of the population from which data is collected.

Parameter
	Numerical summary of the population of interest.

Statistic
	Numerical summary of a sample taken from the population.

![[Pasted image 20240813211435.png]]


Branches of Statistics

Descriptive Statistics
	Involves the organization, summarization, and display of data.

Inferential Statistics
	involves the use of a sample to draw conclusions of entire population leveraging probability.


Types of Data

Qualitative Data
	consists of attributes, labels, or nonnumeric entries.

Nominal Data
	Categories with no natural ordering. Eg color of hair, or nationality.

Ordinal Data
	Categories with a natural ordering. Eg. When companies ask for rating 1-10 on service.

Quantitative Data
	consists of numerical counts or measurements.

Discrete Data
	Consists of quantities that can be counted.

Continuous Data
	Consists of quantities that can be measured.

Types of Sampling


Simple Random Sampling
	All samples have equal chance of selection.

Stratified Sampling
	A set number of items is selected from each subgroup.

Cluster Sampling
	All items are selected from a set number of subgroups.

Systematic Sampling
	every $k^th$ item in the population is selected.

Variables


Variable
	any characteristic observed in a study. Eg. Age

Distribution
	describes how the result falls across the range of possible results. Eg. Age of individual over plot of possible ages.

Categorical Variable
	A categorical (or qualitative) variable is so if observation belongs to one of a set of distinct categories.

Quantitative Variable
	A variable is quantitative if observations are numerical values that represent different magnitudes of the variable.

![[Pasted image 20240813224549.png]]

Sample Mean
	Suppose that the observations in a sample are $x_1, x_2, ..., x_n$ The Sample Mean is denoted by $\overline x$, and the equation is:
$$
		\overline x$ = $\sum_{i = 1}^{n} \frac{x_i}{n} = \frac{x_1 + x_2 + ... + x_n}{n}
$$

![[Pasted image 20240813231425.png]]


Sample Mean
	Given the observations in a sample are $x_1 \underline < x_2 \underline < ... \underline < x_n$ the sample median is denoted by x~ 
![[Pasted image 20240814125412.png]]

![[Pasted image 20240814125439.png]]

Trimmed Mean
	p% trimmed mean is denoted by $\overline X_{tr(p)}$ and is found by eliminating the largest p% and smallest p% of the data, and computing the average of the remaining values

![[Pasted image 20240814125733.png]]


<font size = 6>Other Measures of Location</font>

Mode
	Value that occurs the most frequently in the sample
	Does not need to be near center

![[Pasted image 20240814130646.png]]
![[Pasted image 20240814130700.png]]


Percentile
	the $p_{th}$ percentile is a value that p% of observations fall at or below that value

Quartile
	First Quartile
		$25_{th}$ percentile, denoted as $Q_1$
	Second Quartile
		$50_{th}$ percentile, denoted as $Q_2$
	Third Quartile
		$75_{th}$ percentile, denoted as $Q_3$

Calculating Percentile
	![[Pasted image 20240817190830.png]]
	![[Pasted image 20240817190855.png]]


<font size = 6> Measures of Variability </font>

Range
	![[Pasted image 20240823102146.png]]

Sample Variance
	![[Pasted image 20240823102413.png]]

Sample Standard Deviation
	![[Pasted image 20240823102434.png]]

EX
	![[Pasted image 20240823102522.png]]
	

Interquartile Range
	Distance between the third and first quartile
	IQR = $Q_3 - Q_1$ 

Determining Outliers
	An observation is an outlier if it is more than $(1.5 * IQR)$
	$Q_1 - (1.5 * IQR), Q_3 + (1.5 * IQR)$ 



<font size = 6>Graphical Summaries</font>

Dot Plot
	Represents observations as individual dots on a number line
	EX
		![[Pasted image 20240824192527.png]]

Histogram
	Dot plots are unwieldy for large datasets
	Instead a Histogram can be used, which uses bars to portray frequencies or relative frequencies of possible outcomes for a quantitative variable
		Steps to a histogram
			(i) Divide the range of the data into intervals of equal width.
			(ii) Count the number of observations in each interval, forming a frequency table.
			(iii) Draw a bar over each value or interval with height equal to its frequency.
	EX
		![[Pasted image 20240824222656.png]]
		![[Pasted image 20240824222725.png]]
		![[Pasted image 20240824222748.png]]

Unimodal
	Distribution that has a single mound or peak

Bimodal
	Distribution with two distinct mounds

Multimodal
	Distribution with more than one distinct mound
![[Pasted image 20240824223111.png]]


Symmetric
	Unimodal distribution is symmetric if the side of the distribution below a central value is a mirror image of the side above that central value.

Skewed
	Unimodal distribution is skewed if one side of the distribution stretches out longer than the other side
	A distribution is left-skewed if the left tail is longer than right tail. Vice versa for right-skewed
	![[Pasted image 20240824224010.png]]
	• symmetric, the sample mean is close to the sample median.
	• left-skewed, the sample mean is smaller than the sample median.
	• right-skewed, the sample mean is greater than the sample median.

Five-Number Summary
	Consists of the minimum value, first quartile, median, third quartile, and the maximum value.

Box Plot
	aka box-and-whisker plot
	Graphical display of the five-number summary of a data set
	Box Plot construction
		(i) Draw a box from the first quartile to the third quartile.
		(ii) Draw a line inside the box at the median.
		(iii) Draw a line from the lower end of the box to the smallest observation that is not a potential outlier and a line from the upper end of the box to the largest observation that is not a potential outlier. These lines are called whiskers.
		(iv) The potential outliers (lying outside the interval $Q_1− 1.5· IQR, Q_3 + 1.5· IQR$) are denoted separately with special symbols such as a dot or a star.
	![[Pasted image 20240824224753.png]]
	![[Pasted image 20240824224806.png]]
	