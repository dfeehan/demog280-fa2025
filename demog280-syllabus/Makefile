## Put this Makefile in your project directory---i.e., the directory
## containing the paper you are writing. Assuming you are using the
## rest of the toolchain here, you can use it to create .html, .tex,
## and .pdf output files (complete with bibliography, if present) from
## your markdown file. 
## -	Change the paths at the top of the file as needed.
## -	Using `make` without arguments will generate html, tex, and pdf 
## 	output files from all of the files with the designated markdown
##	extension. The default is `.md` but you can change this. 
## -	You can specify an output format with `make tex`, `make pdf` or 
## - 	`make html`. 
## -	Doing `make clean` will remove all the .tex, .html, and .pdf files 
## 	in your working directory. Make sure you do not have files in these
##	formats that you want to keep!

## DMF NOTES JAN 2017:
## MODIFIED THE FOLLOWING FILES FROM kjhealy's setup:
##   * made a version of csl/chicago-syllabus.csl called csl/chicago-syllabus-nobib.csl
##     which does not print the full reference list at the bottom of the page
##   * made a version of marked/kultiad-serif.css called marked/kultias-serif-dmf.css
##     which wrapped the original file in <style> ... </style> tags, so that it
##     correctly gets read as CSS

## Markdown extension (e.g. md, markdown, mdown).
MEXT = md

## All markdown files in the working directory
SRC = $(wildcard *.$(MEXT))

## Location of Pandoc support files.
PREFIX = /Users/dennis/kjhealy_templates/pandoc-templates
##PREFIX = assets/pandoc-templates

## Location of your working bibliography file
BIB = /Users/dennis/Dropbox/teaching/2019_spring/grad/class_networks_2019.bib

## CSL stylesheet (located in the csl folder of the PREFIX directory).
## use the -nobib version to prevent the full list of references from printing out at the end
CSL = chicago-syllabus-nobib
#CSL = apsa


PDFS=$(SRC:.md=.pdf)
HTML=$(SRC:.md=.html)
TEX=$(SRC:.md=.tex)


all:	$(PDFS) $(HTML) $(TEX)

pdf:	clean $(PDFS)
html:	clean $(HTML)
tex:	clean $(TEX)

#%.html:	%.md
#    pandoc -r markdown+simple_tables+table_captions+yaml_metadata_block -w html -S --template=$(PREFIX)/templates/html.template --css=$(PREFIX)/marked/kultiad-serif.css --filter pandoc-citeproc --csl=$(PREFIX)/csl/$(CSL).csl --bibliography=$(BIB) -o $@ $<

%.html:	%.md
	pandoc -r markdown+simple_tables+table_captions+yaml_metadata_block -w html --template=$(PREFIX)/templates/html.template -H $(PREFIX)/marked/kultiad-serif-dmf.css --filter pandoc-citeproc --filter pandoc-include --csl=$(PREFIX)/csl/$(CSL).csl --bibliography=$(BIB) -o $@ $<

%.tex:	%.md
	pandoc -r markdown+simple_tables+table_captions+yaml_metadata_block -w latex -s --latex-engine=pdflatex --template=$(PREFIX)/templates/latex.template --filter pandoc-citeproc --filter pandoc-include --csl=$(PREFIX)/csl/ajps.csl --bibliography=$(BIB) -o $@ $<


%.pdf:	%.md
	pandoc -r markdown+simple_tables+table_captions+yaml_metadata_block -s --pdf-engine=pdflatex --filter pandoc-citeproc --filter pandoc-include --csl=$(PREFIX)/csl/$(CSL).csl --bibliography=$(BIB) -o $@ $<
	#pandoc -r markdown+simple_tables+table_captions+yaml_metadata_block+smart -s --pdf-engine=pdflatex --template=$(PREFIX)/templates/latex.template --filter pandoc-citeproc --csl=$(PREFIX)/csl/$(CSL).csl --bibliography=$(BIB) -o $@ $<

clean:
	rm -f *.html *.pdf *.tex
