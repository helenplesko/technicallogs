# GCP Virtual Machine on the Remote Desktop

> [!IMPORTANT]
> You need to create a virtual machine on your Google Cloud Platform to complete these logs. Visit the [GCPVM.md](/GCPVM.md) technical log for the steps on how to do so.

In this log:

- [x] Accessing the Remote Desktop
- [x] Setting Firewall Rules on the Remote Desktop
- [x] How to check your ArcGIS Server Manager and REST Endpoints
- [x] How to Start and Stop Your GCP Virtual Machine on the Remote Desktop
- [x] References

---

## Connecting to the Remote Desktop

Learn how to connect to the remote desktop

Assumption(s):
- You have already created a vitual machine on Google Cloud Platform

Duration: 10 mins

### Steps

1. Ensure you are on the VM Instances page through Google Cloud Platform, which can be accessed by clicking on the ```hamburger button``` on the top-left corner of the page, hovering over ```Compute Engine``` and clicking ```VM Instances```.

2. Copy the **External IP** address for you VM Instance.

3. On your Windows computer, search for **Remote Desktop**.

4. Click the app that appears in the search called ```Remote Desktop Connection```. A new window will appear.

5. In the new window, paste your external IP address and add port **:444** to the end of it and click ```Connect```.

6. If you are prompted to just put in your password (no username), click ```More choices``` and click ```Use a different account```.

7. Enter **username** and **password** from your VM (saved in your Notepad++) and click ```OK```.

8. If given a warning that the remote computer cannot be verified, click ```Yes``` to connect anyways.

9. The remote desktop will then take over your screen.

:tada: *Congratulations! You have now learned how to connect to the remote desktop from your computer*

> [!WARNING]
> Once connected to your Remote Desktop, at the top, you will see a bar. You can minimize the remote computer screen or change other settings. Clicking the X in the bar at the top of your remote desktop does **NOT** turn the computer off or shut down your virtual machine. It simply "turns off the monitor". The computer is still running and you are still logged in.
> See below for more details on how to disconnect your VM from the remote desktop.

---

## Setting Firewall Rules for GCP Virtual Machine on Remote Desktop

Learn how to create a Firewall Rule on the remote desktop to only allow certain ports to access ArcGIS Server Manager on the GCP Virtual Machine

Assumption(s):
- You have already created a vitual machine on Google Cloud Platform
- You are already connected to the remote desktop

Expected Duration: 10 mins

### Steps

1. On the remote desktop, search for **Firewall with Advanced Settings**.

2. Click the desktop app that reads ```Windows Defender Firewall with Advanced Security```. A new window will appear.

3. In the Windows Defender Firewall with Advanced Security window, click ```Inbound Rules``` on the lefthand side.

4. Click ```New Rule``` in the **Actions** sidebar, under **Inbound Rules**
    - For **Rule Type**, select ```Port``` to control the connections for a TCP or UDP port. Click ```Next```.
    - For **Protocols and Ports**, apply the rule to ```TCP``` and specify local ports ```6643,6080```. Click ```Next```.
    - For **Action**, select ```Allow the connection``` to include connections that are protected with IPsec as well as those that are not. Click ```Next```.
    - For **Profile**, ensure ```Domain```, ```Private```, and ```Public``` are all selected. Click ```Next```.
    - For **Name**, enter a ```Name``` for the Firewall. You can also enter a description, although this is optional. Click ```Finish```. 

5. In the Windows Defender Firewall with Advanced Security window, you will now see your new rule under **Inbound Rules**.

:tada: *Congratulations! You have now learned how to set a firewall rule on the remote desktop*
    
> [!NOTE] 
> The firewall rule will go live immediately and persist after any restart of the server. 

> [!WARNING]
> If you are stopping here, remember to **SHUT DOWN** the remote desktop to stop the virtual machine or else it will continue to run and bill to your account.
> See below for more details on how to disconnect your VM from the remote desktop.

---

## How to check your ArcGIS Server Manager and REST Endpoints on the Remote Desktop

Learn how to access manager capabilities of the GCP virtual machine through ArcGIS Server Manager on the remote desktop

Assumption(s):
- You have already created a vitual machine on Google Cloud Platform
- You are already connected to the remote desktop

Expected Duration: 5 mins

### Steps

1. Ensure you are on the VM Instances page through Google Cloud Platform, which can be accessed by clicking on the ```hamburger button``` on the top-left corner of the page, hovering over ```Compute Engine``` and clicking ```VM Instances```.

2. Copy the **External IP** address for you VM Instance.

3. On the remote desktop, open a new browser and paste the external IP address followed by **/arcgis/rest/services**. Hit ```Enter``` on your keyboard.

4. The page should now result in the REST endpoint for your server.

5. To access the ArcGIS Server Manager, type in the IP address followed by **/arcgis/manager**.

:tada: *Congratulations! You have now learned how to check the REST endpoint and ArcGIS Server Manager of your server on the remote desktop.*

> [!WARNING]
> If you are stopping here, remember to **SHUT DOWN** the remote desktop to stop the virtual machine or else it will continue to run and bill to your account.
> See below for more details on how to disconnect your VM from the remote desktop.

---

## How to Start and Stop Your GCP Virtual Machine on the Remote Desktop

Learn how to stop your virtual machine when it is not in use and resume it when you would like to use it again. This is an important step because you do not want unwanted charges on your account as the server will run in the background if it is not stopped.

Assumption(s):
- You have already created a vitual machine on Google Cloud Platform
- You are already connected to the remote desktop

Expected Duration: 5 mins

### Steps 

1. On the remote desktop, click the ```Start``` menu.

2. Click ```Power```.

3. Click ```Shut Down```.

4. A window may pop up saying that your remote desktop services session has ended. Click ```OK```.

5. On your VM Instances page, the Status of your VM will update to a grey dot with a white 'stop' symbol in the center.

    > [!NOTE] 
    > The VM Instances page can be accessed through Google Cloud Platform by clicking on the ```hamburger button``` on the top-left corner of the page, hovering over ```Compute Engine``` and clicking ```VM Instances```.

6. If you would like to start it up again, simply click the three dots and then ```Start / Resume```.

:tada: *Congratulations! You have now learned how to start and stop your virtual machine through the Remote Desktop.*

---

## References

Morgan, S. [Shawn's Spotlight on GIS]. (2023, January 19). Geom99 - GCP Part 2: Creating your VM from the image [Video]. YouTube. https://www.youtube.com/watch?v=dyFeyBX9jIY