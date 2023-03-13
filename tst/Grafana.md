
### Best practices for creating dashboards

* When creating a new dashboard, make sure it has a meaningful name.
* If you are creating a dashboard to play or experiment, then put the word TEST or TMP in the name.
* Consider including your name or initials in the dashboard name or as a tag so that people know who owns the dashboard.
* Remove temporary experiment dashboards when you are done with them.
* If you create many related dashboards, think about how to cross-reference them for easy navigation. 
* Grafana retrieves data from a data source. A basic understanding of data sources in general and your specific is important.
* Avoid unnecessary dashboard refreshing to reduce the load on the network or backend. For example, if your data changes every hour, then you don’t need to set the dashboard refresh rate to 30 seconds.
* Use the left and right Y-axes when displaying time series with different units or ranges.
