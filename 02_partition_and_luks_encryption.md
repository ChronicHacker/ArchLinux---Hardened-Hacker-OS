<h2>🧱 Phase 2: Disk Partitioning + LUKS Encryption</h2>

<p><strong>⚠️ WARNING:</strong> This will permanently erase everything on your target drive. Double-check you're selecting the correct disk. Example: <code>/dev/nvme0n1</code> or <code>/dev/sda</code></p>

<h3>Step 1: Identify the Correct Disk</h3>
<pre><code>lsblk</code></pre>
<p>Look for your internal drive (not the USB). Make note of its name.</p>

<h3>Step 2: Start Partitioning with cgdisk</h3>
<pre><code>cgdisk /dev/nvme0n1</code></pre>
<p>Delete all existing partitions, then create:</p>
<ul>
  <li><strong>EFI System Partition:</strong> 512MB, type: <code>ef00</code>, name: <code>EFI</code></li>
  <li><strong>Main Partition:</strong> Use remaining space, type: <code>8300</code>, name: <code>cryptroot</code></li>
</ul>
<p>Write and confirm the partition table, then quit <code>cgdisk</code>.</p>

<h3>Step 3: Encrypt the Main Partition with LUKS</h3>
<pre><code>cryptsetup luksFormat /dev/nvme0n1p2</code></pre>
<p>Type <code>YES</code> in all caps and choose a strong passphrase.</p>

<h3>Step 4: Unlock the Encrypted Volume</h3>
<pre><code>cryptsetup open /dev/nvme0n1p2 cryptroot</code></pre>

<h3>Step 5: Set Up LVM Inside Encrypted Volume</h3>
<pre><code>pvcreate /dev/mapper/cryptroot
vgcreate vg0 /dev/mapper/cryptroot
lvcreate -L 20G vg0 -n root
lvcreate -l 100%FREE vg0 -n home</code></pre>

<h3>Step 6: Format the Partitions</h3>
<pre><code>mkfs.fat -F32 /dev/nvme0n1p1
mkfs.ext4 /dev/vg0/root
mkfs.ext4 /dev/vg0/home</code></pre>

<h3>Step 7: Mount Everything</h3>
<pre><code>mount /dev/vg0/root /mnt
mkdir /mnt/home
mount /dev/vg0/home /mnt/home
mkdir -p /mnt/boot/efi
mount /dev/nvme0n1p1 /mnt/boot/efi</code></pre>

<p><strong>✅ Disk is now partitioned, encrypted, and mounted.</strong></p>
<p>➡️ Continue to <strong>Phase 3: Base System Installation</strong>.</p>
