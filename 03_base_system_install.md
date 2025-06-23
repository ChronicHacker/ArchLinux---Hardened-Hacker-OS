<h2>🛠️ Phase 3: Base System Installation</h2>

<p>Now that your partitions are mounted, it’s time to install the core Arch system and configure essential settings.</p>

<h3>Step 1: Install Base Packages</h3>
<p>Run the following command:</p>
<pre><code>pacstrap /mnt base base-devel linux linux-firmware vim networkmanager</code></pre>
<p>This installs:</p>
<ul>
  <li><code>base</code>: minimal Arch system</li>
  <li><code>base-devel</code>: tools like make, gcc, etc.</li>
  <li><code>linux</code> and <code>linux-firmware</code>: the kernel and drivers</li>
  <li><code>vim</code>: terminal text editor</li>
  <li><code>networkmanager</code>: tool to manage Wi-Fi/Ethernet connections</li>
</ul>

<h3>Step 2: Generate fstab</h3>
<p>This file tells the system how to mount partitions:</p>
<pre><code>genfstab -U /mnt >> /mnt/etc/fstab</code></pre>
<p>Confirm it was generated properly:</p>
<pre><code>cat /mnt/etc/fstab</code></pre>

<h3>Step 3: chroot into Your New System</h3>
<p>Enter your newly installed Arch system:</p>
<pre><code>arch-chroot /mnt</code></pre>

<h3>Step 4: Set the Timezone</h3>
<p>Example: Pacific time zone (Los Angeles):</p>
<pre><code>ln -sf /usr/share/zoneinfo/America/Los_Angeles /etc/localtime</code></pre>

<p>Then generate hardware clock:</p>
<pre><code>hwclock --systohc</code></pre>

<h3>Step 5: Configure Locale</h3>
<p>Uncomment <code>en_US.UTF-8 UTF-8</code> in <code>/etc/locale.gen</code>:</p>
<pre><code>sed -i 's/#en_US.UTF-8 UTF-8/en_US.UTF-8 UTF-8/' /etc/locale.gen</code></pre>

<p>Then generate locales:</p>
<pre><code>locale-gen</code></pre>

<p>Create <code>/etc/locale.conf</code>:</p>
<pre><code>echo "LANG=en_US.UTF-8" > /etc/locale.conf</code></pre>

<h3>Step 6: Set Console Keymap (Optional)</h3>
<p>If you're not using a US keyboard layout, specify it here:</p>
<pre><code>echo "KEYMAP=de-latin1" > /etc/vconsole.conf</code></pre>

<h3>Step 7: Set Hostname</h3>
<p>Pick a name for your machine:</p>
<pre><code>echo hacker-os > /etc/hostname</code></pre>

<p>Now edit <code>/etc/hosts</code>:</p>
<pre><code>cat <<EOF > /etc/hosts
127.0.0.1   localhost
::1         localhost
127.0.1.1   hacker-os.localdomain hacker-os
EOF</code></pre>

<h3>Step 8: Set the Root Password</h3>
<pre><code>passwd</code></pre>
<p>Enter your root password twice.</p>

<h3>Step 9: Enable Networking</h3>
<p>Enable NetworkManager so you’ll have internet after reboot:</p>
<pre><code>systemctl enable NetworkManager</code></pre>

<p><strong>✅ You now have a working Arch base system.</strong></p>
<p>➡️ Continue to <strong>Phase 4: KDE and GUI Setup</strong>.</p>
