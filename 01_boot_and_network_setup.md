<h2>🚀 Phase 1: Boot & Network Setup</h2>

<h3>Step 1: Boot from USB</h3>
<ol>
  <li>Insert your Arch USB stick into the target machine.</li>
  <li>Reboot and access BIOS/UEFI.</li>
  <li>Select the USB as your boot device.</li>
  <li>Choose: <strong>Arch Linux install medium (x86_64, UEFI)</strong></li>
</ol>

<h3>Step 2: Set Keyboard Layout (Optional)</h3>
<p>If you’re using a non-US keyboard layout, set it now. For example, to use German layout:</p>
<pre><code>loadkeys de-latin1</code></pre>
<p>Otherwise, skip this step (US is default).</p>

<h3>Step 3: Verify UEFI Mode</h3>
<p>Type the following:</p>
<pre><code>ls /sys/firmware/efi/efivars</code></pre>
<p>If you see output, you're in UEFI mode. If the directory doesn't exist, you are in BIOS mode and should reboot and change boot options.</p>

<h3>Step 4: Connect to Wi-Fi</h3>
<p>Launch the Wi-Fi tool:</p>
<pre><code>iwctl</code></pre>
<p>Then enter:</p>
<pre><code>station wlan0 scan
station wlan0 get-networks
station wlan0 connect Your_WiFi_Name
exit</code></pre>
<p>Replace <code>Your_WiFi_Name</code> with the SSID of your wireless network. You'll be prompted for the password.</p>

<h3>Step 5: Set System Time</h3>
<pre><code>timedatectl set-ntp true</code></pre>
<p>This ensures your system clock is accurate — essential for security and encryption.</p>

<p><strong>✅ You're now connected and ready to partition your disk.</strong></p>
<p>➡️ Continue to <strong>Phase 2: Disk Partitioning + LUKS Encryption</strong></p>
