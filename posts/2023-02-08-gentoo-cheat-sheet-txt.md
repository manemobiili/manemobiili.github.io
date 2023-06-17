<!DOCTYPE html>
<html>
<head>
    <title>2023-02-08-gentoo-cheat-sheet-txt</title>
    <link rel="stylesheet" href="../_static/style.css" type="text/css" media="screen, handheld" title="default">
    <link rel="shortcut icon" href="../_static/favicon.ico" type="image/vnd.microsoft.icon">
    <meta charset="UTF-8">
    <meta http-equiv="Content-Type" content="text/html; charset=UTF-8"> 
</head>
<body>

<header>
    <nav class="head-nav">
		<div class="left">
			<a href="http://quotes.cat-v.org">quotes</a> |
			<a href="http://doc.cat-v.org">docs</a> |
			<a href="http://repo.cat-v.org">repo</a> |
			<a href="http://go-lang.cat-v.org">golang</a> |
			<a href="http://sam.cat-v.org">sam</a> |
			<a href="http://man.cat-v.org">man</a> |
			<a href="http://acme.cat-v.org">acme</a> |
			<a href="http://glenda.cat-v.org">Glenda</a> |
			<a href="http://ninetimes.cat-v.org">9times</a> |
			<a href="http://harmful.cat-v.org">harmful</a> |
			<a href="http://9p.cat-v.org/">9P</a> |
			<a href="http://cat-v.org">cat-v.org</a>
		</div>

		<div class="right">
		  <span class="doNotDisplay">Related sites:</span>
		  | <a href="../sitemap">site map</a>
		</div>
    </nav>
    <h1><a href="../index.html">crew <span id="headerSubTitle">Bringing more minimalism and sanity to the web, in a suckless way</span></a></h1>
</header>

<nav id="side-bar">
    <div>
		<ul><li><a href="../pics">› pics/</a></li><li><a href="../posts">» <i>posts</i>/</a><ul><ul><li><a href="2023-02-08-gentoo-cheat-sheet-txt.md"><b>» 2023-02-08-gentoo-cheat-sheet-txt</b></a></li><li><a href="2023-04-21-zero-punctuation-top-5-videos.md">› 2023-04-21-zero-punctuation-top-5-videos</a></li><li><a href="2023-06-07-my-26-euro-mistake.md">› 2023-06-07-my-26-euro-mistake</a></li><li><a href="2023-06-09-Turning-Fedora-Silverblue-Into-A-Dev-Station.md">› 2023-06-09-Turning-Fedora-Silverblue-Into-A-Dev-Station</a></li><li><a href="2023-06-10-openSUSE-aeon-first-impressions.md">› 2023-06-10-openSUSE-aeon-first-impressions</a></li><li><a href="2023-06-12-beautify-micro.md">› 2023-06-12-beautify-micro</a></li><li><a href="2023-06-15-avoid-snaps-for-joplin.md">› 2023-06-15-avoid-snaps-for-joplin</a></li></ul></ul></li></ul>
	</div>
</nav>

<article>
	<p>Plain text version of <a href="https://wiki.gentoo.org/wiki/Gentoo_Cheat_Sheet">https://wiki.gentoo.org/wiki/Gentoo_Cheat_Sheet</a>
Handy reference for working inside the terminal. Get the markdown file <a href="https://manemobiili.github.io/assets/portage.md">here</a>.</p>

<pre><code># Sync methods
emaint -a sync				// Sync all repositories that are set to auto-sync including the Gentoo ebuild repository
emerge-webrsync				// Sync the Gentoo ebuild repository using the mirrors by obtaining a snapshot that is (at most) a day old
eix-sync				// emerge --sync now runs the emaint sync module with the --auto option
qlist -IRv				// List installed packages with version number and name of overlay used
eix --world | less			// To view the list of packages in the world set, along with their available versions, it is possible to use
eix --color -c --world | less -R	// To keep color in the output, use the --color switch

# Package installation (man emerge)
emerge -pv www-client/firefox		// List what packages would be installed, without installing them
emerge -av www-client/firefox		// List what packages would be installed, ask for confirmation before installing them
emerge -a =www-client/firefox-96.0.1	// Install a specific version of a package temporarily, to make it persistent, add &quot;&lt;www-client/firefox-96.0.1&quot; to /etc/portage/package.mask
emerge -a1 www-client/firefox		// Install a package without adding it to the world file (--oneshot, -1)

# Package removal
emerge -W www-client/firefox		// Remove atoms and/or sets from the world file (--deselect [ y | n ], -W)
emerge -pc				// Review to make sure no required packages would be removed
emerge -n www-client/firefox        	// ^Don't remove these dependensies (--noreplace) by adding them into world file
emerge -ac				// ^Once it has been assured that emerge -c will only remove unneeded packages, remove packages
emerge -avc www-client/firefox		// To directly remove a package that no other packages depend on. (--depclean, -c) wont remove packages unless everything has been resolved. Sometimes it's necessary to update first (as below)

# Package upgrade
emerge -avuND @world			// Upgrade all packages in the world and their dependencies (--deep, -D)
emerge -avuUD @world			// ^Use (--changed-use, -U) in place of (--newuse, -N) to avoid rebuilds
emerge -aquUD @world			// ^Use the (--quiet, -q) flag for more succinct execution

# Package troubleshooting
revdep-rebuild -v			// Check for and rebuild missing libraries (not normally needed)
equery b `which vim`			// Tell which installed package provides a command using equery (app-portage/gentoolkit)
e-file vim				// Tell which (not) installed package provides a command using efile (app-portage/pfl)
equery d www-client/firefox		// Tell which packages depend on a specific package using equery
eix www-client/firefox			// Get information about a package using eix
emerge @module-rebuild			// After installing a new kernel
emerge @golang-rebuild			// After installing new version of go
emerge @preserved-rebuild		// For using newer libraries

# Portage enhancements
dispatch-conf				// Manage configuration changes after an emerge completes

# After installations or updates
perl-cleaner --all			// Or if previous didn't help
perl-cleaner --reallyall -- -av
haskell-updater				// For haskell packages

# USE flags (man euse)
euse -i X				// Obtain descriptions and usage of the USE flag X using euse
equery hasuse mysql			// Show what packages have the mysql USE flag
eix --installed-with-use mysql		// Show what packages are currently built with the mysql USE flag
equery uses &lt;package-name&gt;		// Show what USE flags are available for a specific package

# Log management (man genlop)
emerge -a app-portage/genlop		// Install app-portage/genlop by issuing
genlop -l | tail -n 10			// View the last 10 emerges (installs)
genlop -t libreoffice			// View how long emerging LibreOffice took
emerge -pU @world | genlop --pretend	// Estimate how long emerge -uND --with-bdeps=y @world will take
watch genlop -unc			// Watch the latest merging ebuild during system upgrades

# Overlays
eselect repository list			// List all existing overlays (app-eselect/eselect-repository)
eselect repository list -i		// List all installed overlays

# OpenRC services
rc-update add sshd default		// Start the ssh daemon in the default runlevel at boot
rc-service sshd start			// Start the sshd service now
rc-service sshd status			// Check if the sshd service is running
rc-service sshd restart			// Restart the sshd service
rc-service sshd stop			// Stop the sshd service
rc-status --all				// List services, their status, and the runlevels they belong to
rc-update show				// Show enabled services and the runlevels they belong to

# Systemd services
systemctl enable sshd			// Start the ssh daemon at boot
systemctl start sshd			// Start the sshd service now
systemctl status sshd			// Check if the sshd service is running

# Tips
emerge -s &quot;%^python$			// To search packages in Portage by regular expressions
emerge --regen				// Generate local metadata cache after syncing overlays
qcheck vim-core				// Use qcheck to verify installed packages (app-portage/portage-utils)
</code></pre>

</article>

<footer>
<br class="doNotDisplay doNotPrint" />
<div style="margin-right: auto;"><a href="http://crew.0xffff.me">Powered by crew</a></div>
</footer>
</body></html>
