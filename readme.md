This is my homepage. 

# CV 

Here is a bit of information about how I use my homepage to create a CV.

# My goal: To write a CV in one format and in a way so that it can be rendered in multiple formats

I have trying to write my CV once and have it be displayed/rendered as HTML (for this website), a PDF (for sharing), and a Word document (also for sharing - as some folks require it to be in this format).

I have something that seems to work and so thought I would share what I did as a first attempt. In part, I hoped doing so would spark other folks sharing better ways (or suggesting improvements to me).

# The results

Here's what I did; all of the source files are available [here](https://github.com/jrosen48/utk-homepage); the final versions are available in the following formats from different URLs:

- HTML: [https://www.joshuamrosenberg.com/](https://www.joshuamrosenberg.com/)

- PDF: [https://www.joshuamrosenberg.com/rosenberg-cv.pdf](https://www.joshuamrosenberg.com/rosenberg-cv.pdf) 

- Word (.docx): [https://www.joshuamrosenberg.com/cv/rosenberg-cv.docx](https://www.joshuamrosenberg.com/cv/rosenberg-cv.docx)

# My process

*All of the file locations refer to the source [here](ttps://github.com/jrosen48/utk-homepage)*.

- Treated the file at `content/about-source.md` as the one file in which I wrote (and will update) my CV
- Added a file (in a new directory), `r/build.R`, which contains `cv-utils.R`
- This script (`cv-utils.R` does most of the work:
    - copies `content/about-source.md` to `static/cv` with the name (and file type) changed to `rosenberg-cv.Rmd` (and which)
    - reads `content/about-source.md`
        - then removes the LaTeX tags 
        - writes the file to to `static/cv` with the name (and file type) changed to `rosenberg-cv.Rmd`
        - and renders the Word document using `Rosenberg-CV-template.docx` as the document template (created by using the "Incremental style editing" described [here](https://rmarkdown.rstudio.com/articles_docx.html))
    - does essentially the steps taken to render the Word document *again* to render the HTML version
        - but with a line added after the front matter with a link to the PDF version
        - and with the result being saved to `content/about.md` to serve as basis for the HTML file rendered with that file name (i.e., the file [here](https://www.joshuamrosenberg.com/about/)
        