# DuckDNS

> [!IMPORTANT]
> You need to create a virtual machine on your Google Cloud Platform to complete these logs. Visit the [GCPVM.md](/GCPVM.md) technical log for the steps on how to do so.

In this log:

- [x] Create free DNS entry pointing to temporary IP address (18/03/24 | 5 mins)
- [x] Using DNS entry for GCP VM (18/03/24 | 5 mins)
- [x] Testing the DNS entry connected to server in a web browser (18/03/24 | 5 mins)
- [x] References

Total Duration: 15 mins

---

## Create free DNS entry pointing to temporary IP address

Learn how to create free DNS entry pointing to temporary IP address to prevent having to copy and paste the external IP every single time

Assumption(s):
- You have already created a virtual machine on Google Cloud Platform

Duration: 5 mins

### Steps

1. Visit DuckDNS at https://www.duckdns.org/ 

2. At the top of the page, choose your desired sign in option. Sign in to create an account to store your domains.

> [!TIP]
> Sign in with the same Google Account you use for your VM on Google Cloud Platform to keep things simple.

![DuckDNS homepage](/images/DuckDNS/DuckDNSpage.png)

3. If this is your first time signing in, you may be asked to complete the reCAPTCHA. If so, click the ```>>> reCaptcha <<<``` button. 

![duckdns recaptcha](/images/DuckDNS/DuckDNSReCAPTCHA.png)

4. You will now see an updated page with **account, type, token, when the token was generated, and creation date and time**.

![after signing in](/images/DuckDNS/DuckDNSAfterSigningIn.png)

5. Below that information is where your domains are stored. 
    - You can have up to 5 domains.
    - If this is your first time signing in, there will be no domains.

![Empty Domain](/images/DuckDNS/DuckDNSEmptyDomain.png)

6. Enter a **domain** name.
    - Pick a name that is not already in use
    - Pick a name that is meaningful to you so you can remember it
    - The URL will be ```https://YOURDOMAIN.duckdns.org```

7. Click ```add domain```. You will now see your domain addd to the list.

![new domain](/images/DuckDNS/DuckDNSNewDomain.png)

:tada: *Congratulations! You have now completed the task of creating a DNS on DuckDNS!*

> [!CAUTION]
> Use DuckDNS at your own risk - sometimes it may not work
> It is free afterall!

---

## Using DNS entry for GCP VM

Learn how to use your DNS entry for your Virtual Machine on Google Cloud Platform

Assumption(s):
- You have already created a virtual machine on Google Cloud Platform
- You have already created a DNS domain on DuckDNS

Duration: 5 mins

### Steps

1. Visit DuckDNS at https://www.duckdns.org/ and sign in. Scroll down to view your domains. Set this window aside for now.

2. In another window, open your VM instances page through Google Cloud Platform. This can be accessed by going to https://console.cloud.google.com/, clicking on the ```hamburger button``` on the top-left corner of the page, hovering over ```Compute Engine``` and clicking ```VM Instances```.

3. If your VM is running, as indicated by the green dot under your VM's Status, skip this step. If your VM is not running yet, click the three dots on the righthand side of your VM and click ```Start/Resume```. Wait for the page to refresh. The status of your VM will change to a green dot to show it is running.

3. An External IP will also appear once the VM is running. Copy the **External IP** address for you VM Instance.

4. Head back to the DuckDNS site in the other window.

5. Paste the **External IP** from your VM to the **current ip** of your new domain. Click ```update ip```. 

6. You will get a success message at the top of the page saying that it has been added to your account. Now you can use this domain in the browser and on other applications instead of typing in the external IP every time, that changes quite often.

:tada: *Congratulations! You have now completed the task of using your DNS for your VM on GCP!*

> [!WARNING]
> If you are stopping here, remember to STOP the virtual machine or else it will continue to run and bill to your account.
> Visit the [GCPVM.md](/GCPVM.md) technical log to learn how to disconnect from the server.

---

## Testing the DNS entry connected to server in a web browser

Learn how to test the DNS entry that is connected to your GCP VM in a web browser

Assumption(s):
- You have already created and started running a virtual machine on Google Cloud Platform
- You have already created a DNS domain on DuckDNS that is connected to your GCP VM

Duration: 5 mins

### Steps

1. Open your VM instances page through Google Cloud Platform. This can be accessed by going to https://console.cloud.google.com/, clicking on the ```hamburger button``` on the top-left corner of the page, hovering over ```Compute Engine``` and clicking ```VM Instances```.

2. Copy your **External IP** from your VM.

3. In a new browser:
    - Paste your **External IP** in the address bar
    - Click ```Enter``` on your keyboard
    - This will open up your **Window Server Internet Information Services** page.

![testing external ip](/images/DuckDNS/DuckDNSTestingExtIP.png)

4. In a new tab:
    - Type in your **DuckDNS URL** in the address bar
    - Click ```Enter``` on your keyboard
    - This will ALSO open up your **Window Server Internet Information Services** page
    - This confirms the DNS is working

![testing domain](/images/DuckDNS/DuckDNSTestingDomain.png)

:tada: *Congratulations! You have now completed the task testing your newly created and connected DNS!*

> [!WARNING]
> If you are stopping here, remember to STOP the virtual machine or else it will continue to run and bill to your account.
> Visit the [GCPVM.md](/GCPVM.md) technical log to learn how to disconnect from the server.

---

## References

Morgan, S. [Shawn's Spotlight on GIS]. (2023, January 19). Geom99 - GCP Part 3: Using DuckDNS [Video]. YouTube. https://www.youtube.com/watch?v=8peq7B8SEYk 