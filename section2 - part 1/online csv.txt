#Using RCurl to read in csv data hosted online on github and other #sites
library(RCurl)
data1= read.csv(text=getURL("https://raw.githubusercontent.com/sciruela/Happiness-Salaries/master/data.csv"))
head(data1)
summary(data1)

data2=read.csv(text=getURL("https://raw.githubusercontent.com/opetchey/RREEBES/master/Beninca_etal_2008_Nature/data/nutrients_original.csv"), skip=7, header=T)
head(data2)
summary(data2)

data3=read.csv(text=getURL("https://www.gov.uk/government/uploads/system/uploads/attachment_data/file/246663/pmgiftsreceivedaprjun13.csv"))
head(data3)