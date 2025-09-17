# Understanding Pollution in Major US Cities

- **Name**: Lily Soetebier
- **Dataset**: pollution_data.csv

## Overview

*Paragraph 1: Briefly explain your reasons for choosing the specific dataset,
which can include any discussion about the topic and particular variables.*

I chose the pollution data set as I felt it best aligned with my interests in science communication. While I don't always work with data on this large of a scale, nor do I often work with data that has not been processed, I do work with environmental data on a daily basis as a science communication intern at North Carolina Sea Grant. As such, I feel that being able to work with environmental data, and have the familiarity with the kinds of measurements that I could be looking for is something that will strengthen my skills as an intern. 

<!--importing time from d3 -->
```js
import {utcParse, utcFormat} from "d3-time-format";
```

Then, divide the notebook into meaningfully sections and subsections.
Use the following general scheme to revise as needed.

## Attach the data

*In this section, be sure to make some small notes about the*data and output it
in an executable js codeblock, so you can review it on the page interactively.
You can note its size, for instance, as well as any other notable insights
gleaned during your first glance.*

*Remember that this is a notebook, so you can treat it like one. `:-)`*

```js
const pollutionData = FileAttachment("./../data/midterm-options/pollution/pollution_data.csv").csv({typed: true})
```
### Dataset Printout
```js
// printing the data so that I can see it and reference backl
pollutionData
```
## Convert Dates

*Convert the dates, which are strings, into Date() objects with your own custom
D3.js parser and any formatters. Discuss any particular choices to format the
date data in any new ways.*

*Again, be sure to output your newly transformed data in executable codeblocks
for easier verification and reviewing.*
### Creating and Testing Date Formatter
```js
const dateFormatter = utcFormat("%A, %B %d, %Y")
```
```js
let testObject = pollutionData[0]
```
```js
testObject
```

```js
dateFormatter(testObject.Date)
```

### Converting Dates
```js
let dataWithDates = pollutionData.map(
  (city) => {
    city.prettyDate = dateFormatter(city.Date)
    return city
  }
)
```
```js
dataWithDates
```

### Reasoning
Since the data present in the set was already set as date objects, I chose to reformat into a string with the full weekday and month name written out. My purpose for this is that the day of the week that pollution data may have been collected could impact the results. For example, it is possible that pollutants caused by exhaust will be higher on workdays when there are more commuters present. 


## Looking Through the Data
To familiarize myself with the data, I am performing a few actions here to make decision making about the next parts a bit easier.

```js
let no2Medians =[]
for (let city of pollutionData) {
  no2Medians.push(city.no2_median)
}

```

```js
no2Medians
```


## Grouping #1 - Median Measurement of NO2

*Explain your plan to group the data in a particular way here, before you do so.
At least one of the groupings should use some variation of D3's `.rollup()`, so
you can count particular grouped properties.
*

### Explanation and Procedure
This grouping categorizes cities by their median amount of NO2 that was present in the atmosphere. The groupings are done in ranges of 10.


1. Create a for of loop to loop through the data
2. Create a set of conditionals that evaluates the no3_median property of each city object and assigns a new property called date range to the city
3. 

Again, be sure to output your newly transformed data in executable codeblocks
for easier verification and reviewing.

## Grouping #2 - Rollup of Cities and States

Explain your plan to group the data in a particular way here, before you do so.
At least one of the groupings should use some variation of D3's `.rollup()`, so
you can count particular grouped properties.

Provide a procedure of your grouping plan in an ordered list before the codeblock:

### Explanation and Procedure
This rollup tallies the number of entries from each city, and groups these cities by their state.

1. Initialize a constant to hold the new D3 map.
2. Set the const equal to d3.rollup()
3. add a line naming the data set separated by a comma
4. add in the .length method to ensure that we are getting counts of each instance
5. create the outer most grouping of state by using an arrow function and dot notation
6. create the inner grouping of city by using an arrow function and dot notation
7. in a separate JS block, print the new map to verify

### Completing the RollUp
```js
const stateRollup = d3.rollup(
  pollutionData,
  (D) => D.length,
  (d) => d.State,
    (d) => d.City,
)
```

```js
stateRollup
```
### 

Again, be sure to output your newly transformed data in executable codeblocks
for easier verification and reviewing.

## Reflection

Use the following prompt to guide your reflection about your data work:
"What 2-3 insights and 2-3 questions did you glean from your initial work
with the dataset?"

Use the PR-TEMPLATE prompts to reflect on the midterm experience.