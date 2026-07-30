# pm-professor.com - static site

Files
-----
style.css                        every style, one file
index.html                       landing page (about / now / updates / notes / posts / contact)
notes.html                       full notes index, grouped by year
notes/concession-agreement.html  a note; copy this file to start a new one
CV_Ke.pdf                        linked from the nav on every page

Principle
---------
The HTML carries content only. There are no class attributes anywhere.
Every rule in style.css selects by element type, attribute or position,
so the markup below is all you ever need to write.

Add a row to any list (index.html or notes.html)
------------------------------------------------
    <li><a href="notes/my-new-note.html">Title of the thing</a><span>Jul 2026</span></li>
    <li>Plain text with no link<span>UTS</span></li>

Left side is either a link or bare text. Right side is always the last
<span> in the row: a date, a journal, a one-word marker. On wide screens
the marker is pinned right on the same line, so keep titles under about
65 characters. Below 34rem the row stops being a grid: the marker runs
on inline after the title, separated by a middot, and wraps with it. No
title length is unsafe on mobile.

Add a section
-------------
    <section>
      <h2 data-path="~/teaching">teaching</h2>
      <ul>
        <li>Project Management Fundamentals<span>Spring</span></li>
      </ul>
      <a href="teaching.html">all subjects -></a>   <!-- optional -->
    </section>

data-path holds the grey path shown at the right of the heading rule.
Write it exactly as you want it to appear, tilde included. The same
attribute drives the path beside your name in the page header, so there
is one convention for both.

Add a page
----------
Copy the nearest existing page and replace the body. Pages one folder
deep (notes/*.html) link to ../style.css, ../index.html, ../notes.html
and ../CV_Ke.pdf; everything else is identical markup.

Note pages open with an <hgroup>: an <h1> then a <p> holding the date
and reading time. No wrapper div, no classes.

Rules the CSS enforces
----------------------
No webfonts. Everything uses --font, a system monospace stack that
resolves to SF Mono or Menlo on Apple, Cascadia Mono or Consolas on
Windows, Liberation or DejaVu Sans Mono on Linux, and the generic
monospace elsewhere. Nothing is fetched from a third-party domain, so
the site renders immediately everywhere, including mainland China where
Google Fonts is blocked. Fixed-width characters are also what keeps the
right-hand dates aligned down each list.

One size (14px, --size in :root), one accent (--link). No images, no
code blocks. Headings inherit the body size; hierarchy comes from weight
and colour only. Change --size, --measure or any --gap-* in :root to
retune the whole site, including the mobile overrides.

Known gaps
----------
The nav block and the header/footer markup are duplicated in every page,
which is the only real maintenance cost left. Note and post links in
index.html and notes.html point to files that do not exist yet. There is
no atom.xml feed; if you add one, restore a footer link on index.html
and a <link rel="alternate"> tag in its <head>.
