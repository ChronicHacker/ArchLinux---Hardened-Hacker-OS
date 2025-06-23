<h2>🔧 Phase 6: Hacking Tools & System Hardening</h2>

<p>Let’s install essential pentesting tools, lock down your system with firewall and kernel protections, and harden Firefox with Arkenfox.</p>

<h3>1. Install Pentesting Tools</h3>
<pre><code>pacman -Sy --noconfirm nmap netdiscover airgeddon bettercap wireshark-qt proxychains-ng ufw rkhunter</code></pre>
<p>This adds:</p>
<ul>
  <li><code>nmap</code>, <code>netdiscover</code>, <code>airgeddon</code>, <code>bettercap</code>, <code>wireshark-qt</code>: classic pentesting tools</li>
  <li><code>proxychains-ng</code>: for TOR routing</li>
  <li><code>ufw</code>: a simple firewall interface</li>
  <li><code>rkhunter</code>: rootkit/malware detection</li>
</ul>

<h3>2. Configure Firewall (UFW)</h3>
<pre><code>ufw default deny incoming
ufw default allow outgoing
ufw enable</code></pre>
<p>This blocks all unsolicited inbound traffic while allowing outgoing connections—a setup recommended by Arch and general usage guides.</p>

<pre><code>ufw status verbose</code></pre>
<small>Confirm it’s running and enforcing rules.</small>

<h3>3. Apply Kernel Hardening via Sysctl</h3>
<p>Create a file:</p>
<pre><code>/etc/sysctl.d/99-hardening.conf</code></pre>
<p>Add these secure settings:</p>
<pre><code>net.ipv4.ip_forward = 0
net.ipv4.conf.all.rp_filter = 1
net.ipv4.conf.default.secure_redirects = 0
net.ipv4.icmp_echo_ignore_broadcasts = 1
vm.swappiness = 10</code></pre>
<p>Then apply them:</p>
<pre><code>sysctl --system</code></pre>
<p>These settings improve network hygiene and resource use.</p>

<h3>4. Harden Firefox with Arkenfox</h3>
<ol>
  <li>Install Firefox if not already:</li>
    <pre><code>pacman -S firefox</code></pre>
  <li>Download the latest <code>user.js</code> from <a href="https://github.com/arkenfox/user.js" target="_blank">arkenfox</a>.</li>
  <li>Locate your profile folder via Firefox’s `about:support` (or `firefox -P`).</li>
  <li>Place <code>user.js</code> into that profile directory.</li>
  <li>Optionally add a <code>user-overrides.js</code> for custom tweaks.</li>
</ol>
<p>Arkenfox is a robust privacy-enhancing config—just make sure you read the docs and set overrides.</p>

<h3>5. Check for Rootkits (rkhunter)</h3>
<pre><code>rkhunter --update
rkhunter --checkall</code></pre>
<p>Review the output in <code>/var/log/rkhunter.log</code> and address any flagged items.</p>

<p><strong>✅ Tools installed, firewall active, kernel locked down, and browser hardened.</strong></p>
<p>➡️ Continue to <strong>Phase 7: Final Setup & Reboot</strong> (`07_final_setup.md`).</p>
