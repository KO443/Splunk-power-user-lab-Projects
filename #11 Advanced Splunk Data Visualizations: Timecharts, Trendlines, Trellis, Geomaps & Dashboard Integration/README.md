In this lab, I demonstrate how to create visualizations using SPL commands, followed by configuring formatting options and selecting appropriate chart types in the visualization panel.
<br><br>
1. Using a **Timechart command** - which is an SPL visualization command that displays statistical trends over time. This search queries the **web** index and uses the** timechart command** to calculate the daily average of the **bytes** field, grouping the results by **host**, producing a time-series view that shows how the average amount of data transferred changes over time for each host.  
![111a](https://github.com/KO443/Splunk-power-user-lab-Projects/blob/main/Images/111a.png?raw=true)

2. In this part, the command was changed to chart, which produces a static aggregation without a time-based x-axis, unlike timechart, which generates a time-series visualization showing how the average amount of data transferred changes over time for each host.
![111b](https://github.com/KO443/Splunk-power-user-lab-Projects/blob/main/Images/111b.png?raw=true)
 
3. This Splunk search queries events from the **web** index, the **isnotnull** command filters out any records where the **action** field is missing to ensure only meaningful user **actions** are analyzed, and then uses the **timechart** command to count occurrences of each action over time, grouping the results by action to produce a time-series visualization that shows how different actions trend and change across the selected time range.
 
 ![111d](https://github.com/KO443/Splunk-power-user-lab-Projects/blob/main/Images/111d.png?raw=true)
 
 The chart above is currently displayed as a column chart with an overlay which is the green line that runs above my charts. In my earlier visualization examples, I used a line chart instead. In the next section, I’ll walk through how I switch between chart types in Splunk and highlight some of the other visualization features available.

4. In the screenshot below, I’ve marked two key areas with a red arrow: the **Column Chart** selector and the **Format** menu. The button showing ‘Column Chart’ is the visualization selector, so this is where I switch between chart types or choose a completely different visualization. The **Format** panel (the page displaying screenshot) lets me adjust settings such as the X‑axis, Y‑axis, chart overlays, and legend options.<br><br>
Additionally, Splunk’s **Trellis** layout allows me to split search results into multiple small panels, each based on a specific field or aggregation, making it easier to compare patterns across different segments of the data.

![111c](https://github.com/KO443/Splunk-power-user-lab-Projects/blob/main/Images/111c.png?raw=true)

5. 
 
