<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.1//EN"
    "http://www.w3.org/TR/xhtml11/DTD/xhtml11.dtd">
<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en">
<head>
<meta http-equiv="Content-Type" content="application/xhtml+xml; charset=UTF-8" />
<meta name="generator" content="AsciiDoc 10.2.0" />
<title>How to rebase from an internal branch</title>
<style type="text/css">
/* Shared CSS for AsciiDoc xhtml11 and html5 backends */

/* Default font. */
body {
  font-family: Georgia,serif;
}

/* Title font. */
h1, h2, h3, h4, h5, h6,
div.title, caption.title,
thead, p.table.header,
#toctitle,
#author, #revnumber, #revdate, #revremark,
#footer {
  font-family: Arial,Helvetica,sans-serif;
}

body {
  margin: 1em 5% 1em 5%;
}

a {
  color: blue;
  text-decoration: underline;
}
a:visited {
  color: fuchsia;
}

em {
  font-style: italic;
  color: navy;
}

strong {
  font-weight: bold;
  color: #083194;
}

h1, h2, h3, h4, h5, h6 {
  color: #527bbd;
  margin-top: 1.2em;
  margin-bottom: 0.5em;
  line-height: 1.3;
}

h1, h2, h3 {
  border-bottom: 2px solid silver;
}
h2 {
  padding-top: 0.5em;
}
h3 {
  float: left;
}
h3 + * {
  clear: left;
}
h5 {
  font-size: 1.0em;
}

div.sectionbody {
  margin-left: 0;
}

hr {
  border: 1px solid silver;
}

p {
  margin-top: 0.5em;
  margin-bottom: 0.5em;
}

ul, ol, li > p {
  margin-top: 0;
}
ul > li     { color: #aaa; }
ul > li > * { color: black; }

.monospaced, code, pre {
  font-family: "Courier New", Courier, monospace;
  font-size: inherit;
  color: navy;
  padding: 0;
  margin: 0;
}
pre {
  white-space: pre-wrap;
}

#author {
  color: #527bbd;
  font-weight: bold;
  font-size: 1.1em;
}
#email {
}
#revnumber, #revdate, #revremark {
}

#footer {
  font-size: small;
  border-top: 2px solid silver;
  padding-top: 0.5em;
  margin-top: 4.0em;
}
#footer-text {
  float: left;
  padding-bottom: 0.5em;
}
#footer-badges {
  float: right;
  padding-bottom: 0.5em;
}

#preamble {
  margin-top: 1.5em;
  margin-bottom: 1.5em;
}
div.imageblock, div.exampleblock, div.verseblock,
div.quoteblock, div.literalblock, div.listingblock, div.sidebarblock,
div.admonitionblock {
  margin-top: 1.0em;
  margin-bottom: 1.5em;
}
div.admonitionblock {
  margin-top: 2.0em;
  margin-bottom: 2.0em;
  margin-right: 10%;
  color: #606060;
}

div.content { /* Block element content. */
  padding: 0;
}

/* Block element titles. */
div.title, caption.title {
  color: #527bbd;
  font-weight: bold;
  text-align: left;
  margin-top: 1.0em;
  margin-bottom: 0.5em;
}
div.title + * {
  margin-top: 0;
}

td div.title:first-child {
  margin-top: 0.0em;
}
div.content div.title:first-child {
  margin-top: 0.0em;
}
div.content + div.title {
  margin-top: 0.0em;
}

div.sidebarblock > div.content {
  background: #ffffee;
  border: 1px solid #dddddd;
  border-left: 4px solid #f0f0f0;
  padding: 0.5em;
}

div.listingblock > div.content {
  border: 1px solid #dddddd;
  border-left: 5px solid #f0f0f0;
  background: #f8f8f8;
  padding: 0.5em;
}

div.quoteblock, div.verseblock {
  padding-left: 1.0em;
  margin-left: 1.0em;
  margin-right: 10%;
  border-left: 5px solid #f0f0f0;
  color: #888;
}

div.quoteblock > div.attribution {
  padding-top: 0.5em;
  text-align: right;
}

div.verseblock > pre.content {
  font-family: inherit;
  font-size: inherit;
}
div.verseblock > div.attribution {
  padding-top: 0.75em;
  text-align: left;
}
/* DEPRECATED: Pre version 8.2.7 verse style literal block. */
div.verseblock + div.attribution {
  text-align: left;
}

div.admonitionblock .icon {
  vertical-align: top;
  font-size: 1.1em;
  font-weight: bold;
  text-decoration: underline;
  color: #527bbd;
  padding-right: 0.5em;
}
div.admonitionblock td.content {
  padding-left: 0.5em;
  border-left: 3px solid #dddddd;
}

div.exampleblock > div.content {
  border-left: 3px solid #dddddd;
  padding-left: 0.5em;
}

div.imageblock div.content { padding-left: 0; }
span.image img { border-style: none; vertical-align: text-bottom; }
a.image:visited { color: white; }

dl {
  margin-top: 0.8em;
  margin-bottom: 0.8em;
}
dt {
  margin-top: 0.5em;
  margin-bottom: 0;
  font-style: normal;
  color: navy;
}
dd > *:first-child {
  margin-top: 0.1em;
}

ul, ol {
    list-style-position: outside;
}
ol.arabic {
  list-style-type: decimal;
}
ol.loweralpha {
  list-style-type: lower-alpha;
}
ol.upperalpha {
  list-style-type: upper-alpha;
}
ol.lowerroman {
  list-style-type: lower-roman;
}
ol.upperroman {
  list-style-type: upper-roman;
}

div.compact ul, div.compact ol,
div.compact p, div.compact p,
div.compact div, div.compact div {
  margin-top: 0.1em;
  margin-bottom: 0.1em;
}

tfoot {
  font-weight: bold;
}
td > div.verse {
  white-space: pre;
}

div.hdlist {
  margin-top: 0.8em;
  margin-bottom: 0.8em;
}
div.hdlist tr {
  padding-bottom: 15px;
}
dt.hdlist1.strong, td.hdlist1.strong {
  font-weight: bold;
}
td.hdlist1 {
  vertical-align: top;
  font-style: normal;
  padding-right: 0.8em;
  color: navy;
}
td.hdlist2 {
  vertical-align: top;
}
div.hdlist.compact tr {
  margin: 0;
  padding-bottom: 0;
}

.comment {
  background: yellow;
}

.footnote, .footnoteref {
  font-size: 0.8em;
}

span.footnote, span.footnoteref {
  vertical-align: super;
}

#footnotes {
  margin: 20px 0 20px 0;
  padding: 7px 0 0 0;
}

#footnotes div.footnote {
  margin: 0 0 5px 0;
}

#footnotes hr {
  border: none;
  border-top: 1px solid silver;
  height: 1px;
  text-align: left;
  margin-left: 0;
  width: 20%;
  min-width: 100px;
}

div.colist td {
  padding-right: 0.5em;
  padding-bottom: 0.3em;
  vertical-align: top;
}
div.colist td img {
  margin-top: 0.3em;
}

@media print {
  #footer-badges { display: none; }
}

#toc {
  margin-bottom: 2.5em;
}

#toctitle {
  color: #527bbd;
  font-size: 1.1em;
  font-weight: bold;
  margin-top: 1.0em;
  margin-bottom: 0.1em;
}

div.toclevel0, div.toclevel1, div.toclevel2, div.toclevel3, div.toclevel4 {
  margin-top: 0;
  margin-bottom: 0;
}
div.toclevel2 {
  margin-left: 2em;
  font-size: 0.9em;
}
div.toclevel3 {
  margin-left: 4em;
  font-size: 0.9em;
}
div.toclevel4 {
  margin-left: 6em;
  font-size: 0.9em;
}

span.aqua { color: aqua; }
span.black { color: black; }
span.blue { color: blue; }
span.fuchsia { color: fuchsia; }
span.gray { color: gray; }
span.green { color: green; }
span.lime { color: lime; }
span.maroon { color: maroon; }
span.navy { color: navy; }
span.olive { color: olive; }
span.purple { color: purple; }
span.red { color: red; }
span.silver { color: silver; }
span.teal { color: teal; }
span.white { color: white; }
span.yellow { color: yellow; }

span.aqua-background { background: aqua; }
span.black-background { background: black; }
span.blue-background { background: blue; }
span.fuchsia-background { background: fuchsia; }
span.gray-background { background: gray; }
span.green-background { background: green; }
span.lime-background { background: lime; }
span.maroon-background { background: maroon; }
span.navy-background { background: navy; }
span.olive-background { background: olive; }
span.purple-background { background: purple; }
span.red-background { background: red; }
span.silver-background { background: silver; }
span.teal-background { background: teal; }
span.white-background { background: white; }
span.yellow-background { background: yellow; }

span.big { font-size: 2em; }
span.small { font-size: 0.6em; }

span.underline { text-decoration: underline; }
span.overline { text-decoration: overline; }
span.line-through { text-decoration: line-through; }

div.unbreakable { page-break-inside: avoid; }


/*
 * xhtml11 specific
 *
 * */

div.tableblock {
  margin-top: 1.0em;
  margin-bottom: 1.5em;
}
div.tableblock > table {
  border: 3px solid #527bbd;
}
thead, p.table.header {
  font-weight: bold;
  color: #527bbd;
}
p.table {
  margin-top: 0;
}
/* Because the table frame attribute is overridden by CSS in most browsers. */
div.tableblock > table[frame="void"] {
  border-style: none;
}
div.tableblock > table[frame="hsides"] {
  border-left-style: none;
  border-right-style: none;
}
div.tableblock > table[frame="vsides"] {
  border-top-style: none;
  border-bottom-style: none;
}


/*
 * html5 specific
 *
 * */

table.tableblock {
  margin-top: 1.0em;
  margin-bottom: 1.5em;
}
thead, p.tableblock.header {
  font-weight: bold;
  color: #527bbd;
}
p.tableblock {
  margin-top: 0;
}
table.tableblock {
  border-width: 3px;
  border-spacing: 0px;
  border-style: solid;
  border-color: #527bbd;
  border-collapse: collapse;
}
th.tableblock, td.tableblock {
  border-width: 1px;
  padding: 4px;
  border-style: solid;
  border-color: #527bbd;
}

table.tableblock.frame-topbot {
  border-left-style: hidden;
  border-right-style: hidden;
}
table.tableblock.frame-sides {
  border-top-style: hidden;
  border-bottom-style: hidden;
}
table.tableblock.frame-none {
  border-style: hidden;
}

th.tableblock.halign-left, td.tableblock.halign-left {
  text-align: left;
}
th.tableblock.halign-center, td.tableblock.halign-center {
  text-align: center;
}
th.tableblock.halign-right, td.tableblock.halign-right {
  text-align: right;
}

th.tableblock.valign-top, td.tableblock.valign-top {
  vertical-align: top;
}
th.tableblock.valign-middle, td.tableblock.valign-middle {
  vertical-align: middle;
}
th.tableblock.valign-bottom, td.tableblock.valign-bottom {
  vertical-align: bottom;
}


/*
 * manpage specific
 *
 * */

body.manpage h1 {
  padding-top: 0.5em;
  padding-bottom: 0.5em;
  border-top: 2px solid silver;
  border-bottom: 2px solid silver;
}
body.manpage h2 {
  border-style: none;
}
body.manpage div.sectionbody {
  margin-left: 3em;
}

@media print {
  body.manpage div#toc { display: none; }
}


</style>
<script type="text/javascript">
/*<![CDATA[*/
var asciidoc = {  // Namespace.

/////////////////////////////////////////////////////////////////////
// Table Of Contents generator
/////////////////////////////////////////////////////////////////////

/* Author: Mihai Bazon, September 2002
 * http://students.infoiasi.ro/~mishoo
 *
 * Table Of Content generator
 * Version: 0.4
 *
 * Feel free to use this script under the terms of the GNU General Public
 * License, as long as you do not remove or alter this notice.
 */

 /* modified by Troy D. Hanson, September 2006. License: GPL */
 /* modified by Stuart Rackham, 2006, 2009. License: GPL */

// toclevels = 1..4.
toc: function (toclevels) {

  function getText(el) {
    var text = "";
    for (var i = el.firstChild; i != null; i = i.nextSibling) {
      if (i.nodeType == 3 /* Node.TEXT_NODE */) // IE doesn't speak constants.
        text += i.data;
      else if (i.firstChild != null)
        text += getText(i);
    }
    return text;
  }

  function TocEntry(el, text, toclevel) {
    this.element = el;
    this.text = text;
    this.toclevel = toclevel;
  }

  function tocEntries(el, toclevels) {
    var result = new Array;
    var re = new RegExp('[hH]([1-'+(toclevels+1)+'])');
    // Function that scans the DOM tree for header elements (the DOM2
    // nodeIterator API would be a better technique but not supported by all
    // browsers).
    var iterate = function (el) {
      for (var i = el.firstChild; i != null; i = i.nextSibling) {
        if (i.nodeType == 1 /* Node.ELEMENT_NODE */) {
          var mo = re.exec(i.tagName);
          if (mo && (i.getAttribute("class") || i.getAttribute("className")) != "float") {
            result[result.length] = new TocEntry(i, getText(i), mo[1]-1);
          }
          iterate(i);
        }
      }
    }
    iterate(el);
    return result;
  }

  var toc = document.getElementById("toc");
  if (!toc) {
    return;
  }

  // Delete existing TOC entries in case we're reloading the TOC.
  var tocEntriesToRemove = [];
  var i;
  for (i = 0; i < toc.childNodes.length; i++) {
    var entry = toc.childNodes[i];
    if (entry.nodeName.toLowerCase() == 'div'
     && entry.getAttribute("class")
     && entry.getAttribute("class").match(/^toclevel/))
      tocEntriesToRemove.push(entry);
  }
  for (i = 0; i < tocEntriesToRemove.length; i++) {
    toc.removeChild(tocEntriesToRemove[i]);
  }

  // Rebuild TOC entries.
  var entries = tocEntries(document.getElementById("content"), toclevels);
  for (var i = 0; i < entries.length; ++i) {
    var entry = entries[i];
    if (entry.element.id == "")
      entry.element.id = "_toc_" + i;
    var a = document.createElement("a");
    a.href = "#" + entry.element.id;
    a.appendChild(document.createTextNode(entry.text));
    var div = document.createElement("div");
    div.appendChild(a);
    div.className = "toclevel" + entry.toclevel;
    toc.appendChild(div);
  }
  if (entries.length == 0)
    toc.parentNode.removeChild(toc);
},


/////////////////////////////////////////////////////////////////////
// Footnotes generator
/////////////////////////////////////////////////////////////////////

/* Based on footnote generation code from:
 * http://www.brandspankingnew.net/archive/2005/07/format_footnote.html
 */

footnotes: function () {
  // Delete existing footnote entries in case we're reloading the footnodes.
  var i;
  var noteholder = document.getElementById("footnotes");
  if (!noteholder) {
    return;
  }
  var entriesToRemove = [];
  for (i = 0; i < noteholder.childNodes.length; i++) {
    var entry = noteholder.childNodes[i];
    if (entry.nodeName.toLowerCase() == 'div' && entry.getAttribute("class") == "footnote")
      entriesToRemove.push(entry);
  }
  for (i = 0; i < entriesToRemove.length; i++) {
    noteholder.removeChild(entriesToRemove[i]);
  }

  // Rebuild footnote entries.
  var cont = document.getElementById("content");
  var spans = cont.getElementsByTagName("span");
  var refs = {};
  var n = 0;
  for (i=0; i<spans.length; i++) {
    if (spans[i].className == "footnote") {
      n++;
      var note = spans[i].getAttribute("data-note");
      if (!note) {
        // Use [\s\S] in place of . so multi-line matches work.
        // Because JavaScript has no s (dotall) regex flag.
        note = spans[i].innerHTML.match(/\s*\[([\s\S]*)]\s*/)[1];
        spans[i].innerHTML =
          "[<a id='_footnoteref_" + n + "' href='#_footnote_" + n +
          "' title='View footnote' class='footnote'>" + n + "</a>]";
        spans[i].setAttribute("data-note", note);
      }
      noteholder.innerHTML +=
        "<div class='footnote' id='_footnote_" + n + "'>" +
        "<a href='#_footnoteref_" + n + "' title='Return to text'>" +
        n + "</a>. " + note + "</div>";
      var id =spans[i].getAttribute("id");
      if (id != null) refs["#"+id] = n;
    }
  }
  if (n == 0)
    noteholder.parentNode.removeChild(noteholder);
  else {
    // Process footnoterefs.
    for (i=0; i<spans.length; i++) {
      if (spans[i].className == "footnoteref") {
        var href = spans[i].getElementsByTagName("a")[0].getAttribute("href");
        href = href.match(/#.*/)[0];  // Because IE return full URL.
        n = refs[href];
        spans[i].innerHTML =
          "[<a href='#_footnote_" + n +
          "' title='View footnote' class='footnote'>" + n + "</a>]";
      }
    }
  }
},

install: function(toclevels) {
  var timerId;

  function reinstall() {
    asciidoc.footnotes();
    if (toclevels) {
      asciidoc.toc(toclevels);
    }
  }

  function reinstallAndRemoveTimer() {
    clearInterval(timerId);
    reinstall();
  }

  timerId = setInterval(reinstall, 500);
  if (document.addEventListener)
    document.addEventListener("DOMContentLoaded", reinstallAndRemoveTimer, false);
  else
    window.onload = reinstallAndRemoveTimer;
}

}
asciidoc.install();
/*]]>*/
</script>
</head>
<body class="article">
<div id="header">
<h1>How to rebase from an internal branch</h1>
</div>
<div id="content">
<div id="preamble">
<div class="sectionbody">
<div class="listingblock">
<div class="content">
<pre><code>Petr Baudis &lt;pasky@suse.cz&gt; writes:

&gt; Dear diary, on Sun, Aug 14, 2005 at 09:57:13AM CEST, I got a letter
&gt; where Junio C Hamano &lt;junkio@cox.net&gt; told me that...
&gt;&gt; Linus Torvalds &lt;torvalds@osdl.org&gt; writes:
&gt;&gt;
&gt;&gt; &gt; Junio, maybe you want to talk about how you move patches from your
&gt;&gt; &gt; "seen" branch to the real branches.
&gt;&gt;
&gt; Actually, wouldn't this be also precisely for what StGIT is intended to?</code></pre>
</div></div>
<div class="paragraph"><p>Exactly my feeling.  I was sort of waiting for Catalin to speak
up.  With its basing philosophical ancestry on quilt, this is
the kind of task StGIT is designed to do.</p></div>
<div class="paragraph"><p>I just have done a simpler one, this time using only the core
Git tools.</p></div>
<div class="paragraph"><p>I had a handful of commits that were ahead of master in <em>seen</em>, and I
wanted to add some documentation bypassing my usual habit of
placing new things in <em>seen</em> first.  At the beginning, the commit
ancestry graph looked like this:</p></div>
<div class="literalblock">
<div class="content">
<pre><code>                         *"seen" head
master --&gt; #1 --&gt; #2 --&gt; #3</code></pre>
</div></div>
<div class="paragraph"><p>So I started from master, made a bunch of edits, and committed:</p></div>
<div class="literalblock">
<div class="content">
<pre><code>$ git checkout master
$ cd Documentation; ed git.txt ...
$ cd ..; git add Documentation/*.txt
$ git commit -s</code></pre>
</div></div>
<div class="paragraph"><p>After the commit, the ancestry graph would look like this:</p></div>
<div class="literalblock">
<div class="content">
<pre><code>                          *"seen" head
master^ --&gt; #1 --&gt; #2 --&gt; #3
      \
        \---&gt; master</code></pre>
</div></div>
<div class="paragraph"><p>The old master is now master^ (the first parent of the master).
The new master commit holds my documentation updates.</p></div>
<div class="paragraph"><p>Now I have to deal with "seen" branch.</p></div>
<div class="paragraph"><p>This is the kind of situation I used to have all the time when
Linus was the maintainer and I was a contributor, when you look
at "master" branch being the "maintainer" branch, and "seen"
branch being the "contributor" branch.  Your work started at the
tip of the "maintainer" branch some time ago, you made a lot of
progress in the meantime, and now the maintainer branch has some
other commits you do not have yet.  And "git rebase" was written
with the explicit purpose of helping to maintain branches like
"seen".  You <em>could</em> merge master to <em>seen</em> and keep going, but if you
eventually want to cherrypick and merge some but not necessarily
all changes back to the master branch, it often makes later
operations for <em>you</em> easier if you rebase (i.e. carry forward
your changes) "seen" rather than merge.  So I ran "git rebase":</p></div>
<div class="literalblock">
<div class="content">
<pre><code>$ git checkout seen
$ git rebase master seen</code></pre>
</div></div>
<div class="paragraph"><p>What this does is to pick all the commits since the current
branch (note that I now am on "seen" branch) forked from the
master branch, and forward port these changes.</p></div>
<div class="literalblock">
<div class="content">
<pre><code>master^ --&gt; #1 --&gt; #2 --&gt; #3
      \                                  *"seen" head
        \---&gt; master --&gt; #1' --&gt; #2' --&gt; #3'</code></pre>
</div></div>
<div class="paragraph"><p>The diff between master^ and #1 is applied to master and
committed to create #1' commit with the commit information (log,
author and date) taken from commit #1.  On top of that #2' and #3'
commits are made similarly out of #2 and #3 commits.</p></div>
<div class="paragraph"><p>Old #3 is not recorded in any of the .git/refs/heads/ file
anymore, so after doing this you will have dangling commit if
you ran fsck-cache, which is normal.  After testing "seen", you
can run "git prune" to get rid of those original three commits.</p></div>
<div class="paragraph"><p>While I am talking about "git rebase", I should talk about how
to do cherrypicking using only the core Git tools.</p></div>
<div class="paragraph"><p>Let&#8217;s go back to the earlier picture, with different labels.</p></div>
<div class="paragraph"><p>You, as an individual developer, cloned upstream repository and
made a couple of commits on top of it.</p></div>
<div class="literalblock">
<div class="content">
<pre><code>                           *your "master" head
upstream --&gt; #1 --&gt; #2 --&gt; #3</code></pre>
</div></div>
<div class="paragraph"><p>You would want changes #2 and #3 incorporated in the upstream,
while you feel that #1 may need further improvements.  So you
prepare #2 and #3 for e-mail submission.</p></div>
<div class="literalblock">
<div class="content">
<pre><code>$ git format-patch master^^ master</code></pre>
</div></div>
<div class="paragraph"><p>This creates two files, 0001-XXXX.patch and 0002-XXXX.patch.  Send
them out "To: " your project maintainer and "Cc: " your mailing
list.  You could use contributed script git-send-email if
your host has necessary perl modules for this, but your usual
MUA would do as long as it does not corrupt whitespaces in the
patch.</p></div>
<div class="paragraph"><p>Then you would wait, and you find out that the upstream picked
up your changes, along with other changes.</p></div>
<div class="literalblock">
<div class="content">
<pre><code> where                      *your "master" head
upstream --&gt; #1 --&gt; #2 --&gt; #3
  used   \
 to be     \--&gt; #A --&gt; #2' --&gt; #3' --&gt; #B --&gt; #C
                                              *upstream head</code></pre>
</div></div>
<div class="paragraph"><p>The two commits #2' and #3' in the above picture record the same
changes your e-mail submission for #2 and #3 contained, but
probably with the new sign-off line added by the upstream
maintainer and definitely with different committer and ancestry
information, they are different objects from #2 and #3 commits.</p></div>
<div class="paragraph"><p>You fetch from upstream, but not merge.</p></div>
<div class="literalblock">
<div class="content">
<pre><code>$ git fetch upstream</code></pre>
</div></div>
<div class="paragraph"><p>This leaves the updated upstream head in .git/FETCH_HEAD but
does not touch your .git/HEAD or .git/refs/heads/master.
You run "git rebase" now.</p></div>
<div class="literalblock">
<div class="content">
<pre><code>$ git rebase FETCH_HEAD master</code></pre>
</div></div>
<div class="paragraph"><p>Earlier, I said that rebase applies all the commits from your
branch on top of the upstream head.  Well, I lied.  "git rebase"
is a bit smarter than that and notices that #2 and #3 need not
be applied, so it only applies #1.  The commit ancestry graph
becomes something like this:</p></div>
<div class="literalblock">
<div class="content">
<pre><code> where                     *your old "master" head
upstream --&gt; #1 --&gt; #2 --&gt; #3
  used   \                      your new "master" head*
 to be     \--&gt; #A --&gt; #2' --&gt; #3' --&gt; #B --&gt; #C --&gt; #1'
                                              *upstream
                                              head</code></pre>
</div></div>
<div class="paragraph"><p>Again, "git prune" would discard the disused commits #1-#3 and
you continue on starting from the new "master" head, which is
the #1' commit.</p></div>
<div class="paragraph"><p>-jc</p></div>
</div>
</div>
</div>
<div id="footnotes"><hr /></div>
<div id="footer">
<div id="footer-text">
Last updated
 2023-01-23 14:33:16 PST
</div>
</div>
</body>
</html>
