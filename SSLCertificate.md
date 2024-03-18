# SSL certificate

> [!IMPORTANT]
> You need to create and have running a virtual machine on your Google Cloud Platform to complete these logs. Visit the [GCPVM.md](/GCPVM.md) technical log for the steps on how to do so.
> You also need to have created and connected a DuckDNS entry pointing to temporary IP address of GCP VM. Visit the [DuckDNS.md](/DuckDNS.md) technical log for the steps on how to do so.

In this log:

- [x] Creating an SSL certificate (18/03/24 | 10 mins)
- [x] Comparing server access with and without SSL certificate (18/03/24 | 5 mins)
- [x] References

Total Duration: 15 mins

---

## Creating and obtaining an SSL certificate

Learn how to create and obtain a free SSL certificate to use your GCP VM in ArcGIS Online or any other place

Assumption(s):
- You have already created and have running a virtual machine on Google Cloud Platform
- You have already created and connected a DuckDNS entry pointing to temporary IP address of GCP VM
- You are logged into the GCP VM via the remote desktop

Duration: 10 mins

### Steps

1. On the Remote Desktop, open ```Microsoft Edge``` web browser.

> [!NOTE]
> Yes, use Microsoft Edge. Do NOT try downloading Google Chrome on the machine.

2. Visit https://www.win-acme.com/.

3. Click ```Download``` dropdown menu, and from there, click ```2.1.23 (recommended)```. The zipped file should download quickly.

4. Open your **File Explorer** and go to your **Downloads**. 

5. Right-click on the zipped folder and click ```Extract All```.

6. In the search bar of the Remote Desktop, type in **IIS** and then click on the app called ```Internet Information Services (IIS) Manager```.
    - Expand the **DEMOAGS** on the lefthand side menu
    - Double-click ```Sites```
    - Click ```Default Web Site```
    - In the menu on the righthand side, under **Edit Site**, click ```Bindings...```
    - Click ```https``` to highlight that site type
    - Click ```Edit...```
    - Add your DuckDNS URL to the **Host name** to let it only apply to the new DNS entry
    - Accept all other defaults and click ```OK```
    - Your URL will now appear under **Host Name** for **https** site type
    - Click ```Close``` to close the **Site Bindings** window

6. In **File Explorer**, open the unzipped folder. 

7. Right-click the ```wacs.exe``` software program and click ```Run as administrator```.

> [!NOTE]
> If a **User Account Control** window pops up and asks if you want to allow the app from an unknown publisher to make changes to your device, click ```Yes```.

8. A **Command Prompt** window will pop up and start running. We are going to be entering some defaults...
    - Type **n** and click ```Enter``` on your keyboard to select the **Create certificate** option
    - Type **1** and click ```Enter``` on your keyboard to select the **Default Web Site** option. You should see your DuckDNS domain.
    - Type **A** and click ```Enter``` on your keyboard to select the **Pick *all* bindings** option
    - Click ```Enter``` on your keyboard to select default YES to continue with the selection (the * next to the y tells us that y is the default)
    - Click ```Enter``` on your keyboard to select default NO to not open the terms of service
    - Click ```Enter``` on your keyboard to select default YES to agree to the terms
    - Enter an **email address** so if there are any issues, they can get a hold of you. Click ```Enter``` on your keyboard.

9. The last message before the menu options should now read **Certificate [IIS] Default Web Site, (any host) created**.

:tada: *Congratulations! You have now completed the task of creating an SSL Certificate!*

> [!WARNING]
> If you are stopping here, remember to STOP the virtual machine or else it will continue to run and bill to your account.
> Visit the [GCPVM.md](/GCPVM.md) technical log to learn how to disconnect from the server.

> [!IMPORTANT]
> If you ever start and stop the VM, you need to update the IP address on DuckDNS, but the SSL Certificate will still be valid since it is against the DNS entry.

---

## Comparing server access with and without SSL certificate

Learn how to test your SSL certificate

Assumption(s):
- You have already created and have running a virtual machine on Google Cloud Platform
- You have already created and connected a DuckDNS entry pointing to temporary IP address of GCP VM
- You are logged into the GCP VM via the remote desktop
- You have already created an SSL certificaate

Duration: 5 mins

### Steps (without SSL certificate)

1. On the Remote Desktop, open up a web browser and type in your **DuckDNS domain** in the address bar and click ```Enter```.

> [!NOTE]
> The page may warn you that the connection isn't private.
> Click ```Advanced``` and click ```Continue to ___ (unsafe)``` to bypass this message.

2. There will be a red triangle icon with a ! in the center in the address bar, crossing out https and saying it is **Not secure**. Click this message to expand it.

3. This error is telling us that the certificate currently being used is the wrong one.


### Steps (with SSL certificate)

1. On the Remote Desktop, open up a web browser and type in your **DuckDNS domain** in the address bar and click ```Enter```.

2. With the certificate created, no errors will pop up - instead of the **red triangle ! icon**, there will be a **lock icon** next to your URL. If even after you create the SSL certificate the connection is insecure, try refreshing or starting and stopping your web browser.

3. Click the ```lock icon```.

4. Click ```Connection is secure```.

5. Click the ```certificate icon``` in the top righthand corner to view the certificate. 
    - Under **Issued To**, the **Common Name (CN)** is your DuckDNS URL
    - Under **Validity Period**, you will see when it was issued and when it will expire

:tada: *Congratulations! You have now completed the task of testing the SSL Certificate in a web browser of the remote desktop!*

> [!WARNING]
> If you are stopping here, remember to STOP the virtual machine or else it will continue to run and bill to your account.
> Visit the [GCPVM.md](/GCPVM.md) technical log to learn how to disconnect from the server.

> [!IMPORTANT]
> If you ever start and stop the VM, you need to update the IP address on DuckDNS, but the SSL Certificate will still be valid since it is against the DNS entry.

---

## References

Morgan, S. [Shawn's Spotlight on GIS]. (2023, January 19). GCP Part 4: Getting a free SSL certificate [Video]. YouTube. https://www.youtube.com/watch?v=eTNtJNn5j74 