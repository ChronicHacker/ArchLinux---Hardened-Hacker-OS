<h2>🎯 Phase 7: Final Setup & Reboot</h2>

<p>You’re almost there! This final phase wraps up the setup, creates a regular user, enables services, and ensures your system is ready to go.</p>

<h3>1. Create a Standard User Account</h3>
<pre><code>useradd -m -G wheel -s /bin/bash yourusername</code></pre>
<p>Replace <code>yourusername</code> with your desired name.  
Then set their password:</p>
<pre><code>passwd yourusername</code></pre>

<h3>2. Grant Sudo Privileges</h3>
<pre><code>EDITOR=vim visudo</code></pre>
<p>Find the line:</p>
<pre><code># %wheel ALL=(ALL) ALL</code></pre>
<p>Uncomment it to:</p>
<pre><code>%wheel ALL=(ALL) ALL</code></pre>

---

<h3>3. Enable Essential Services</h3>
<pre><code>systemctl enable sshd
systemctl enable ufw
systemctl enable dnscrypt-proxy</code></pre>
<p>These ensure SSH, firewall, and encrypted DNS start on boot.</p>

---

<h3>4. Final System Cleanup</h3>
<pre><code>umount -R /mnt
cryptsetup close cryptroot</code></pre>
<p>This cleans up mounts and locks your encrypted volume.</p>

---

<h3>5. Reboot into Your New Hacker OS</h3>
<p>Remove the USB and reboot:</p>
<pre><code>reboot</code></pre>

<p>Boot into your new, hardened system. Log in as your regular user and test:</p>
<ul>
  <li>Run <code>sudo pacman -Syu</code> to test sudo access.</li>
  <li>Check firewall status: <code>ufw status</code>.</li>
  <li>Ensure VPN and services are running: <code>systemctl status wg-quick@wg0 dnscrypt-proxy sshd</code>.</li>
</ul>

<p><strong>🎉 Congratulations! You've built a secure, encrypted, hacker-ready system from scratch.</strong></p>
<p>Feel free to tweak configurations, install additional tools, and share improvements.</p>
