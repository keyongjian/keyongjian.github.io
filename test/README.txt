# pm-professor.com — static site

Files
-----
style.css                        every style, one file
index.html                       landing page (about / now / updates / notes / posts / contact)
notes.html                       full notes index, grouped by year
notes/concession-agreement.html  a note; copy this file to start a new one

Add a row to any list (index.html or notes.html)
------------------------------------------------
    <li><a href="notes/my-new-note.html">Title of the thing</a><span class="meta">Jul 2026</span></li>

Left side can be a link or plain <span>Text</span>. Right side is always
<span class="meta"> — a date, a journal, a one-word marker. Rows stay on one
line: the marker is pinned right, so keep titles under ~55 characters.

Add a section
-------------
    <section>
      <div class="head"><h2>teaching</h2><span class="dim">~/teaching</span></div>
      <ul class="rows">
        <li><span>Project Management Fundamentals</span><span class="meta">Spring</span></li>
      </ul>
      <a class="more" href="teaching.html">all subjects →</a>   <!-- optional -->
    </section>

Add a page
----------
Copy the nearest existing page and replace the body. Pages one folder deep
(notes/*.html) link to ../style.css, ../index.html, ../notes.html — everything
else is the same markup.

Rules the CSS enforces
----------------------
One font (IBM Plex Mono), one size (14px, --size in :root), one accent (--link).
No images. Headings inherit the body size; hierarchy comes from weight and
colour only. Change --size or --measure in :root to retune the whole site.
