Basic Commands

Command	Description	Example
search	Initiates a search for events	index=web_logs status=200
index	Specifies the index to search	index=web_logs
sourcetype	Filters events by sourcetype	sourcetype=apache_access
Filtering and Extraction

Command	Description	Example
where	Filters events using conditions	`index=logs
eval	Creates or modifies fields	`index=logs
rex	Regex extraction on fields	`index=logs
erex	Regex extraction with named groups	`index=logs
Aggregation and Statistics

Command	Description	Example
stats	Calculates statistics on fields	`index=sales
timechart	Time-based aggregation	`index=web_logs
chart	Creates charts from fields	`index=web_logs
eventstats	Adds aggregate values back to events	`index=transactions
Grouping and Transactional Analysis

Command	Description	Example
transaction	Groups related events	`index=transactions
stats count by	Counts values per field	`index=web_logs
stats earliest latest by	Retrieves first and last events	`index=logs
Field Manipulation

Command	Description	Example
fields	Includes selected fields	`index=logs
rename	Renames fields	`index=logs
fieldformat	Formats field values	`index=metrics
addcoltotals	Adds column totals	`index=sales
Data Transformation

Command	Description	Example
rex mode=sed	Performs text replacement	`index=logs
spath	Extracts structured data (JSON/XML)	`index=logs
spath output path	Extracts specific paths	`index=logs
spath default	Assigns default values	`index=logs
Lookup and Enrichment

Command	Description	Example
lookup	Enriches events from lookup tables	`index=logs
inputlookup	Loads lookup data	`
outputlookup	Writes results to lookup	`index=logs
Advanced Analysis

Command	Description	Example
eval case()	Conditional logic	eval priority=case(severity="High","Urgent",severity="Medium","Normal",true(),"Low")
eval coalesce()	Returns first non-null value	eval important_info=coalesce(critical_message,warning_message,info_message)
eval round()	Rounds numeric values	eval rounded_value=round(value,2)
eval mvjoin()	Joins multivalue fields	eval combined_tags=mvjoin(tags,", ")
eval strftime()	Converts epoch to date	eval formatted_time=strftime(_time,"%Y-%m-%d %H:%M:%S")
Subsearch and Correlation

Command	Description	Example
subsearch	Correlates events	`index=access_logs [ search index=error_logs
tstats	Accelerated statistics	`
Visualization and Reporting

Command	Description	Example
timechart span	Time-based charts	`index=web_logs
geostats	Geospatial aggregation	`index=locations
chart usenull	Includes NULL values	`index=logs
rangemap	Maps values to ranges	`index=sales
xyseries	XY chart creation	`index=metrics
Alerting and Monitoring

Command	Description	Example
alert	Defines alert conditions	`index=errors
collect	Stores events	`index=access_logs
track_alert	Tracks alert activity	`index=_audit action="alert_fired"
Batch Mode and Parallel Search

Command	Description	Example
multisearch	Runs searches in parallel	`
multisearch SID	Session-based parallel search	`
inputcsv	Loads CSV data	`
inputlookup append=t	Appends lookup data	`
Working with Time

Command	Description	Example
strptime	Converts string to timestamp	eval event_time=strptime(timestamp,"%Y-%m-%d %H:%M:%S")
earliest/latest	Time range filters	index=logs earliest=-7d latest=now
bucket	Groups events into time buckets	`index=logs
String Functions

Command	Description	Example
substr	Extracts substring	eval short_message=substr(message,1,50)
len	String length	eval message_length=len(message)
toupper/tolower	Case conversion	eval uppercase_message=toupper(message)
Math and Numeric Functions

Command	Description	Example
round	Rounds numbers	eval rounded_value=round(value)
abs	Absolute value	eval absolute_value=abs(change)
sqrt	Square root	eval square_root=sqrt(number)
power	Exponentiation	eval squared_value=power(value,2)
log/log10	Logarithmic functions	eval ln_value=log(value)
Conditional and Logical Functions

Command	Description	Example
if()	Conditional evaluation	eval status_type=if(status>=400,"Error","Success")
case()	Multi-condition logic	eval severity_level=case(severity="High",3,severity="Medium",2,true(),1)
and/or/not	Logical operators	eval is_error=(severity="High" OR status>=500)
like()	Pattern matching	eval is_error=like(message,"%error%")
Multivalue Field Operations

Command	Description	Example
mvexpand	Expands multivalue fields	`index=events
mvzip/mvappend/mvcombine	Combines multivalue fields	eval combined_fields=mvzip(field1,field2,",")
mvcount	Counts multivalue entries	eval tag_count=mvcount(tags)
mvfind	Searches multivalue fields	eval has_error=mvfind(tags,"error")
Time and Date Functions

Command	Description	Example
now()	Current time	eval current_time=now()
relative_time	Relative timestamps	earliest=relative_time(now(),"-1d@d")
date_month/date_wday	Extracts date components	eval month=date_month(_time)
time()	Converts string to epoch	eval event_time=time("2023-01-15 10:30:00")
date_part	Extracts year/month/day	eval year=date_part(_time,"year")
IP, Geolocation, and Geospatial Functions

Command	Description	Example
iplocation	IP geolocation	`index=logs
cidrmatch	CIDR matching	cidrmatch(ip,"192.168.0.0/24")
isipv4/isipv6	IP version check	eval is_ipv4=isipv4(ip_address)
maxmindispolocation	MaxMind lookup	maxmindispolocation ipfield=client_ip
iptoname	Resolves IP to hostname	eval hostname=iptoname(destination_ip)
geodistance	Distance between points	eval distance_km=geodistance(lat1,lon1,lat2,lon2,"km")
geopoint	Creates geopoints	eval geopoint=geopoint(latitude,longitude)
Advanced Correlation and Deduplication

Command	Description	Example
stats first last	First and last values	stats first(_time) last(_time) by user
eventstats	Correlated stats	eventstats avg(amount) as avg_amount by user
rare	Identifies rare values	`index=errors
dedup	Removes duplicates	`index=logs
multikv	Extracts key-value pairs	`index=logs
License

This cheat sheet is provided for educational and operational use.
Splunk is a registered trademark of Splunk Inc
