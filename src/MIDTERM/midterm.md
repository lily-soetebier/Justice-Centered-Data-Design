# Understanding Pollution in Major US Cities

- **Name**: Lily Soetebier
- **Dataset**: pollution_data.csv

## Overview

*Paragraph 1: Briefly explain your reasons for choosing the specific dataset,
which can include any discussion about the topic and particular variables.*

I chose the pollution data set as I felt it best aligned with my interests in science communication. While I don't always work with data on this large of a scale, nor do I often work with data that has not been processed, I do work with environmental data on a daily basis as a science communication intern at North Carolina Sea Grant. As such, I feel that being able to work with environmental data, and have the familiarity with the kinds of measurements that I could be looking for is something that will strengthen my skills as an intern. 

<!--importing time from d3 -->
```js
import {utcParse,utcFormat} from "d3-time-format";
```

Then, divide the notebook into meaningfully sections and subsections.
Use the following general scheme to revise as needed.

## Attach the data

*In this section, be sure to make some small notes about the data and output it
in an executable js codeblock, so you can review it on the page interactively.
You can note its size, for instance, as well as any other notable insights
gleaned during your first glance.*

*Remember that this is a notebook, so you can treat it like one. `:-)`*

```js
let pollutionData = FileAttachment("./../data/midterm-options/pollution/pollution_data.csv").csv({typed: true})
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
### Creating and Testing Date Parser
```js
let dateParser = utcParse("%Y-%m-%d")
let testDate = dateParser("2019-01-01")
```
```js
testDate
```
### Converting Dates
```js
for (let city of pollutionData) {
  console.log(city.Date)
}
```


## Grouping #1 - Name of grouping here

Explain your plan to group the data in a particular way here, before you do so.
At least one of the groupings should use some variation of D3's `.rollup()`, so
you can count particular grouped properties.

Provide a procedure of your grouping plan in an ordered list before the codeblock:

1. Coding_Action_1
2. Coding_Action_2
3. ...

Again, be sure to output your newly transformed data in executable codeblocks
for easier verification and reviewing.

## Grouping #2 - Name of grouping here

Explain your plan to group the data in a particular way here, before you do so.
At least one of the groupings should use some variation of D3's `.rollup()`, so
you can count particular grouped properties.

Provide a procedure of your grouping plan in an ordered list before the codeblock:

1. Coding_Action_1
2. Coding_Action_2
3. ...

Again, be sure to output your newly transformed data in executable codeblocks
for easier verification and reviewing.

## Reflection

Use the following prompt to guide your reflection about your data work:
"What 2-3 insights and 2-3 questions did you glean from your initial work
with the dataset?"

Use the PR-TEMPLATE prompts to reflect on the midterm experience.