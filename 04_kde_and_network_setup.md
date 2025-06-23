<h2>🌐 Phase 4: KDE Plasma & Network Management</h2>

<p>You now have a working Arch base. In this phase, we'll install KDE Plasma desktop with a display manager and enable NetworkManager for network management.</p>

<h3>Step 1: Install Xorg, KDE & SDDM</h3>
<pre><code>pacman -S xorg plasma plasma-wayland-session sddm</code></pre>
<p>This includes:</p>
<ul>
  <li><code>xorg</code>: X‑window system</li>
  <li><code>plasma</code>: KDE Plasma desktop</li>
  <li><code>plasma-wayland-session</code>: Wayland support for KDE</li>
  <li><code>sddm</code>: Recommended display manager for KDE</li>
</ul>
<p>Citation: KDE installation on Arch Wiki :contentReference[oaicite:1]{index=1}.</p>

<h3>Step 2: Enable SDDM</h3>
<pre><code>systemctl enable sddm.service</code></pre>
<p>SDDM will launch a graphical login on startup.</p>

<h3>Step 3: Install & Enable NetworkManager</h3>
<pre><code>pacman -S networkmanager plasma-nm</code></pre>
<p>This installs:</p>
<ul>
  <li><code>networkmanager</code>: Core networking service</li>
  <li><code>plasma-nm</code>: KDE NetworkManager applet</li>
</ul>
<p>Citation: NetworkManager installation via Arch Wiki :contentReference[oaicite:2]{index=2}.</p>

<pre><code>systemctl enable NetworkManager.service</code></pre>

<h3>Step 4: Reboot Into KDE</h3>
<pre><code>exit      # leave chroot
reboot</code></pre>
<p>Remove the USB and your machine will boot into the KDE login screen. Use your root or user credentials to log in.</p>

<h3>Post-Login: Configure Network via GUI</h3>
<ul>
  <li>Click the network applet in the KDE tray</li>
  <li>Select your Wi‑Fi network or wired connection</li>
  <li>Connect (you may be prompted for password)</li>
</ul>
<p>If the applet doesn’t show networks, make sure NetworkManager is running:  
<code>systemctl status NetworkManager</code></p>
<p>Advice from users: run <code>systemctl enable --now NetworkManager</code> if it's inactive :contentReference[oaicite:3]{index=3}.</p>

<p><strong>✅ KDE is now installed and networking is configured.</strong></p>
<p>➡️ Proceed to <strong>Phase 5: VPN, DNS & TOR Setup</strong> (`05_vpn_dns_tor.md`).</p>
