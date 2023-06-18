<!DOCTYPE html>
<html>
<head>
    <title>2023-06-09-Turning-Fedora-Silverblue-Into-A-Dev-Station</title>
    <link rel="stylesheet" href="../_static/style.css" type="text/css" media="screen, handheld" title="default">
    <link rel="shortcut icon" href="../_static/favicon.ico" type="image/vnd.microsoft.icon">
    <meta charset="UTF-8">
    <meta http-equiv="Content-Type" content="text/html; charset=UTF-8"> 
</head>
<body>

<header>

	<nav class="head-nav">
	<div class="left">
		<img src="../_static/toast.gif" <="" div="">
    </div>
    
    <div class="right">
		<!-- <span class="doNotDisplay">Socials:</span> -->
		  | <a href="https://github.com/manemobiili">Github </a>
		  | <a href="https://fosstodon.org/@mane">Mastodon </a>
		  | <a href="https://youtube.com/@manemobiili">YouTube </a>
		  |
		</div>
	</nav>
    <h1><a href="../index.html">manemobiili <span id="headerSubTitle">fail early, fail often, fail forward</span></a></h1>
</header>

<nav id="side-bar">
    <div>
		<ul><li><a href="../cheatsheets">› cheatsheets/</a></li><li><a href="../dotfiles">› dotfiles/</a></li><li><a href="../journal">» <i>journal</i>/</a><ul><ul><li><a href="2023-06-07-my-26-euro-mistake.md">› 2023-06-07-my-26-euro-mistake</a></li><li><a href="2023-06-09-Turning-Fedora-Silverblue-Into-A-Dev-Station.md"><b>» 2023-06-09-Turning-Fedora-Silverblue-Into-A-Dev-Station</b></a></li><li><a href="2023-06-10-openSUSE-aeon-first-impressions.md">› 2023-06-10-openSUSE-aeon-first-impressions</a></li><li><a href="2023-06-12-beautify-micro.md">› 2023-06-12-beautify-micro</a></li><li><a href="2023-06-15-avoid-snaps-for-joplin.md">› 2023-06-15-avoid-snaps-for-joplin</a></li></ul></ul></li><li><a href="../lists">› lists/</a></li></ul>
	</div>
</nav>

<article>
	<p>My XPS 13 running Debian+Gnome was constantly crashing, and as an aspiring livestreamer, I couldn&rsquo;t afford to have my device go down willy-nilly!
I was on the verge of installing Ubuntu because I enjoy using LXD, but I&rsquo;m glad I took a closer look at immutable Linux distributions.
At the time of writing, they are very much in fashion, although some have been around for multiple years now. Alpine Linux has been doing it for years.</p>

<p>I&rsquo;m a fan of ChromeOS and Android (LineageOS specifically). When I use a stable Linux distro, I can get almost all my programs from Flatpak and GitHub.
If Silverblue turns out to be similiar to Android, i&rsquo;m going to be running it happily for years to come.</p>

<p>I&rsquo;m not too keen on customization; most of my dotfiles fit in less than 100 lines.
And when it comes to updating the root image: I install them every once in a while instead of doing it repeatedly in a short span.
Good thing you can just skip a few releases and go straight into the newest one/S.
Frequent reboots are a turnoff, but at least system boots itself back up quickly.</p>

<p>My usual desktop consists of xmonad, but nowadays with wayland making progress i&rsquo;m running gnome-shell with material-shell extension.
I don&rsquo;t like Pop-shell one because i always use &lsquo;monocle&rsquo; layout aka. fullscreen layout. And less window borders the better. Sway is ok but i can&rsquo;t wrap my head around resizing it&rsquo;s windows.</p>

<p>Here are the first things i&rsquo;m installing first off in a fresh system</p>

<ul>
<li>tailscale</li>
<li>tmux</li>
<li>micro</li>
<li>joplin cli version</li>
<li>mc or lf</li>
<li>doas</li>
<li>zsh or oksh (but bash is fine too)</li>
<li>all i want from wm is max windows and alt-tab</li>
<li>firefox, librewolf, chromium, vivaldi</li>
<li>zfs</li>
</ul>

<p>silverblue can install some rpm packages as seperate modules, so i can still enjoy tailscale, tmux and zsh.</p>

<pre><code>$ rpm-ostree install blahblahblah
</code></pre>

<p>Also a wide variety of programming languages still work using tools to fetch latest lts releases of things.</p>

<ul>
<li>SDKMAN for kotlin and other jvm languages</li>
<li>nvm for Node (mostly for terminal version of joplin)</li>
<li>golang manually installed in ~/.local/go</li>
<li>crystal somewhere in $PATH eg. ~/.local/bin</li>
<li>RVM for ruby (i tried it and it&rsquo;s a little cumbersome)</li>
</ul>

<p>Virtual machines</p>

<ul>
<li>Boxes and/or Bottles for windows applications if using gnome</li>
<li>LXC/LXD - maybe throw in a BSD image somewhere</li>
<li>Podman is installed ootb should you use it</li>
</ul>

<p>Overall feeling pretty good about this hypervisor system :) It&rsquo;s read-only nature should keep it in check.</p>

</article>

<footer>
    <div class="right">
    	<a href="http://crew.0xffff.me">Powered by crew</a>
	</div>
</footer>


</body></html>
