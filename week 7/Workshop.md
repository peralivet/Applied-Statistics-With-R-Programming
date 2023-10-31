## Introduction
In this workshop I will learn how to fit, evaluate and report some of the main time series models.

## Packages
I will be using three packages
-  stats
- TTR
- forecast

- 
```
#the following code will install the packages
install.packages("TTR")
install.packages("forecast")
library(TTR)
library(forecast)
```

# Reading data in R

the file [http://robjhyndman.com/tsdldata/misc/kings.dat] contains data on the age of death of successive kings of England, starting with William the Conqueror (original source: Hipel and Mcleod, 1994).

```
#skip = 3 is skipping the first 3 lines cos they are comments
kings <- scan("http://robjhyndman.com/tsdldata/misc/kings.dat",skip=3)

#display the dataframe
kings
```

```
#Reading birth data
births <- scan("http://robjhyndman.com/tsdldata/data/nybirths.dat")
birthstimeseries <- ts(births, frequency=12, start=c(1946,1))
birthstimeseries
```

```
# Souvenir data
#the file http://robjhyndman.com/tsdldata/data/fancy.dat contains monthly sales for a souvenir shop at a beach resort town in Queensland, Australia, for January 1987-December 1993 #(original data from Wheelwright and Hynd- man, 1998).

#Reading the data
souvenir <- scan("http://robjhyndman.com/tsdldata/data/fancy.dat")
#start variable limits the year the data should start
souvenirtimeseries <- ts(souvenir, frequency=12, start=c(1987,1))
souvenirtimeseries
```

# Plotting Time Series
```
#Plotting the king's time series 
plot.ts(kingstimeseries)
```
- result of the kingstimeseries ploting 
![kingstimeseries](https://github.com/peralivet/Applied-Statistics-With-R-Programming/blob/1cdcab076c8445e3ff68fef21207c520aa644d6b/week%207/Rplot.png)

From the time plot, this time series could probably be described using an additive model, since the random fluctuations in the data are roughly constant in size over time.

```
#Plotting the time series of the number of births per month in New York city
plot.ts(birthstimeseries)
```
- result of the birthstimeseries ploting 
![kingstimeseries](https://github.com/peralivet/Applied-Statistics-With-R-Programming/blob/b110742f8755e01fe5a43510566a1f9d8784925d/week%207/Rplot01.png) 
from this time series there seems to be seasonal variation in the number of births per month: there is a peak every summer, and a trough every winter. Again, it seems that this time series could probably be described using an additive model, as the seasonal fluctuations are roughly constant in size over time and do not seem to depend on the level of the time series, and the random fluctuations also seem to be roughly constant in size over time.


```
#Plotting the Souvenir Data 
plot.ts(souvenirtimeseries)
```


