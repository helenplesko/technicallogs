# GCP Virtual Machine on Esri ArcGIS Products

> [!IMPORTANT]
> You need to create a virtual machine on your Google Cloud Platform to complete these logs. Visit the [GCPVM.md](/GCPVM.md) technical log for the steps on how to do so.
> For accessing the GCP VM on the Remote Desktop, review the steps in the [GCPVMRemoteDesktop.md](/GCPVMRemoteDesktop.md) technical log.

In this log:

- [x] Connect to your GCP server to an ArcGIS Pro project (18/03/24 | 10 mins)
- [x] Publish map service to GCP ArcGIS Server from ArcGIS Pro (18/03/24 | 40 mins)
- [x] Publish map to AGOL from GCP VM Rest Services (18/03/24 | 10 mins)
- [ ] References

Total Duration: 60 mins

---

## Connect to your GCP server to an ArcGIS Pro project

Learn how to connect to your GCP server to an ArcGIS Pro project

Assumption(s):
- You have already created and have running a virtual machine on Google Cloud Platform
- You have an Esri ArcGIS account with ArcGIS Pro privileges

Duration: 10 mins

### Steps

1. Navigate to your VM Instances page through Google Cloud Platform, which can be accessed by going to https://console.cloud.google.com/, clicking on the ```hamburger button``` on the top-left corner of the page, hovering over ```Compute Engine``` and clicking ```VM Instances```. 

2. Double check that your server is running (green dot icon under Status). Copy the **External IP**.

3. Open a new project in **ArcGIS Pro**.

4. Add a new server connection via the following steps:
    - Click ```Insert``` tab
    - Click ```Connections```
    - Click ```Server```
    - Click ```New ArcGIS Server```
    - Enter **Server URL** as your https://externalip:6443/arcgis
    - Enter **Authentication** provided to us in the documentation

> [!NOTE]
> If a **Security** alert pops up saying that the certificate issuer for the site is untrusted or unknown, click ```Yes``` to proceed anyways.

> [!TIP]
> Best to NOT save login at this time, since the external IP is going to change every time the VM is started and stopped.

5. Check that the Server is connected by navigating to your **Catalog Pane** in your project and click ```Servers```. You should see the arcgis server there.

:tada: *Congratulations! You have now completed the task of connecting your server to an ArcGIS Pro project!*

> [!WARNING]
> If you are stopping here, remember to STOP the virtual machine or else it will continue to run and bill to your account.
> Visit the [GCPVM.md](/GCPVM.md) technical log to learn how to disconnect from the server.

---

## Publish map service to GCP ArcGIS Server from ArcGIS Pro

Learn how to consume the data published on the GCP stand-alone ArcGIS Server and display it in a Web Map on ArcGIS Online

Assumption(s):
- You have already created and have running a virtual machine on Google Cloud Platform
- You have an ArcGIS Online Developer Account or ArcGIS Online College-provided Organization Account
- You have already connected your server to the ArcGIS Pro project

Duration: 40 mins

### Steps

1. In your ArcGIS Pro project, double check that the Server is connected by navigating to your **Catalog Pane** in your project and click ```Servers```. You should see the arcgis server there.

2. In the **Catalog Pane**, right click ```Folders``` and click ```

3. 

4. 

---

## Publish map to AGOL from GCP VM Rest Services

Learn how to publish a map service to ArcGIS Online from GCP VM Rest Services

Assumption(s):
- You have already created and have running a virtual machine on Google Cloud Platform
- You have an ArcGIS Online Developer Account or ArcGIS Online College-provided Organization Account

Duration: 10 mins

### Steps

1. Navigate to your GCP VM Rest Services site ```https://externalip:6443/arcgis/rest/services``` or ```https://domain.duckdns.org:6443/arcgis/rest/services```

2. Under **Services:** click ```SampleWorldCities (MapServer)```.

![Rest Services](../images/GCPVMArcGIS/SampleWorldCitiesRest.png)

3. Then click ```ArcGIS Online Map Viewer``` to bring it into ArcGIS Online.

![SampleWorldCities Rest Services](../images/GCPVMArcGIS/AGStoAGOLSWCRest.png)

4. If not already signed in, sign in to your AGOL account.

![AGOL sign in window](../images/GCPVMArcGIS/AGStoAGOLSignIn.png)

5. In the sidebar, click ```Save as``` to save the map to the Content of your AGOL account.
    - Give it a name
    - Add any tags
    - Click ```Save```

![SampleWorldCities Map in AGOL](../images/GCPVMArcGIS/AGStoAGOLFinal.png)

:tada: *Congratulations! You have now completed the task of publishing a map to AGOL from GCP VM Rest Services!*

> [!WARNING]
> If you are stopping here, remember to STOP the virtual machine or else it will continue to run and bill to your account.
> Visit the [GCPVM.md](/GCPVM.md) technical log to learn how to disconnect from the server.

---

## References

Morgan, S. [Shawn's Spotlight on GIS]. (2023, January 19). Geom99 - GCP Part 2: Creating your VM from the image [Video]. YouTube. https://www.youtube.com/watch?v=dyFeyBX9jIY