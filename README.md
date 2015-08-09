# crime
Many municipalities provide open data on crime statistics.  
This project tries to leverage that data and show patterns. 


The direct source for this data is
[OpenDataPhilly](https://www.opendataphilly.org/dataset/philadelphia-police-part-one-crime-incidents)

![alt tag](https://github.com/mchirico/crime/blob/master/images/cheltenhamPhilly.gif)




Below shows Philadelphia Center City crime
![alt tag](https://github.com/mchirico/crime/blob/master/images/crimePhillyCC.gif)


```r

# Here's a quick way to get the data into R
library(RCurl)
File <- getURL("https://raw.githubusercontent.com/mchirico/crime/master/data/philly_crime.csv")
d <- read.csv(text = File,header=TRUE,stringsAsFactors=FALSE)
wd<-function(x) as.POSIXct(strptime(x, '%Y-%m-%d %H:%M:%S',tz='GMT'))
d$mdate = wd(d$DISPATCH_DATE_TIME)
# Remove na's
d=d[complete.cases(d[4:5]),]


```

For a more detail, see the following
![Analyzing Philadelphia Crime Data](https://github.com/mchirico/crime/wiki/Analyzing-Philadelphia-Crime-Data)

