# A Beginner's Guide to Build a Tableau Bar Chart Race
TowardsDataScience: 

https://towardsdatascience.com/a-beginners-guide-to-build-a-tableau-bar-chart-race-in-6-minutes-998b0087d30e

YouTube: 

https://www.youtube.com/watch?v=4svhLm9gjzk&feature=youtu.be

A bar chart race has become very popular recently. Since the beginning of 2020, Tableau released 2020.x version with the new Animations feature for dynamic parameters. This means that the bar chart race below can now be built easily in 6 minutes.

This tutorial is a step-by-step guide to build a bar chart race based on historical Gross Domestic Product (GDP) data. To build a bar chart race is to create many discrete pages of bar charts and then string them together, just like how a traditional cartoon animation is built.

## Step 1: Get ready the software and data
Download and install Tableau Public (latest version 2020.1.2 onwards). It is free of charge with full functionality. The only snag is that any work done can only be published on the Tableau Public server, and not saved locally to your Desktop. This is alright if the data is not sensitive or private.
https://public.tableau.com/en-us/s/

Next, download the latest GDP data (in *.xls format) from The World Bank.
https://data.worldbank.org/indicator/NY.GDP.MKTP.CD
However, the data format is not desired. Go to my GitHub and run the Python file GDP_data_cleanup.ipynb. This will output a new data file historical_gdp.xls.

Open the Tableau Public app and connect to the newly created data file, by clicking on "Microsoft Excel" and then selecting the data file: historical_gdp.xls.
Click on the "Sheet 1" tab at the bottom left to start the worksheet. 

## Step 2: Select the Measures to race
To choose GDP as the Measures to race: Drag "Gdp" to Columns.

To label the bars with country names, and with various colours:
First, drag "Country" to Label, then drag "Country" again to Colour.

## Step 3: Create Rank for countries
This section requires a simple programming line of code.
Click on Dimensions → drop-down menu → Create Calculated Field.

Create a new field "Rank", and key in the code below.

RANK_UNIQUE(Sum([Gdp]))

Click on "Apply" to ensure that calculation is valid, then click "OK".

"Rank" is newly created under Measures. Drag "Rank" to Rows.
Click on (Rows) Rank → drop down menu → Discrete.
Click on (Rows) Rank → drop down menu → Compute Using → "Country".

## Step 4: Configure Animations 
To create a snapshot of animations frames, each year is one page:
Drag "Year" to Pages.

Turn on animations: Format → Animations → On.
To set the transition duration: Duration → "1.00 seconds (Slow)".
Close Animations window by clicking "X".

Look for a little Animations control which appeared when the animations feature is turned on, and click the "forward play" icon. Drag the slider bar to another year or use the left/right button to choose a year.

## Step 5: Add some simple customisation
1. To change chart title:
Double-click on "Sheet 1" tab (at the bottom left), and change it to "Top 10 Countries Historical GDP By Year".
Double-click on the chart title, this brings up the title editor.
Select all and configure the following:
Font size 26, Bold type, Centre alignment.

2. To change X-axis limits:
Double-click on the X-axis, this brings up the Axis menu.
Choose Range to be "Fixed", Fixed start=0, Fixed end=2.1e+13
Click on "X" to close the window.

3. To display only the top 15 countries:
Drag "Rank" to Filters → click on "OK".
Click on (Filters) Rank → drop down menu → Compute Using → "Country" .
Replace "206" with "15", and click on "OK".
Change the Standard view to "Entire View".

4. To increase label font size and bar size:
Click on Label → ensure "Show mark labels" is checked.
Click on Label → ensure "Allow labels to overlap other marks" is checked.
Click on Label → Font → drop down menu → change to font size "20".
To increase label font sizeClick on Size → drag the slider towards the right.

5. To add the year label on chart:
Right-click on any empty chart area → Annotate → Area.
This brings up the annotation editor.
Increase font size to "48", and key in <Page Name>.
Click on "OK".
The year label is created. Resize and locate it in the middle of the chart.

6. To grey off the bottom 5 countries:
Right-click on any empty chart area → Annotate → Area.
This brings up the annotation editor. This time do nothing and click "OK".
A grey box is formed. Right-click inside the grey box → Format.
Format Annotation → Shading → drop down menu → drag slider to 75%.
Resize the grey box and locate it to hover over the bottom 5 countries.

## Publish Visualisation
When you are satisfied with the customisation, the visualisation is then ready to be published.
Click on File → Save to Tableau Public.
The work is now published on the Tableau Public server. You can then share it using the web link.

Here's a video tutorial with step-by-step guide for the entire process:
https://youtu.be/4svhLm9gjzk

## Congratulations!
You have now created your very first bar chart race!
You can now try it on other country level data with date/time series: 
COVID19 Cases (https://towardsdatascience.com/how-to-build-a-bar-chart-race-on-covid-19-cases-in-tableau-4c45b08cdafe), Population, Life Expectancy, etc.

Have fun, and let your creativity flow!
