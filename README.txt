BCI SPEECH-TO-IMAGE COMMUNICATION FLOW — website
Jules Sherman · UC Irvine MHCID · August 2026

The eight sheets are real HTML, not pictures of sheets. The text can be
selected, searched, translated, enlarged, and read aloud by a screen reader.


HOW TO PUT THIS ONLINE
  1. Go to https://app.netlify.com/drop
  2. Drag this folder (or the zip) onto the page.
  3. About ten seconds later you have a live URL.
  4. To rename it: sign in, open the site, then
     Site configuration > Change site name.


WHAT IS IN HERE
  index.html            all eight sheets, plus the navigation and footer
  assets/sheets.css     the shared style system, commented
  assets/fonts/         Archivo Black and Chivo, self-hosted so the page does
                        not call out to Google and does not depend on it
  assets/fig/           the four illustrations that could not become text
  assets/bci-*          the title-page animation, its WebM fallback, and poster
  netlify.toml          cache headers, optional


WHERE THE VALUES CAME FROM
  Nothing was eyeballed. Colours, type sizes, weights, paddings and gaps were
  read out of the Figma file through Figma's own developer connection:
    ink    #0b0d14      body text and every rule
    muted  #5a6178      labels and secondary text
    pink   #ffe9f0      emphasis panels
    panel  #f6f7f9      quiet panels
  Type is Archivo Black for sheet titles and Chivo 400/500/700 for the rest.
  The Figma file itself was never modified.


WHAT IS STILL A PICTURE, AND WHY
  Four things are drawings and cannot be turned into text. Each carries a
  written description in its alt attribute:
    the six-panel storyboard on Sheet 01
    the participants strip on Sheet 02
    the design-values strip on Sheet 04
    the course-concepts strip on Sheet 07
  The title-page animation is also a picture. It is silent, so it needs no
  captions; it carries a written description of what it shows.


HOW THE ACCESSIBILITY WAS VERIFIED
  axe-core, the standard automated auditor, run against the whole page at
  1640, 1024, 390 and 320 pixels wide: zero violations at every width,
  covering WCAG 2.0 A and AA, WCAG 2.1 A and AA, and best practice.

  Checked by hand on top of that:
    - the heading outline runs h1, h2, h3, h4 with no skipped levels
    - the stakeholder table has a caption, column headers and row headers, so
      a screen reader announces "Nurses and direct care staff, what I need to
      learn, at 3:00 AM can you understand what was sent"
    - that table keeps its role, headers and cells when it stacks into cards
      on a phone, because the markup carries explicit ARIA roles; without
      them, restyling a table with display:block silently destroys its
      meaning in every major browser
    - no horizontal scrolling and no clipped text at any width down to 320px
    - lowest colour contrast anywhere on the site is 5.32:1, against the 4.5:1
      the standard asks for


TWO THINGS TO KNOW IF YOU EDIT IT
  Labels and titles are typed in normal sentence case and made uppercase by
  CSS, so a screen reader reads words rather than spelling letters out. Where
  real capitals belong to the word — BCI, BCIs, AAC, SLP, AI, CHI — the text
  is wrapped in <span class="keepcase"> so CSS cannot mangle it. Remove that
  and "BCIs" becomes "BCIS".

  The layout uses flex and grid only. Nothing is positioned absolutely and no
  box has a fixed height that could cut text off, which is what lets every
  sheet reflow onto a narrow screen.
