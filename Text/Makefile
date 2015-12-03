SHELL    =bash
TARGET   =main.pdf
PREAMBLE =preamble-vbm
TEX      =*.tex
AUX      =aux

all: $(TARGET)

$(TARGET): .FORCE
	@[ -d $(AUX) ] || mkdir $(AUX)
	@cd aux && mv * .. &>/dev/null ||:
	latexmk -interaction=nonstopmode -recorder- -halt-on-error -pdf $(TARGET:.pdf=)
	@mv *.aux *.log *.fdb_latexmk *.toc aux &>/dev/null ||:

.FORCE:


.PHONY:
clean:
	latexmk -C
	rm -rf $(AUX)/*

.PHONY:
view:
	(evince $(TARGET) 2>/dev/null || atril $(TARGET) 2>/dev/null) &
