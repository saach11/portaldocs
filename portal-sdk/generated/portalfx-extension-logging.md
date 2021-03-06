<a name="logging"></a>
## Logging
 The portal provides a way for extensions to log to MDS using a feature that can be enabled in the extension.

 More information about the portal logging feature can be found here [https://auxdocs.azurewebsites.net/en-us/documentation/articles/portalfx-telemetry-logging](https://auxdocs.azurewebsites.net/en-us/documentation/articles/portalfx-telemetry-logging)

 The logs generated by the extension when this feature is enabled can be found in a couple of tables in the portal's MDS account

Trace Events

>https://ailoganalyticsportal-privatecluster.cloudapp.net/clusters/Azportal/databases/AzurePortal?query=ExtEvents%7Cwhere+PreciseTimeStamp%3Eago(10m)

>ExtEvents | where PreciseTimeStamp >ago(10m)

Telemetry Events


>https://ailoganalyticsportal-privatecluster.cloudapp.net/clusters/Azportal/databases/AzurePortal?query=ExtTelemetry%7Cwhere+PreciseTimeStamp%3Eago(10m)

>ExtTelemetry | where PreciseTimeStamp >ago(10m)

<a name="monitoring"></a>
## Monitoring
 There are two categories of issues that needs to be monitored for each extension and that partners can act on.

 * Portal loading and running the extension

    The portal already has alerts setup to notify extensions of when it fails to load the extension for any reason. More work is being done to monitor other issues like blade load failures and part load failures.

 * Hosting Service downloading and service the extension

    The hosting service will ping the endpoint where it expects to find the extension bits every minute. It will then download any new configurations and verions it finds. If it fails to download or process the downloaded files it log these as errors in its own MDS tables.
    We are working on setting up alerts and monitors for such issues. Currently we get notified if any errors or warnings are generated by the hosting service. 
    You can access the logs of the hosting service using the below link
    https://jarvis-west.dc.ad.msft.net/53731DA4
