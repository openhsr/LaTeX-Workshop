INPUTS  := gauss-flux.tex packages.tex
OUTPUTS := $(patsubst %.tex,%.pdf,$(INPUTS))

AUXDIR  := build
SUBDIRS := fig

TEX     := xelatex
TEXOPTS := --output-directory=$(AUXDIR) --8bit --interaction=nonstopmode

SUBDIR_FILES := $(wildcard $(SUBDIRS)/*)
AUX_SUBDIRS  := $(patsubst %,$(AUXDIR)/%,$(SUBDIRS))

.PHONY: all clean
all: $(OUTPUTS)

clean:
	rm -rdv $(OUTPUTS) $(AUXDIR)

$(OUTPUTS): %.pdf: %.tex $(SUBDIR_FILES) $(AUXDIR) $(AUX_SUBDIRS)
	$(TEX) $(TEXOPTS) $< && cp $(AUXDIR)/$@ .

$(AUX_SUBDIRS):
	mkdir -p $(AUX_SUBDIRS)

$(AUXDIR):
	mkdir -p $(AUXDIR)
 
