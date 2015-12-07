SHELL    =bash
TARGET   =main.pdf
PREAMBLE =preamble-vbm
TEX      =*.tex
AUX      =aux

all: $(TARGET)

$(TARGET): .FORCE
	@[ -d $(AUX) ] || mkdir $(AUX)
	@cd aux && mv * .. &>/dev/null ||:
	latexmk -interaction=nonstopmode -bibtex -recorder- -halt-on-error -pdf\
		$(TARGET:.pdf=)
	@mv main.run.xml main-blx.bib *.aux *.bbl *.log *.fdb_latexmk *.toc *.blg aux \
		&>/dev/null ||:

.FORCE:


.PHONY:
clean:
	latexmk -C
	rm -rf $(AUX)/* *.bbl main.run.xml main-blx.bib

.PHONY:
view:
	(evince $(TARGET) 2>/dev/null || atril $(TARGET) 2>/dev/null) &
