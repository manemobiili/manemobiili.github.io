<!DOCTYPE html>
<html>
<head>
    <title>2023-06-12-beautify-micro</title>
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
		<ul><li><a href="../cheatsheets">› cheatsheets/</a></li><li><a href="../dotfiles">› dotfiles/</a></li><li><a href="../journal">» <i>journal</i>/</a><ul><ul><li><a href="2023-06-07-my-26-euro-mistake.md">› 2023-06-07-my-26-euro-mistake</a></li><li><a href="2023-06-09-Turning-Fedora-Silverblue-Into-A-Dev-Station.md">› 2023-06-09-Turning-Fedora-Silverblue-Into-A-Dev-Station</a></li><li><a href="2023-06-10-openSUSE-aeon-first-impressions.md">› 2023-06-10-openSUSE-aeon-first-impressions</a></li><li><a href="2023-06-12-beautify-micro.md"><b>» 2023-06-12-beautify-micro</b></a></li><li><a href="2023-06-15-avoid-snaps-for-joplin.md">› 2023-06-15-avoid-snaps-for-joplin</a></li></ul></ul></li><li><a href="../lists">› lists/</a></li></ul>
	</div>
</nav>

<article>
	<p>I prefer command-line editors over full-blown IDEs. For my upcoming Kotlin projects, I decided to try out IntelliJ IDEA and VSCode (in the form of VSCodium and <a href="https://vscode.dev">https://vscode.dev</a>). Although I was pleasantly surprised by IntelliJ IDEA’s distraction-free mode. I still prefer command-line editors. To my knowledge: people who use command-line editors aren&rsquo;t fond of debugging tools, and that&rsquo;s where IDE&rsquo;s have the edge. I should look more into utilizing debug tools later.</p>

<p>The most important thing for me are keyboard shortcuts because I’m too lazy to keep clicking and dragging buttons around. Although I still use vi(m) sometimes, I think modal editing is a bit overrated. However, it doesn’t stop me from using other software with vim keys; Firefox+viumium and lf come to mind.</p>

<p>There are plenty of CLI editors out in the wild; most of them are way older than micro so UTF-8 isn’t a promise. I suggest trying out elvis, mcedit, mg, nano, and vile.</p>

<p>My favorite things about micro are its super small size of the editor, working clipboard, mostly sensible keybindings, and excellent language support. I might expand the list in the future if there are other hurdles in my way.</p>

<h2>Get alt, ctrl &amp; shift keys working correctly within tmux</h2>

<p>I love tmux to bits, but if you open micro inside tmux, modifier keys aren&rsquo;t working properly. Instead of highlighting the text it print&rsquo;s out [1;2D] [1;2C]&hellip; and a bunch of other junk we wouldn&rsquo;t want in our text.</p>

<p>Stackoverflow to the rescue! Author of micro found a fix for that by inserting the following into ~/.config/micro/bindings.json</p>

<pre><code>&quot;\u001b[1;2A&quot;: &quot;SelectUp&quot;,
&quot;\u001b[1;2B&quot;: &quot;SelectDown&quot;,
&quot;\u001b[1;2C&quot;: &quot;SelectRight&quot;,
&quot;\u001b[1;2D&quot;: &quot;SelectLeft&quot;,
&quot;\u001b[1;3D&quot;: &quot;WordLeft&quot;,
&quot;\u001b[1;3C&quot;: &quot;WordRight&quot;,
&quot;\u001b[1;3A&quot;: &quot;MoveLinesUp&quot;,
&quot;\u001b[1;3B&quot;: &quot;MoveLinesDown&quot;,
&quot;\u001b[1;4C&quot;: &quot;SelectWordRight&quot;,
&quot;\u001b[1;4D&quot;: &quot;SelectWordLeft&quot;,
&quot;\u001b[1;5D&quot;: &quot;StartOfLine&quot;,
&quot;\u001b[1;5C&quot;: &quot;EndOfLine&quot;,
&quot;\u001b[1;6D&quot;: &quot;SelectToStartOfLine&quot;,
&quot;\u001b[1;6C&quot;: &quot;SelectToEndOfLine&quot;,
&quot;\u001b[1;5A&quot;: &quot;CursorStart&quot;,
&quot;\u001b[1;5B&quot;: &quot;CursorEnd&quot;,
&quot;\u001b[1;6A&quot;: &quot;SelectToStart&quot;,
&quot;\u001b[1;6B&quot;: &quot;SelectToEnd&quot;
</code></pre>

<p>I&rsquo;m leaving link&rsquo;s to stackoverflow thread in the end.</p>

<h2>Bind Ctrl-R and Alt-R to replaceall and replace commands</h2>

<p>To bind Ctrl-R and Alt-R to replaceall and replace commands, you can add the following lines to your ~/.config/micro/bindings.json file:</p>

<pre><code>&quot;Alt-r&quot;: &quot;replace&quot;,
&quot;Ctrl-r&quot;: &quot;replaceall&quot;
</code></pre>

<p>By default Ctrl-R toggles the “ruler” command, which shows the line numbers. As of 2023 default keys don’t have a keybinding for replacing text. Luckily everything can be done using Ctrl-E and writing the command’s there. Commands are saved to <i>~/.config/micro/settings.json </i>file.</p>

<h2>Set a custom colorscheme</h2>

<p>I emphatise cleanliness in my setup, everything out of my way. I want the default background for all of my programs, which is assigned by the terminal emulator. AFAIK there is no &ldquo;terminal&rdquo; variable as there is in tmux (Ctrl-b :)</p>

<p>set -g status-style bg=terminal</p>

<p>But micro has a variety of themes to use, i chose dukeubuntu-tc, maybe because orange is my favorite colour. You copy a theme file from here:</p>

<p><a href="https://github.com/zyedidia/micro/tree/0859f4aa36d69e5cdb92b868dfc08498fd8a1d70/runtime/colorschemes">https://github.com/zyedidia/micro/tree/0859f4aa36d69e5cdb92b868dfc08498fd8a1d70/runtime/colorschemes</a></p>

<p>to <i>~/.config/micro/colorschemes</i> and tweak it to your hearts content.</p>

<p>Here&rsquo;s what i came up with</p>

<p><a href="https://manemobiili.github.io/assets/dukinuki.micro">https://manemobiili.github.io/assets/dukinuki.micro</a></p>

<p><img src="https://manemobiili.github.io/assets/Screenshot%20from%202023-06-12%2021-22-55.png" alt="micro screenshot" /></p>

<hr>

<p>With these customizations micro is a very intuitive editor. I highly recommend checking it out!</p>

<h4>Links</h4>

<p>Stackoverflow thread: <a href="https://stackoverflow.com/questions/69396856/tmux-micro-text-editor-shift-arrow-echo-keycode">https://stackoverflow.com/questions/69396856/tmux-micro-text-editor-shift-arrow-echo-keycode</a></p>

<p>Micro&rsquo;s author note: <a href="https://github.com/zyedidia/micro/issues/983#issuecomment-355867571">https://github.com/zyedidia/micro/issues/983#issuecomment-355867571</a></p>

<hr>

<h2>Update #1 (16. June 2023)</h2>

<p>Micro does not have anything binded to alt hjkl keys, so let&rsquo;s turn them into vi-style movement keys</p>

<pre><code>    &quot;Alt-h&quot;: &quot;CursorLeft&quot;,
    &quot;Alt-j&quot;: &quot;CursorDown&quot;,
    &quot;Alt-k&quot;: &quot;CursorUp&quot;,
    &quot;Alt-l&quot;: &quot;CursorRight&quot;
</code></pre>

<p>This is way nicer than moving with arrow keys, especially with those cramped laptop arrow keys!
However, there are some emacs keys out of the box. You can use them for moving word to word and line start to line end.</p>

<pre><code>    // Emacs-style keybindings
    // These are installed by default
    // No need to copy these keys
    &quot;Alt-f&quot;: &quot;WordRight&quot;,
    &quot;Alt-b&quot;: &quot;WordLeft&quot;,
    &quot;Alt-a&quot;: &quot;StartOfLine&quot;,
    &quot;Alt-e&quot;: &quot;EndOfLine&quot;
</code></pre>

</article>

<footer>
    <div class="right">
    	<a href="http://crew.0xffff.me">Powered by crew</a>
	</div>
</footer>


</body></html>
