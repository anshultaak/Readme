
### Best practices for creating dashboards

* When creating a new dashboard, make sure it has a meaningful name.
* If you are creating a dashboard to play or experiment, then put the word TEST or TMP in the name.
* Consider including your name or initials in the dashboard name or as a tag so that people know who owns the dashboard.
* Remove temporary experiment dashboards when you are done with them.
* If you create many related dashboards, think about how to cross-reference them for easy navigation. 
* Grafana retrieves data from a data source. A basic understanding of data sources in general and your specific is important.
* Avoid unnecessary dashboard refreshing to reduce the load on the network or backend. For example, if your data changes every hour, then you don’t need to set the dashboard refresh rate to 30 seconds.
* Use the left and right Y-axes when displaying time series with different units or ranges.

#### Add documentation to dashboards and panels.
* To add documentation to a dashboard, add a Text panel visualization to the dashboard. Record things like the purpose of the dashboard, useful resource links, and any instructions users might need to interact with the dashboard.
* To add documentation to a panel, edit the panel settings and add a description. Any text you add will appear if you hover your cursor over the small i in the top left corner of the panel.

### Best practices for managing dashboards
* Avoid dashboard sprawl, meaning the uncontrolled growth of dashboards. Dashboard sprawl negatively affects time to find the right dashboard. Duplicating dashboards and changing “one thing” (worse: keeping original tags) is the easiest kind of sprawl.
   * Periodically review the dashboards and remove unnecessary ones.
   * If you create a temporary dashboard, perhaps to test something, prefix the name with TEST: . Delete the dashboard when you are finished.
* Copying dashboards with no significant changes is not a good idea
   * You miss out on updates to the original dashboard, such as documentation changes, bug fixes, or additions to metrics.
* Maintain a dashboard of dashboards or cross-reference dashboards. This can be done in several ways:
   * Create dashboard links, panel, or data links. Links can go to other dashboards or to external systems. For more information, refer to Manage dashboard links.
   * Add a Dashboard list panel. You can then customize what you see by doing tag or folder searches.
   * Add a Text panel and use markdown to customize the display.
