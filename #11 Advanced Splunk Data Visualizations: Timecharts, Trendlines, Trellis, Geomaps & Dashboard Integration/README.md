In this lab, I demonstrate how to create visualizations using SPL commands, followed by configuring formatting options and selecting appropriate chart types in the visualization panel.
<br><br>
1. Using a **Timechart command** - which is an SPL visualization command that displays statistical trends over time. This search queries the **web** index and uses the** timechart command** to calculate the daily average of the **bytes** field, grouping the results by **host**, producing a time-series view that shows how the average amount of data transferred changes over time for each host.  

![111a](https://github.com/KO443/Splunk-power-user-lab-Projects/blob/main/Images/111a.png?raw=true)

2. In this part, the command was changed to chart, which produces a static aggregation without a time-based x-axis, unlike timechart, which generates a time-series visualization showing how the average amount of data transferred changes over time for each host.

![111b](https://github.com/KO443/Splunk-power-user-lab-Projects/blob/main/Images/111b.png?raw=true)
 
3. This Splunk search queries events from the **web** index, the **isnotnull** command filters out any records where the **action** field is missing to ensure only meaningful user **actions** are analyzed, and then uses the **timechart** command to count occurrences of each action over time, grouping the results by action to produce a time-series visualization that shows how different actions trend and change across the selected time range.
 
 ![111d](https://github.com/KO443/Splunk-power-user-lab-Projects/blob/main/Images/111d.png?raw=true)
 
 The chart above is currently displayed as a column chart with a **Chart Overlay** which is the green line that runs above my charts. <br><br>In my earlier visualization examples, I used a line chart instead. In the next section, I’ll walk through how I switch between chart types in Splunk and highlight some of the other visualization features available.

4. In the screenshot below, I’ve marked two key areas with a red arrow: the **Column Chart** selector and the **Format** menu. The button showing ‘Column Chart’ is the visualization selector, so this is where I switch between chart types or choose a completely different visualization. The **Format** panel (the page displaying screenshot) lets me adjust settings such as the X‑axis, Y‑axis, chart overlays, and legend options.<br><br>
Additionally, Splunk’s **Trellis** layout allows me to split search results into multiple small panels, each based on a specific field or aggregation, making it easier to compare patterns across different segments of the data.

![111c](https://github.com/KO443/Splunk-power-user-lab-Projects/blob/main/Images/111c.png?raw=true)

5. Using an overlay like i used in this part allows me to add other fields to display on the chart.

![111e](https://github.com/KO443/Splunk-power-user-lab-Projects/blob/main/Images/111e.png?raw=true)

6. Here is what it looks like to use Trellis for the same chart.

![111f](https://github.com/KO443/Splunk-power-user-lab-Projects/blob/main/Images/111f.png?raw=true)

7. I turned off the **Trellis layout**, returning the chart to its original view. After that, I saved it to a new dashboard titled **‘Weekly Info’** and named the panel **‘Action Taken by Shoppers’**. Finally, I selected Save to Dashboard to store the updated visualization as Dashboard.
![111g](https://github.com/KO443/Splunk-power-user-lab-Projects/blob/main/Images/111g.png?raw=true)

8. I created a pie chart visualization to display all user actions, including purchase, view, remove, add to cart, and change quantity. To generate the data, I ran a simple SPL query against the **web** index using the stats command with the count function to aggregate action totals. I then added this pie chart to my existing dashboard, **‘Weekly Info'**.

![111h](https://github.com/KO443/Splunk-power-user-lab-Projects/blob/main/Images/111h.png?raw=true)

***********

In this section of the Lab i will be Making a visualization for number of **purchases** which is one of the field Values of **action field**.

1. I started by running a search query that returned the total number of **purchases**. I then used the **Single Value** visualization in Splunk to display this result, which showed a total of **5,737** purchases.

![111i](https://github.com/KO443/Splunk-power-user-lab-Projects/blob/main/Images/111i.png?raw=true)

2. Next, I configured the color range in the Format panel. I set values from **0 to 100 sales** to display in **red**, and anything above **100** to appear in **green**. I also added a caption to the Single Value visualization, labeling it as **"Total Purchases Made"** and this was done by going to General and then Caption in the format panel.

![111j](https://github.com/KO443/Splunk-power-user-lab-Projects/blob/main/Images/111j.png?raw=true)

3. I changed the background color of **‘Total Purchase Price’** to green by clicking on **Color Mode**, and then I added it to the existing **‘Weekly Info’** dashboard. The dashboard is set up with the top panel displaying the **Total Purchase price**, a column chart showing the **Actions taken by shoppers by day**, and a pie chart below it showcasing the **Actions taken by shoppers by week**.
![111k](https://github.com/KO443/Splunk-power-user-lab-Projects/blob/main/Images/111k.png?raw=true)

![111L](https://github.com/KO443/Splunk-power-user-lab-Projects/blob/main/Images/111l.png?raw=true)

***********
***********








 
