SOURCE=summarize
PDF=$(SOURCE).pdf
HTML=$(SOURCE).html

INTERMEDIAFILE=missfont.log $(SOURCE).aux $(SOURCE).log $(SOURCE).out $(SOURCE).toc $(SOURCE).bbl $(SOURCE).blg  $(SOURCE).dvi $(SOURCE).idv $(SOURCE).lg $(SOURCE).ps

LaTeX=xelatex
BiBTeX=bibtex

all:$(PDF)

$(INTERMEDIAFILE) $(PDF):$(SOURCE).tex ../refrence.bib  summarize_body.tex
	$(RM) $(INTERMEDIAFILE)
	$(LaTeX) -interaction=nonstopmode $(SOURCE)
	$(LaTeX) -interaction=nonstopmode $(SOURCE)
	-mkdir -p /tmp/tex
	iconv -f UTF-8 -t GBK ../refrence.bib -o /tmp/refrence.bib 
	iconv -f UTF-8 -t GBK summarize.aux -o /tmp/tex/summarize.gbk.aux
	cd /tmp/tex && env BIBINPUTS=/tmp/  $(BiBTeX) $(SOURCE).gbk
	iconv -t UTF-8 -f GBK /tmp/tex/summarize.gbk.bbl -o summarize.bbl
	$(LaTeX) -interaction=nonstopmode $(SOURCE)
	$(LaTeX) -interaction=nonstopmode $(SOURCE)
clean:
	$(RM) $(INTERMEDIAFILE) $(PDF) *.aux *.bbl *.blg *.gbk.*
