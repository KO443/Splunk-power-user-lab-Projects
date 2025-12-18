
Splunk Search Processing Language (SPL) Guide Sheet
-


*"I didn’t create this SPL guide myself; I compiled it from resources I found online and documented it here as a reference for my Splunk work.*

*********************
Basic Commands
************************

| Command    | Description                   | Example                     |
| ---------- | ----------------------------- | --------------------------- |
| search     | Initiates a search for events | `index=web_logs status=200` |
| index      | Specifies the index to search | `index=web_logs`            |
| sourcetype | Filters events by sourcetype  | `sourcetype=apache_access`  |

**********
Filtering and Extraction
**********

| Command | Description                        | Example                                            |
| ------- | ---------------------------------- | -------------------------------------------------- |
| where   | Filters events using conditions    | `index=logs \| where status=200`                   |
| eval    | Creates or modifies fields         | `index=logs \| eval status_type="OK"`              |
| rex     | Regex extraction on fields         | `index=logs \| rex field=_raw "user=(?<user>\w+)"` |
| erex    | Regex extraction with named groups | `index=logs \| erex user`                          |

*******
Aggregation and Statistics
********

| Command    | Description                          | Example                                        |
| ---------- | ------------------------------------ | ---------------------------------------------- |
| stats      | Calculates statistics on fields      | `index=sales \| stats sum(amount)`             |
| timechart  | Time-based aggregation               | `index=web_logs \| timechart count`            |
| chart      | Creates charts from fields           | `index=web_logs \| chart count by status`      |
| eventstats | Adds aggregate values back to events | `index=transactions \| eventstats avg(amount)` |

**********
Grouping and Transactional Analysis
*********
| Command                  | Description                     | Example                                                     |
| ------------------------ | ------------------------------- | ----------------------------------------------------------- |
| transaction              | Groups related events           | `index=transactions \| transaction user`                    |
| stats count by           | Counts values per field         | `index=web_logs \| stats count by status`                   |
| stats earliest latest by | Retrieves first and last events | `index=logs \| stats earliest(_time) latest(_time) by user` |


*********
Field Manipulation
*********

| Command      | Description              | Example                                             |
| ------------ | ------------------------ | --------------------------------------------------- |
| fields       | Includes selected fields | `index=logs \| fields host, source`                 |
| rename       | Renames fields           | `index=logs \| rename src_ip AS client_ip`          |
| fieldformat  | Formats field values     | `index=metrics \| fieldformat value=round(value,2)` |
| addcoltotals | Adds column totals       | `index=sales \| addcoltotals`                       |


**************
Data Transformation
*******************

| Command           | Description                         | Example                                          |
| ----------------- | ----------------------------------- | ------------------------------------------------ |
| rex mode=sed      | Performs text replacement           | `index=logs \| rex mode=sed "s/error/warning/"`  |
| spath             | Extracts structured data (JSON/XML) | `index=logs \| spath`                            |
| spath output path | Extracts specific paths             | `index=logs \| spath output=user path=user.name` |
| spath default     | Assigns default values              | `index=logs \| spath default="unknown"`          |

*********
Lookup and Enrichment
***********

| Command      | Description                        | Example                                  |
| ------------ | ---------------------------------- | ---------------------------------------- |
| lookup       | Enriches events from lookup tables | `index=logs \| lookup users.csv user_id` |
| inputlookup  | Loads lookup data                  | `\| inputlookup users.csv`               |
| outputlookup | Writes results to lookup           | `index=logs \| outputlookup results.csv` |

**********
Advanced Analysis
*************

| Command         | Description                  | Example                                                                                |
| --------------- | ---------------------------- | -------------------------------------------------------------------------------------- |
| eval case()     | Conditional logic            | `eval priority=case(severity="High","Urgent",severity="Medium","Normal",true(),"Low")` |
| eval coalesce() | Returns first non-null value | `eval info=coalesce(a,b,c)`                                                            |
| eval round()    | Rounds numeric values        | `eval rounded=round(value,2)`                                                          |
| eval mvjoin()   | Joins multivalue fields      | `eval tags=mvjoin(tags,", ")`                                                          |
| eval strftime() | Converts epoch to date       | `eval time=strftime(_time,"%Y-%m-%d %H:%M:%S")`                                        |

*****************
Subsearch and Correlation
****************

| Command   | Description            | Example                                         |
| --------- | ---------------------- | ----------------------------------------------- |
| subsearch | Correlates events      | `index=access_logs [ search index=error_logs ]` |
| tstats    | Accelerated statistics | `\| tstats count where index=logs`              |

**************
Visualization & Reporting
***************

| Command        | Description            | Example                                     |
| -------------- | ---------------------- | ------------------------------------------- |
| timechart span | Time-based charts      | `index=web_logs \| timechart span=1h count` |
| geostats       | Geospatial aggregation | `index=locations \| geostats count`         |
| chart usenull  | Includes NULL values   | `index=logs \| chart count usenull=t`       |
| rangemap       | Maps values to ranges  | `index=sales \| rangemap field=amount`      |
| xyseries       | XY chart creation      | `index=metrics \| xyseries x y z`           |

***************
Alerting and Monitoring
**************


| Command     | Description              | Example                                      |
| ----------- | ------------------------ | -------------------------------------------- |
| alert       | Defines alert conditions | `index=errors \| stats count`                |
| collect     | Stores events            | `index=access_logs \| collect index=summary` |
| track_alert | Tracks alert activity    | `index=_audit action="alert_fired"`          |

**************
Batch Mode and Parallel Search
**************

| Command              | Description                   | Example                                                |
| -------------------- | ----------------------------- | ------------------------------------------------------ |
| multisearch          | Runs searches in parallel     | `\| multisearch [ search index=a ] [ search index=b ]` |
| multisearch SID      | Session-based parallel search | `\| multisearch SID=12345`                             |
| inputcsv             | Loads CSV data                | `\| inputcsv data.csv`                                 |
| inputlookup append=t | Appends lookup data           | `\| inputlookup append=t users.csv`                    |

******************
Working with Time
*******************

| Command           | Description                     | Example                                            |
| ----------------- | ------------------------------- | -------------------------------------------------- |
| strptime          | Converts string to timestamp    | `eval event_time=strptime(ts,"%Y-%m-%d %H:%M:%S")` |
| earliest / latest | Time range filters              | `index=logs earliest=-7d latest=now`               |
| bucket            | Groups events into time buckets | `index=logs \| bucket _time span=1h`               |

*************************
String Functions
***********************


| Command           | Description        | Example                           |
| ----------------- | ------------------ | --------------------------------- |
| substr            | Extracts substring | `eval short=substr(message,1,50)` |
| len               | String length      | `eval length=len(message)`        |
| toupper / tolower | Case conversion    | `eval upper=toupper(message)`     |

**********************************
Math and Numeric Functions
************************************

| Command     | Description           | Example                       |
| ----------- | --------------------- | ----------------------------- |
| round       | Rounds numbers        | `eval rounded=round(value)`   |
| abs         | Absolute value        | `eval absolute=abs(change)`   |
| sqrt        | Square root           | `eval root=sqrt(number)`      |
| power       | Exponentiation        | `eval squared=power(value,2)` |
| log / log10 | Logarithmic functions | `eval ln=log(value)`          |


*********************
Conditional and Logical Functions
******************

| Command        | Description            | Example                                                        |
| -------------- | ---------------------- | -------------------------------------------------------------- |
| if()           | Conditional evaluation | `eval status=if(code>=400,"Error","Success")`                  |
| case()         | Multi-condition logic  | `eval severity=case(level="High",3,level="Medium",2,true(),1)` |
| and / or / not | Logical operators      | `eval is_error=(status>=500 OR severity="High")`               |
| like()         | Pattern matching       | `eval match=like(message,"%error%")`                           |


**************
Multivalue Field Operations
**************

| Command                      | Description                | Example                           |
| ---------------------------- | -------------------------- | --------------------------------- |
| mvexpand                     | Expands multivalue fields  | `index=events \| mvexpand tags`   |
| mvzip / mvappend / mvcombine | Combines multivalue fields | `eval combined=mvzip(a,b,",")`    |
| mvcount                      | Counts multivalue entries  | `eval count=mvcount(tags)`        |
| mvfind                       | Searches multivalue fields | `eval found=mvfind(tags,"error")` |

*****************
Time and Date Functions
****************

| Command                | Description              | Example                                 |
| ---------------------- | ------------------------ | --------------------------------------- |
| now()                  | Current time             | `eval current=now()`                    |
| relative_time          | Relative timestamps      | `earliest=relative_time(now(),"-1d@d")` |
| date_month / date_wday | Extracts date components | `eval month=date_month(_time)`          |
| time()                 | Converts string to epoch | `eval t=time("2023-01-15 10:30:00")`    |
| date_part              | Extracts year/month/day  | `eval year=date_part(_time,"year")`     |


****************
IP, Geolocation, and Geospatial Functions
*************

| Command             | Description             | Example                                         |
| ------------------- | ----------------------- | ----------------------------------------------- |
| iplocation          | IP geolocation          | `index=logs \| iplocation client_ip`            |
| cidrmatch           | CIDR matching           | `cidrmatch("192.168.0.0/24", ip)`               |
| isipv4 / isipv6     | IP version check        | `eval is_ipv4=isipv4(ip)`                       |
| maxmindispolocation | MaxMind lookup          | `maxmindispolocation ipfield=client_ip`         |
| iptoname            | Resolves IP to hostname | `eval host=iptoname(dest_ip)`                   |
| geodistance         | Distance between points | `eval km=geodistance(lat1,lon1,lat2,lon2,"km")` |
| geopoint            | Creates geopoints       | `eval point=geopoint(lat,lon)`                  |


**********
Advanced Correlation and Deduplication
***********

| Command          | Description              | Example                                  |
| ---------------- | ------------------------ | ---------------------------------------- |
| stats first last | First and last values    | `stats first(_time) last(_time) by user` |
| eventstats       | Correlated stats         | `eventstats avg(amount) by user`         |
| rare             | Identifies rare values   | `index=errors \| rare status`            |
| dedup            | Removes duplicates       | `index=logs \| dedup session_id`         |
| multikv          | Extracts key-value pairs | `index=logs \| multikv`                  |
