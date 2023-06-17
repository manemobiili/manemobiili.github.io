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
		<ul><li><a href="../pics">› pics/</a></li><li><a href="../posts">» <i>posts</i>/</a><ul><ul><li><a href="2023-02-08-gentoo-cheat-sheet-txt.md">› 2023-02-08-gentoo-cheat-sheet-txt</a></li><li><a href="2023-04-21-zero-punctuation-top-5-videos.md">› 2023-04-21-zero-punctuation-top-5-videos</a></li><li><a href="2023-06-07-my-26-euro-mistake.md">› 2023-06-07-my-26-euro-mistake</a></li><li><a href="2023-06-09-Turning-Fedora-Silverblue-Into-A-Dev-Station.md"><b>» 2023-06-09-Turning-Fedora-Silverblue-Into-A-Dev-Station</b></a></li><li><a href="2023-06-10-openSUSE-aeon-first-impressions.md">› 2023-06-10-openSUSE-aeon-first-impressions</a></li><li><a href="2023-06-12-beautify-micro.md">› 2023-06-12-beautify-micro</a></li><li><a href="2023-06-15-avoid-snaps-for-joplin.md">› 2023-06-15-avoid-snaps-for-joplin</a></li></ul></ul></li></ul>
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

<p>Here are the first things i&rsquo;m installing first off in a fresh system (maybe i should make a script for this)
- tailscale
- tmux
- micro
- doas
- zsh or oksh
- some sort of tiling wm (pardon me: i&rsquo;m allergic to mice)
&ndash; all i want from wm is max windows and alt-tab
- joplin cli version
- librewolf (alternatively chromium, vivaldi)
- zfs
- mc or lf</p>

<p>silverblue can install some rpm packages as seperate modules, so i can still enjoy tailscale, tmux and zsh.</p>

<pre><code>$ rpm-ostree install blahblahblah
</code></pre>

<p>Also a wide variety of programming languages still work using tools to fetch latest lts releases of things.
- SDKMAN for kotlin and other jvm languages
- nvm for Node (mostly for terminal version of joplin)
- golang manually installed in ~/.local/go
- crystal somewhere in $PATH eg. ~/.local/bin
- RVM for ruby (i haven&rsquo;t tested it yet)</p>

<p>Virtual machines
- Boxes and/or Bottles for windows applications if using gnome
- LXC/LXD - maybe throw in a BSD image somewhere
- Podman is installed ootb should you use it</p>

<p>Overall feeling pretty good about this &ldquo;hypervisor&rdquo; system :) It&rsquo;s read-only nature should keep it in check.</p>

</article>

<footer>
<br class="doNotDisplay doNotPrint" />
<div style="margin-right: auto;"><a href="http://crew.0xffff.me">Powered by crew</a></div>
</footer>
</body></html>
