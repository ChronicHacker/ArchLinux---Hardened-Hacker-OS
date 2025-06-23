<h2>🛡️ Phase 5: VPN, DNS & TOR Setup</h2>

<p>In this phase, we'll secure your internet traffic through a no-logs WireGuard VPN, encrypt your DNS using <code>dnscrypt-proxy</code>, and configure TOR with <code>proxychains</code> for anonymous routing.</p>

<h3>✅ Step 1: Install Necessary Packages</h3>
<pre><code>pacman -S wireguard-tools networkmanager-wireguard dnscrypt-proxy tor proxychains-ng</code></pre>

<p>This installs:</p>
<ul>
  <li><code>wireguard-tools</code> – WireGuard VPN CLI utilities</li>
  <li>NetworkManager integration for WireGuard</li>
  <li><code>dnscrypt-proxy</code> – encrypted DNS resolver</li>
  <li><code>tor</code> – Tor network daemon</li>
  <li><code>proxychains-ng</code> – route apps through TOR</li>
</ul>

<h3>🔒 Step 2: Enable & Configure WireGuard</h3>
<ol>
  <li>Create your WireGuard config (e.g. <code>/etc/wireguard/wg0.conf</code>) using credentials from your VPN provider.</li>
  <li>Import the config into NetworkManager via CLI:</li>
  <pre><code>nmcli connection import type wireguard file wg0.conf</code></pre>
  <li>Enable and start:</li>
  <pre><code>systemctl enable --now NetworkManager</code></pre>
</ol>

<p>This is a standardized method supported by Arch’s NetworkManager WireGuard docs :contentReference[oaicite:1]{index=1}.</p>

<h3>🌍 Step 3: Set Up dnscrypt-proxy</h3>
<ol>
  <li>Edit <code>/etc/dnscrypt-proxy/dnscrypt-proxy.toml</code> to uncomment or specify resolvers that support DNSSEC and no logs.</li>
  <li>Ensure it listens on localhost (default).</li>
  <li>Enable and start:</li>
  <pre><code>systemctl enable --now dnscrypt-proxy</code></pre>
</ol>

<p>Update <code>/etc/resolv.conf</code> to use the local resolver:</p>
<pre><code>nameserver 127.0.0.1
nameserver ::1
options edns0</code></pre>

<p>Verify it's working by running a DNS leak test—only encrypted DNS servers should appear :contentReference[oaicite:2]{index=2}.</p>

<h3>🧅 Step 4: Configure TOR + Proxychains</h3>
<ol>
  <li>Edit <code>/etc/proxychains.conf</code>:</li>
  <pre><code>[ProxyList]
socks5  127.0.0.1 9050</code></pre>
  <li>Enable Tor:</li>
  <pre><code>systemctl enable --now tor</code></pre>
  <li>Test with:</li>
  <pre><code>proxychains curl https://check.torproject.org/</code></pre>
</ol>

<p>✅ You should see confirmation you're using the Tor network.</p>

<h3>🌐 Step 5: Optional Automatic VPN on Network Connect</h3>
<p>To auto-connect VPN using NetworkManager:</p>
<pre><code>UUID=$(nmcli --get-values connection.uuid connection show wg0)
nmcli connection modify <your-wifi> connection.secondaries "$UUID"</code></pre>

<p>This ensures VPN connects whenever Wi-Fi is active.</p>

<p><strong>✅ Your VPN, encrypted DNS, and Tor routing are now set up and ready.</strong></p>
<p>➡️ Continue to <strong>Phase 6: Hacking Tools & System Hardening</strong> (`06_tools_and_hardening.md`).</p>
