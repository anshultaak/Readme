### What is Grafana

Grafana is a database monitoring and analysis tool. It enables us to build dashboards visualizations of the essential measures that we need to analyze. It has a good community of enthusiasts who will share recyclable dashboards.


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

### Alerts
* If you're using Grafana Alerting, then you can have alerts sent through a number of different alert notifiers, including PagerDuty, SMS, email, VictorOps, OpsGenie, or Slack.
* Alert hooks allow you to create different notifiers with a bit of code if you prefer some other channels of communication. Visually define alert rules for your most important metrics.

### Dashboard variables
* Template variables allow you to create dashboards that can be reused for lots of different use cases. Values aren’t hard-coded with these templates, so for instance, if you have a production server and a test server, you can use the same dashboard for both.
* Templating allows you to drill down into your data, say, from all data to North America data, down to Texas data, and beyond. You can also share these dashboards across teams within your organization—or if you create a great dashboard template for a popular data source, you can contribute it to the whole community to customize and use.

### Issue dashboards
* This is a type of Grafana dashboard created for investigating a specific issue. Their use is scoped to a limited time, after which they become obsolete or stale.
* You may say that Grafana Explore is the right tool for this use case, because it allows you to run ad-hoc disposable queries. But what if it’s a hard-to-diagnose issue you have been chasing for weeks or months?
* I argue that there is a case for setting up a folder for such dashboards. You may also add a timestamp or an issue number in the dashboard title.
