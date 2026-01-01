<sub><sup>This is an extension of my previous articles on the two Server/Client connection methods for DGX Spark: [Day01A: Remote Access from Internet Guide](https://github.com/Sniper711/DGX-Spark-Day01A-Remote-Access-from-Internet-Guide-20251220A/blob/main/DGX%20Spark%20(Day01A)%20Remote%20Access%20from%20Internet%20Guide%2020251220A.md) and [Day01B: Local Access from Same Subnet Guide](https://github.com/Sniper711/DGX-Spark-Day01B-Local-Access-from-Same-Subnet-Guide-20251220B/blob/main/DGX%20Spark%20(Day01B)%EF%BC%9ALocal%20Access%20from%20Same%20Subnet%20Guide%2020251220B.md), and the article [Day02: Open WebUI with Ollama on Remote Spark](https://github.com/Sniper711/DGX-Spark-Day02-Open-WebUI-with-Ollama-on-Remote-Spark-20251226/blob/main/DGX%20Spark%20(Day02)%20Open%20WebUI%20with%20Ollama%20on%20Remote%20Spark%2020251226.md) Here, I'll expand Client support from Mac/PC to Android/iOS Tablets/Phones, to significantly boost your productivity. I hope this gives you more options for reference.</sup></sub>
![Support Tablets](https://github.com/user-attachments/assets/36acd4a2-437a-4daa-ac27-d382a700d2de)

# DGX Spark (Day03) Expand DGX Spark service for Tablets and Phones 20260101
## 🟩 English
> ## Scenarios & Advantages
> **Android/iOS Tablet Client browser uses the Open WebUI interface → through the self-established remote connections → to run Ollama on DGX Spark Server**
> - Expand Support for Android/iOS Tablet Clients (Beyond Just Mac/PC Clients)
>   - Run Ollama anytime, anywhere — significantly boost your productivity.
>   - Install and configure `WireGuard` and `Termius` APPs on your tablet.
> - **Based on the interconnection methods of DGX Spark: [Day01A: Remote Access from Internet Guide](https://github.com/Sniper711/DGX-Spark-Day01A-Remote-Access-from-Internet-Guide-20251220A/blob/main/DGX%20Spark%20(Day01A)%20Remote%20Access%20from%20Internet%20Guide%2020251220A.md) and [Day01B: Local Access from Same Subnet Guide](https://github.com/Sniper711/DGX-Spark-Day01B-Local-Access-from-Same-Subnet-Guide-20251220B/blob/main/DGX%20Spark%20(Day01B)%EF%BC%9ALocal%20Access%20from%20Same%20Subnet%20Guide%2020251220B.md), and the article [Day02: Open WebUI with Ollama on Remote Spark](https://github.com/Sniper711/DGX-Spark-Day02-Open-WebUI-with-Ollama-on-Remote-Spark-20251226/blob/main/DGX%20Spark%20(Day02)%20Open%20WebUI%20with%20Ollama%20on%20Remote%20Spark%2020251226.md)**. 
>   - Guaranteed stability through the self-estabilished remote connections
>   - No reliance on NVIDIA SYNC
> - After rebooting
>   - Simply have the Android/iOS Tablet Clients run `WireGuard` and `Termius`, then browse the `Ollama service URL` - it's super easy.

---

## Table of Contents

- [On Your Tablet: Installing and Setting Up WireGuard APP](#on-your-tablet-installing-and-setting-up-wireguard-app)
  - [Step 1. Download and Install WireGuard APP from the Store](#step-1-download-and-install-wireguard-app-from-the-store)
  - [Step 2. Configure WireGuard App](#step-2-configure-wireguard-app)
    - [Step 2A. If Your Mac/PC WireGuard client version supports exporting settings as a QR Code (the easiest method)](#step-2a-if-your-macpc-wireguard-client-version-supports-exporting-settings-as-a-qr-code-the-easiest-method)
    - [Step 2B. If your Mac/PC WireGuard client version does not support exporting settings as a QR code, enter the details manually](#step-2b-if-your-macpc-wireGuard-client-version-does-not-support-exporting-settings-as-a-qr-code-enter-the-details-manually)
  - [Step 3 Test the WireGuard Client Connection on Your Android/iOS Tablet](#step-3-test-the-wireguard-client-connection-on-your-androidios-tablet)

- [On Your Tablet: Installing and Setting Up the Termius App](#on-your-tablet-installing-and-setting-up-the-termius-app)
  - [Step 1. Download and Install the Termius App from the Store](#step-1-download-and-install-the-termius-app-from-the-store)
  - [Step 2. Configure the Host Feature in the Termius App](#step-2-configure-the-host-feature-in-the-termius-app)
  - [Step 3. Configure the Forwarding Feature in the Termius App](#step-3-configure-the-forwarding-feature-in-the-termius-app)

- [On Your Tablet: Launch WireGuard and Termius in Sequence, then browse Ollama Service URL](#on-your-tablet-launch-wireguard-and-termius-in-sequence-then-browse-the-ollama-service-url)
  - [Step 1. Launch WireGuard to Establish the VPN Tunnel](#step-1-launch-wireguard-to-establish-the-vpn-tunnel)
  - [Step 2. Launch Termius to Establish the SSH Host Connection and Activate the Ollama-Specific Port Forwarding Rule](#step-2-launch-termius-to-establish-the-ssh-host-connection-and-activate-the-ollama-specific-port-forwarding-rule)
  - [Step 3. Browse the Ollama Service URL http://localhost:12000](#step-3-browse-the-ollama-service-url-httplocalhost12000)

---

## On Your Tablet: Installing and Setting Up `WireGuard` APP

### Step 1. Download and Install `WireGuard` APP from the store
### Step 2. Configure `WireGuard` App
(There are two scenarios: Step 2A and Step 2B)
#### Step 2A. If your Mac/PC WireGuard client version supports exporting settings as a QR code (the easiest method):
- Step 2A-1. Open the `WireGuard` app on your Tablet.
- Step 2A-2 Tap the `+` icon in the bottom-left corner, then select `Scan QR Code`
- Step 2A-3. Scan the QR code displayed on your Mac/PC WireGuard client to complete the setup.
#### Step 2B. If your Mac/PC WireGuard client version does not support exporting settings as a QR code, enter the details manually:
- Step 2B-1. Open the `WireGuard` app on your tablet.
- Step 2B-2. Tap the `+` icon in the bottom-left corner, then select `Create from Scratch`
- Step 2B-3. In the Interface section, fill in the following:
  - Name:        **Enter the Server VPN name. My example is `DGXSparkVPN`**
  - Private Key: **Enter the Client PrivateKey from the (Day01A) article**
  - Public Key:  **Leave blank** — the Client PublicKey will be generated automatically
  - Addresses:   **Enter the `WireGuard Client fixed IP inside the VPN`, example from (Day01A) article is 10.0.0.2/32**
  - Listen Port: **Leave blank**
  - DNS Servers: **Enter the DNS servers from the (Day 01A) article which are 168.95.192.1, 8.8.8.8, or use the most common DNS servers in your country**
  - MTU:         **Leave blank**
  - Tap `Apply to all apps` to decide whether to route all apps through the WireGuard VPN or exclude specific ones
  - Finally, tap `Add Peer` (bottom center) to expand the Peer section and fill in the following:
    - Public Key:           **Enter the Server PublicKey from the (Day01A) article**
    - Pre-shared Key:       **Leave blank**
    - Persistent Keepalive: **Enter 25** — as in the (Day01A) article. This is the keepalive interval in seconds.
    - Endpoint:             **Enter <DGX_SPARK_PUBLIC_IP>:51820 from the (Day01A) article and replace <DGX_SPARK_PUBLIC_IP> with your server's public IP**
    - Allowed IPs:          **Enter 0.0.0.0/0 — routes all traffic through the VPN tunnel**
    - Finally, tap the `save icon (a disk logo)` in the top-right corner to save and complete the setup.
### Step 3. Test the WireGuard Client Connection on Your Android/iOS Tablet
(With the WireGuard Server on DGX Spark already running)
- Step 3-1. In the tablet's WireGuard app, find the connection you just created (named with the Server VPN name you just entered, `DGXSparkVPN` for example) and tap it to connect.
- Step 3-2. If the VPN connects successfully, the WireGuard app will start showing a connection timer, and a key icon will appear in the top-right corner of your tablet's status bar.   

---

## On Your Tablet: Installing and Setting Up the `Termius` App

### Step 1. Download and Install the `Termius` App from the Store
### Step 2. Configure the `Host` Feature in the `Termius` App
- Step 2-1. Open the `Termius` app. The `Hosts` menu should be selected on the left sidebar. In the center of the screen, you will see the text `"Create host. Save your connection details as hosts to connect in one click." and a field labeled _____ (Type IP address or hostname)`.
  - Enter the `<DGX_SPARK_PUBLIC_IP>` from the (Day01A) article (replace <DGX_SPARK_PUBLIC_IP> with your server's public IP).
- Step 2-2. The settings panel will now appear on the right. Enter the Host details step by step:
  - Alias: **Enter the Server Host name or nickname (my example: `DGX Spark Host`)**
  - Hostname or IP Address: **Enter the <DGX_SPARK_PUBLIC_IP> from the (Day01A) article** (replace <DGX_SPARK_PUBLIC_IP> with your server's public IP)
  - Group: **Leave blank**
  - Tags: **Leave blank**
  - Delete sends Ctrl-H: **Leave unchecked** (default setting)
  - SSH: **Leave checked** (default setting)
  - Mosh: **Leave unchecked** (default setting)
  - Port: **Leave as 22** (default setting)
  - Credentials:
    - Username: **Enter `<your DGX Spark login username>`**
    - Password: **Enter `<your DGX Spark login password>`**
    - Do not change any fields below this line
    - Finally, tap the checkmark icon `(✓)` in the top-right corner to Save.
- Step 2-3. Test the Hosts Feature in the `Termius` App:
  - Open the `Termius` app, tap `Hosts` in the left sidebar, then tap the newly created Host name (my example: `DGX Spark Host`). If successful, you should establish an SSH connection, and the word `Active` will appear in small text below the Host button.
### Step 3. Configure the `Forwarding` Feature in the `Termius` App
- Step 3-1. Open the `Termius` app. On the main screen, tap `Forwarding` in the left sidebar. The center of the screen will display the text "Set up port forwarding. Save port forwarding to access databases, web apps, and other services" along with a + button in the bottom-right corner. Now please **Tap the `+` button** to create a new port forwarding rule.
- Step 3-2. The settings panel will appear on the right. Enter the Forwarding details step by step:
  - First, tap `Continue`.
  - On the next page: `"Set the local port. This port will be open on the local (current) machine to forward traffic to the remote host. Port number: _____ and Bind address (optional): _____."`
    - Port number: Enter `12000`, as configured on the Client side in the (Day02) article.
    - Bind address (optional): **Leave blank**, then tap `Continue`
  - Next, tap `Select a host`. The panel will show the previously created Host name (my example: `DGX Spark Host`). Tap it.
  - On the next page: `"Set the destination, IP address/hostname and the port number of the remote host where the intermediate host will direct the traffic. Destination address: _____ and Destination port: _____."`
    - Destination address: Enter `0.0.0.0`, as configured in the (Day02) article.
    - Destination port: Enter `3000`, as configured on the Server side in the (Day02) article, then tap `Continue`
  - On the next page: `"Set the label. Label: _____."` 
    - Enter `Ollama 12000:3000` (recommended — this clearly indicates the service name and the ports on both ends, making it easy to identify when you add more services later, such as Jupyter, ComfyUI, etc.)
    - Tap `Done`.
  - Finally, tap the checkmark icon `(✓)` in the top-right corner to Save.
- Step 3-3. Test the Forwarding Feature in the Termius App:
  - Open the `Termius` app, tap `Forwarding` in the left sidebar, then tap the newly created Forwarding rule (gray button, my example: `Ollama 12000:3000`). If (and only if) the `button turns blue`, the test is successful.
    - Important! If the `button turns into a green checkmark`, it means the connection is still being attempted (neither success nor failure yet). Please wait a moment. **A green checkmark does not mean success** — it may be due to network latency. Wait or try tapping again until the button turns blue for confirmed success.

---

## On Your Tablet: Launch `WireGuard` and `Termius` in Sequence, then browse the `Ollama Service URL`

### Step 1. Launch `WireGuard` to Establish the VPN Tunnel
Open the `WireGuard` app and tap the Server VPN name button you created earlier (my example: `DGXSparkVPN`) to connect successfully. Note: If you tap it a second time, a timer showing the connection duration in seconds will appear on the right side of the screen.
### Step 2. Launch `Termius` to Establish the SSH Host Connection and Activate the Ollama-Specific Port Forwarding Rule
- Step 2-1. Open the `Termius` app, tap `Hosts` in the left sidebar, then tap the Host name you created (my example: `DGX Spark Host`).
If the SSH connection is successful, the word `Active` will appear in small text below the button.
- Step 2-2. Open the `Termius` app, tap `Forwarding` in the left sidebar, then tap the newly created Forwarding rule (gray button, my example: `Ollama 12000:3000`). If (and only if) the `button turns blue`, the test is successful.
  - Important! If the `button turns into a green checkmark`, it means the connection is still being attempted (neither success nor failure yet). Please wait a moment. **A green checkmark does not mean success** — it may be due to network latency. Wait or try tapping again until the button turns blue for confirmed success.
### Step 3. Browse the `Ollama Service URL http://localhost:12000`

---

# Congratulations - Now you can run Ollama via your tablet's browser, anytime and anywhere — powered by DGX Spark's GPU!
<sub><sup>* After rebooting. Simply have the Android/iOS Tablet Clients run `WireGuard` and `Termius`, then browse the `Ollama service URL` - it's super easy.</sup></sub>



