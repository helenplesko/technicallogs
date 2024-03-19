# GCP Virtual Machine on Esri ArcGIS Products

> [!IMPORTANT]
> You need to create a virtual machine on your Google Cloud Platform to complete these logs. Visit the [GCPVM.md](/GCPVM.md) technical log for the steps on how to do so.
> For accessing the GCP VM on the Remote Desktop, review the steps in the [GCPVMRemoteDesktop.md](/GCPVMRemoteDesktop.md) technical log.

In this log:

- [x] Connect to your GCP server to an ArcGIS Pro project (18/03/24 | 10 mins)
- [x] Publish map service to GCP ArcGIS Server from ArcGIS Pro (18/03/24 | 60 mins)
- [x] Publish map to AGOL from GCP VM Rest Services with and without port access (18/03/24 | 10 mins)
- [x] References

Total Duration: 80 mins

---

## Connect to your GCP server to an ArcGIS Pro project

Learn how to connect to your GCP server to an ArcGIS Pro project

Assumption(s):
- You have already created and have running a virtual machine on Google Cloud Platform
- You have an Esri ArcGIS account with ArcGIS Pro privileges

Duration: 10 mins

### Steps

1. Navigate to your VM Instances page through Google Cloud Platform, which can be accessed by going to https://console.cloud.google.com/, clicking on the ```hamburger button``` on the top-left corner of the page, hovering over ```Compute Engine``` and clicking ```VM Instances```. 

![VM instance navigation](/images/GCPVMArcGIS/VMInstance.png)

2. Double check that your server is running (green dot icon under Status). Copy the **External IP**.

![running VM](/images/GCPVMArcGIS/VMrunning.png)

3. Open a new project in **ArcGIS Pro**.

4. Add a new server connection via the following steps:
    - Click ```Insert``` tab
    - Click ```Connections```
    - Click ```Server```
    - Click ```New ArcGIS Server```
    - Enter **Server URL** as your https://externalip:6443/arcgis
    - Enter **Authentication** provided to us in the documentation

![Connect Server](/images/GCPVMArcGIS/AGPtoAGSConnectServer.png)

![Server connection](/images/GCPVMArcGIS/AGPtoAGSServerConnection.png)

> [!NOTE]
> If a **Security** alert pops up saying that the certificate issuer for the site is untrusted or unknown, click ```Yes``` to proceed anyways.

![Security alert](/images/GCPVMArcGIS/AGPtoAGSSecurityAlert.png)

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
- You are signed into the Remote Desktop

Duration: 40 mins

### Steps

1. On your Remote Desktop AND on your local computer:
    - Ensure the **Canada shapefile** and all files associated with it are copied from the desktop to the ```C:\GISWorkspace\Canada``` file path
    - The folder path must be the same

![Canada file path](/images/GCPVMArcGIS/AGPtoAGSCanadaFolder.png)

2. Double check that you are connected to the Server:
    - In the **Catalog Pane**, expand the **Servers**.
    - If you see the server, you may proceed to the next step. 
    - If you do not see the server, refer back to the first task in this technical log.

3. Once you are connected, in the **Catalog Pane**:
    - Right click on ```Folders```
    - Click ```Add a folder connection```
    - Navigate to ```C:\GISWorkspace\Canada``` on your local computer

![Folder connection](/images/GCPVMArcGIS/AGPtoAGSConnectFolder.png)

4. Once the folder connection is made, in the **Catalog Pane**:
    - Right click ```Canada.shp```
    - Click ```Add to current map```

![Canada layer added to ArcGIS Pro](/images/GCPVMArcGIS/AGPtoAGSOGCanadaLayer.png)

5. Once the shapefile has been added to the current map, in the **Contents Pane**:
    - Right click the ```Canada``` polygon feature
    - Click ```Symbology```
    - Change the symbology of the layer to best represent Canada and its provinces and territories

![Change symbology of Canada](/images/GCPVMArcGIS/AGPtoAGSChangeSymbology.png)

6. After the symbology has been changed, in the **Catalog Pane**:
    - Expand the **Servers** folder
    - Right click on the server
    - Click ```Publish```
    - Click ```Map Service```

![Publish map service](/images/GCPVMArcGIS/AGPtoAGSPublishMapService.png)

> [!NOTE]
> If you do not see the ```Publish``` option, you will not be able to complete this task.
> Contact the administrator of the server, as you currently do not have publishing rights.

7. This will open up a directory to select the map you wish to publish:
    - Under **Projects** on the lefthand side, click ```Map```
    - Click the map you wish to publish
    - Click ```OK```

![Select map to publish](/images/GCPVMArcGIS/AGPtoAGSSelectMapToPublish.png)

8. The **Publish Map Service** menu will appear in the **Catalog Pane**:
    - Add a **name** for your map
    - Add relevant **tags**
    - Select a **folder** to store the map service
    - Click ```Analyze```

![Publish map service directory](/images/GCPVMArcGIS/AGPtoAGSPublishMapService2.png)

9. Some errors and warnings may appear:
    - **Errors** will have a red circle with an x inside of it
    - **Warnings** will have a yellow triangle with a ! inside of it

10. All errors must be fixed. Some warnings can go unfixed.
    - Right click on the error or warning and it may give you a solution right away.
    - To resolve the **Error** saying *Unique numeric IDs are not assigned*:
        - Right click the error
        - Click ```Auto-Assign IDs Sequentially```
        - This should resolve it, and instead of a red circle with an x in the center, the error should now have a green checkmark
    - To resolve the **Warning** saying *Data source is not registered with the server*:
        - Right click the warning
        - Register the connection
        - Add a **name**
        - Ensure the publisher folder path is the same as the server folder path: ```C:\GISWorkspace\Canada```
        - Click ```Create```
        - This should resolve it, and instead of a yellow triangle with a ! in the center, the warning should now have a green checkmark

> [!IMPORTANT]
> If this warning is not resolved, the data will be COPIED, but we want the data to be REFERENCED

![Map Service warnings and errors](/images/GCPVMArcGIS/AGPtoAGSWarnings.png)

11. In the **Publish Map Service** menu:
    - Click ```Publish```
    - It will analyze again for errors and warnings, then publish the map service to the server

12. Check that the map service has published to the server properly:
    - Navigate to your GCP VM **ArcGIS Rest Services** site ```https://externalip:6443/arcgis/rest/services``` or ```https://domain.duckdns.org:6443/arcgis/rest/services```. The published map service should appear.

    ![Map service in rest services](/images/GCPVMArcGIS/AGPtoAGSMapServerRest1.png)

    ![Canada layer](/images/GCPVMArcGIS/AGPtoAGSMapServerRest2.png)

    - Access it through the **ArcGIS API for JavaScript**

    ![ArcGIS API for JS](/images/GCPVMArcGIS/AGPtoAGSFinal.png)

    - Navigate to your GCP VM **ArcGIS Manager** site ```https://externalip:6443/arcgis/manager``` or ```https://domain.duckdns.org:6443/arcgis/manager```. The published map service should appear.

    ![ArcGIS manager published map service](/images/GCPVMArcGIS/AGPtoAGSManager.png)

13. You can now use it in AGOL, too!
    - Follow the next task in this log to do so.

![published Canada map in AGOL](/images/GCPVMArcGIS/AGPtoAGSAGOL.png)

:tada: *Congratulations! You have now completed the task of publishing a map service in ArcGIS Pro to the ArcGIS Server!*

> [!WARNING]
> If you are stopping here, remember to STOP the virtual machine or else it will continue to run and bill to your account.
> Visit the [GCPVM.md](/GCPVM.md) technical log to learn how to disconnect from the server.

---

## Publish map to AGOL from GCP VM Rest Services with and without port access

Learn how to publish a map service to ArcGIS Online from GCP VM Rest Services

Assumption(s):
- You have already created and have running a virtual machine on Google Cloud Platform
- You have an ArcGIS Online Developer Account or ArcGIS Online College-provided Organization Account

Duration: 10 mins

### Steps

1. Navigate to your GCP VM Rest Services site ```https://externalip:6443/arcgis/rest/services``` or ```https://domain.duckdns.org:6443/arcgis/rest/services```

2. Under **Services:** click ```SampleWorldCities (MapServer)```.

![Rest Services](/images/GCPVMArcGIS/SampleWorldCitiesRest.png)

3. Next to **View As:** click ```ArcGIS Online Map Viewer``` to bring it into ArcGIS Online.

![SampleWorldCities Rest Services](/images/GCPVMArcGIS/AGStoAGOLSWCRest.png)

4. If not already signed in, sign in to your AGOL account.

![AGOL sign in window](/images/GCPVMArcGIS/AGStoAGOLSignIn.png)

5. In the sidebar, click ```Save as``` to save the map to the Content of your AGOL account.
    - Give it a name
    - Add any tags
    - Click ```Save```

![SampleWorldCities Map in AGOL](/images/GCPVMArcGIS/AGStoAGOLFinal.png)

:tada: *Congratulations! You have now completed the task of publishing a map to AGOL from GCP VM Rest Services!*

> [!WARNING]
> If you are stopping here, remember to STOP the virtual machine or else it will continue to run and bill to your account.
> Visit the [GCPVM.md](/GCPVM.md) technical log to learn how to disconnect from the server.

### Without Port Access

- If you do not have access to go through port :6443, you will not be able to see the layer in AGOL - the layer will be unsupported.
- You can save the map to your Content, but it will not have any features or layers, just the basemap.

![Map Service without port access](/images/GCPVMArcGIS/AGPtoAGSUnsupportedLayer.png)

---

## References

Morgan, S. [Shawn's Spotlight on GIS]. (2023, January 19). Geom99 - GCP Part 2: Creating your VM from the image [Video]. YouTube. https://www.youtube.com/watch?v=dyFeyBX9jIY