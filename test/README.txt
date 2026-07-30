# pm-professor.com - static site

Files
-----
style.css                        every style, one file
index.html                       landing page (about / now / updates / notes / posts / contact)
notes.html                       full notes index, grouped by year
notes/concession-agreement.html  a note; copy this file to start a new one

Principle
---------
The HTML carries content only. There are no class attributes anywhere.
Every rule in style.css selects by element type and position, so the
markup below is all you ever need to write.

Add a row to any list (index.html or notes.html)
------------------------------------------------
    <li><a href="notes/my-new-note.html">Title of the thing</a><span>Jul 2026</span></li>
    <li>Plain text with no link<span>UTS</span></li>

Left side is either a link or bare text. Right side is always the last
<span> in the row: a date, a journal, a one-word marker. On wide screens
the marker is pinned right on the same line, so keep titles under about
55 characters. Below 34rem the row stops being a grid: the marker runs
on inline after the title, separated by a middot, and wraps with it. No
title length is unsafe on mobile.

Add a section
-------------
    <section>
      <h2 data-path="teaching">teaching</h2>
      <ul>
        <li>Project Management Fundamentals<span>Spring</span></li>
      </ul>
      <a href="teaching.html">all subjects -></a>   <!-- optional -->
    </section>

data-path holds the path shown in grey at the right of the heading rule.
The "~/" prefix, colour and weight are added by CSS, so write the path
without it: data-path="notes/2026" renders as ~/notes/2026.

Add a page
----------
Copy the nearest existing page and replace the body. Pages one folder
deep (notes/*.html) link to ../style.css, ../index.html, ../notes.html
and ../CV_Ke.pdf; everything else is identical markup.

Note pages open with an <hgroup>: an <h1> then a <p> holding the date
and reading time. No wrapper div, no classes.

Rules the CSS enforces
----------------------
No webfonts. Body text uses --font, the system sans stack (Inter first,
then the platform UI face). Code blocks use --font-mono. Nothing is
fetched from a third-party domain, so the site renders immediately
everywhere, including mainland China where Google Fonts is blocked.

One size (14px, --size in :root), one accent (--link). No images.
Headings inherit the body size; hierarchy comes from weight and colour
only. Change --size, --measure or any --gap-* in :root to retune the
whole site, including the mobile overrides.

Two commented font-family lines in style.css set the ~/path labels and
the row markers in monospace. Uncomment both to get them back.

Known gaps
----------
The nav block and the head/footer markup are duplicated in every page,
which is the only real maintenance cost left. Note and post links in
index.html and notes.html point to files that do not exist yet. There
is no atom.xml feed; if you add one, restore the footer link on
index.html and the <link rel="alternate"> tag in its <head>.
