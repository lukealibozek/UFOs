# UFOs

**Live Project Website**: [UFO Finder](https://lukealibozek.github.io/UFOs/index.html)

## Overview
---
The goal of this project was to create a dynamic website using JavaScript, allowing for live filtering of a dataset.

The coding languages/technologies used in this project:
- JavaScript
- D3
- Bootstrap
- HTML / CSS

### The dataset

The dataset contains UFO observational data structured as JSON objects. Below is a screenshot of a single object within the dataset, showcasing the keys and an example of possible values. 

![](resources/object.png)

### The layout

The front end of this project leverages the [bootstrap grid system](https://getbootstrap.com/docs/4.0/layout/grid/) to organize the content. 

![](resources/layout.png)

![](resources/fullPage.png)

The table is dynamically loaded via bootstrap. Furthermore, the D3 JavaScript library is used for its event listener features and dynamic data loading capabilities to handle user input and data visualization. 

## Results
---
The table can be manipulated by entering text into the following fields:

- Date (the date of the reported observation)
- City
- State
- Country
- Shape (shape of the object, as described by the witness report)

The D3 event listeners are coded to react upon detecting a "change" to the text fields - meaning that once a text field is typed in and escaped, the table will be filtered accordingly.

Additionally, multiple field entries can be combined, with the table updating live as filter the criteria is adjusted.

### Potential use case

This tool can be used to compare sightings at various locations and visualize trends. For example, the city "el cajon" returns five results - four of which occurring on the same evening. The fifth sighting, taking place three days later, mentions "fake stars" observed in the sky. Given that the description is less explicit than the others, and lacking corroboration by anyone else, this sighting reads as less credible.

## Summary
---
Despite the functionality, there are two main drawbacks:
1. The end user will have to know the EXACT cities/states/shapes within the dataset in order to use the filter capabilities. It might be possible to manually iterate through US states to explore the entries, but this is an impractical expectation. Additionally, dates also need to be exact, and cannot be selected by date ranges.
   1. One recommendation would be to include a drop down menu pre-populated with the available options (which has it's own limitations, but is an improvement upon the current design).
   2. Similarly, a date range selector would make it easier to explore the dataset.
2. By relying on text entry in the way it is implemented here, capitalization matters to an unfortunate degree. For example, all values are lowercase in the dataset, therefore the city value "Fresno" would return no results, while "fresno" would return one result. This can be improved via input handling, converting all text entry to lowercase before filtering. The following code is an example of how this can be implemented:
```javascript
let text = "Hello World!";
let result = text.toLowerCase();
```