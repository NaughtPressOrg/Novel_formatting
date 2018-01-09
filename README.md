# fiction_novel

Everything I have learned for formatting a novel with LaTeX. LaTeX is generally used for formatting manuals and scientific text books, but it can be adapted to provide a professional typesetting and formatting environment for fiction novels.  

Please use this as a framework and reference, I am still very new to LaTeX so there could be many things that I am not doing entirely correctly.  

I made all of this on a machine with Ubuntu 16.04, but I believe all software detailed is supported on Linux, Mac OS, and Windows.

## Prerequisite

Install latest [texlive](https://www.tug.org/texlive/) package (this will include all add on packages like memoir, plus much more.)   
The texlive package that is included with Ubuntu is old and does not support everything, it is highly recommended to download the full source from https://www.tug.org/texlive/ and install src manually.    

I prefer TeXWorks as my compiler of choice, just update the path to reflect the local install of texlive. Edit -> Preferences -> Typesetting -> "Paths for TeX and related Programs" -> add


## Notes

main.tex - everything for setup and formatting should go in this document. This includes scripts, macros, includes, font selection, header/footer formatting, etc.

main.tex is the skeleton and brain of your document, with the content in seperate sub documents that will make it much easier for organizing and once you get used to the syntax much clearer where things should be changed and how that effects the document as a whole.

frontmatter.tex - This includes title page, dedication, copyright info, and anything that should preceed the novel. With all of these files it is important to visualize and understand how the viewer will see each page (front page, back page, even pages, odd pages) in relation to where content goes. I recommend comparing with other books in your home to see which pages are commonly included.

prologue.tex and chapter-one.tex - These files will hold your novel seperated by chapter. I've set them up to auto fill with Lorem Ipsum. which you can see in the included main.pdf

backmatter.tex - this inculdes any extra information at the end of your book.

main.pdf - this is the result of all the above files compiled together and published to a pdf.



## Going from LaTeX to epub
This was a journey of trial and error, so I would like to document it here  
Switch documentclass in main.tex to `\documentclass[10pt,ebook,oneside,openany]{memoir} %ebook format`. Save.    
Install `sudo apt install tex4ht` for html latex support.  
`$ htlatex main.tex` to produce main.html an html version of the final product. This will also produce a crapton of other support files. 

Use [Calibre](https://calibre-ebook.com/) to import the main.html and add metadata, bookcover, and convert to .epub. Save .epub to disk.

Import .epub into [Sigil](https://github.com/Sigil-Ebook/Sigil) and smooth out converting issues to make the document look as you wish. I often find that all the frontmatter and backmatter gets squished into a single "page" which makes it appear clumsy and less professional. I spend a lot of time at this stage adding pagebreaks and centering text to match the paperback/PDF edition that was lost during the conversion stages. You can also edit metadata and add content at this stage. Save, Run Epubcheck, and publish!

## Epub check
When submitting an `.epub` file to any service like Amazon, Google Play, Smashwords, etc; they all require that the .epub pass an epub check with this [epubchecker](https://github.com/IDPF/epubcheck).

To run locally, one must have java installed on your system
```
$ java -jar ~/Downloads/epubcheck-4.0.2/epubcheck.jar book.epub 
Validating using EPUB version 2.0.1 rules.
No errors or warnings detected.
epubcheck completed
```

Then you are ready to upload and publish your ebook file! If there are any errors, I find it easiest to correct them with [Sigil](https://github.com/Sigil-Ebook/Sigil).

