<h1>🛠️ Phase 0: Preparing Your Tools</h1>

<p>Before starting the installation, make sure you have the right tools and system ready.</p>

<hr>

<h2>✅ What You Need</h2>
<ul>
  <li>A UEFI-based laptop or desktop (64-bit CPU)</li>
  <li>A blank USB drive (8GB or larger)</li>
  <li>Internet connection (Wi-Fi or Ethernet)</li>
  <li>A second device to view this guide (optional but helpful)</li>
  <li>VPN login credentials (choose a <strong>no-logs provider</strong> like Mullvad or ProtonVPN)</li>
</ul>

<hr>

<h2>📥 Step 1: Download the Arch Linux ISO</h2>
<p>On any working computer, visit:</p>
<pre><code>https://archlinux.org/download/</code></pre>
<p>Choose a mirror near your location and download the latest <code>.iso</code> file (e.g., <code>archlinux-x86_64.iso</code>).</p>

<hr>

<h2>💾 Step 2: Flash the ISO to USB</h2>
<p>Use one of the following tools:</p>
<ul>
  <li><a href="https://www.balena.io/etcher/">Balena Etcher</a> (Windows/macOS/Linux)</li>
  <li>Rufus (Windows)</li>
  <li>Ventoy (Advanced users)</li>
</ul>

<h3>Steps:</h3>
<ol>
  <li>Open the flashing tool.</li>
  <li>Select the ISO file you downloaded.</li>
  <li>Select your USB drive as the target.</li>
  <li>Click <strong>Flash</strong> or <strong>Start</strong>.</li>
  <li>Once it finishes, safely eject the USB.</li>
</ol>

<hr>

<h2>⚙️ Step 3: Prepare Your Target Machine</h2>
<ol>
  <li>Insert the USB into the machine where you'll install Arch.</li>
  <li>Power it on and access your BIOS/UEFI (usually by pressing <code>DEL</code>, <code>F2</code>, or <code>ESC</code>).</li>
  <li>Disable <strong>Secure Boot</strong>.</li>
  <li>Set the USB as the primary boot device.</li>
  <li>Save and reboot.</li>
</ol>

<hr>

<p><strong>✅ You’re now ready to install Arch Linux.</strong></p>
<p>➡️ Proceed to <strong>Phase 1: Boot & Network Setup</strong></p>
