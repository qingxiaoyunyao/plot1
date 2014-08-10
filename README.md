plot1
=====

## read data into R
data <- read.csv2("household_power_consumption.txt", header = TRUE, as.is = TRUE) 

## add a new variable "time" which denotes the time and date
time <- strptime(paste(data$Date, data$Time), "%d/%m/%Y %H:%M:%S")
data$time <- time

## transform "Date" variable to Date type
data$Date <- as.Date(data$Date, "%d/%m/%Y")

## get the data from 01/02/2007 to 02/02/2007
a <- data[data$Date >= as.Date("01/02/2007", "%d/%m/%Y") & data$Date <= as.Date("02/02/2007","%d/%m/%Y"),]

## transform the "Global_active_power" to numeric variable 
a$Global_active_power <- as.numeric(a$Global_active_power)

## draw the histogram
hist(a$Global_active_power, col = "red", ylab = "Frequency", xlab = "Global Active Power (kilowatts)", main = "Global Active Power")


## save the picture in plot1.png
dev.copy(png, width = 480, height = 480, file = "plot1.png")
dev.off()

Exploratory Data Analysis/ assignment 1/ plot1
