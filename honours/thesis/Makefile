#############################################################################

# Makefile for Thesis

#############################################################################

LATEX	  = latex
BIBTEX	  = bibtex
PDFLATEX  = pdflatex
DVIPS	  = dvips
EPSTOPDF  = epstopdf

UMASK	  = umask 007

#############################################################################

MAINBASE  = thesis
BIBFILE	  = allan.bib
TARTARGET = thesis.tar

MAINTEX	  = $(MAINBASE).tex
TARGET    = $(MAINBASE).dvi
PSTARGET  = $(MAINBASE).ps
PDFTARGET = $(MAINBASE).pdf

#############################################################################

MAKEFILE  = Makefile

SRCS	  = preamble.tex title.tex thesis.tex \
01-intro.tex 02-background.tex 03-method.tex \
04-findings.tex 05-implications.tex 06-conclusions.tex


FIGURES	  = Figures

STYLES    = llncs.cls float.sty floatsty.sty

#############################################################################

.SUFFIXES:	.tex .pdf .dvi

# make main target
$(TARGET) : $(MAINTEX) $(SRCS) $(BIBFILE)
	@$(MAKE) tex
	@$(MAKE) bib
	@$(MAKE) tex
	@$(MAKE) tex


# in case you need to resolve new cross-references:
again tex :
	@echo "latex $(MAINBASE)"
	@( $(UMASK); $(LATEX) $(MAINBASE) )


# bibtex only
bib : $(BIBFILE)
	@( $(UMASK); $(BIBTEX) $(MAINBASE) )


# PostScript file
ps $(PSTARGET) : $(TARGET)
	@echo "dvips $(MAINBASE)"
	@( $(UMASK); $(DVIPS) -o $(PSTARGET) $(TARGET) )


# pdf
pdf $(PDFTARGET) : $(SRCS) $(BIBFILE)
	@$(MAKE) clean
	@$(MAKE) pdfagain
	@$(MAKE) bib
	@$(MAKE) pdfagain
	@$(MAKE) pdfagain
	@$(MAKE) pdfagain

# pdflatex only
pdfagain :
	@echo "pdflatex $(MAINBASE)"
	@( $(UMASK); $(PDFLATEX) $(MAINBASE) )


# archive
archive tar :
	@tar -cvf $(TARTARGET) $(MAINTEX) $(SRCS) $(BIBFILE) $(STYLES) $(MAKEFILE) $(FIGURES)
	@chmod 660 $(TARTARGET)
	@gzip -n -9 $(TARTARGET)


# remove unnecessary files
clean :
	$(RM) *.aux *.log *.dvi *.out *.pdf *.ps *.gz
	$(RM) *.blg *.bbl *.toc* *.lof *.lot #*
	$(RM) *~ *% gugus*
	$(RM) $(PSTARGET)

cleanpdf :
	$(RM) $(PDFTARGET)	

# Check for duplicate words	
dups :
	@echo "Checking for duplicate words" 
	perl ./bin/dups.pl *.tex

# Check for use of passive words -- ideally should be avoided
passive :
	@echo "Checking for use of passive voice"
	sh ./bin/passive.sh *.tex

# Check for use of weasel words -- ideally should be avoided
weasel :
	@echo "Checking for use of passive voice"
	sh ./bin/weasel.sh *.tex

# Run all review tasks
rev :
	@$(MAKE) dups
	@$(MAKE) passive
	@$(MAKE) weasel

# Run a word count on the thesis to get an approximate number
wordcount :
	perl ./bin/texcount.pl *.tex
	
# Run a word count on the PDF file -- this is more precise
wcpdf :
	@$(MAKE) pdf
	ps2ascii thesis.pdf | wc -w

#############################################################################
