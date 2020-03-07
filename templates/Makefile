INPUT   := $(wildcard *.tex)
OUTPUT  := $(patsubst %.tex,%.pdf,$(INPUT))

AUXDIR  := build
SUBDIRS := fig

TEX     := xelatex
TEXOPTS := --output-directory=$(AUXDIR) --8bit --interaction=nonstopmode

SUBDIR_FILES := $(wildcard $(SUBDIRS)/*)
AUX_SUBDIRS  := $(patsubst %,$(AUXDIR)/%,$(SUBDIRS))

all: $(OUTPUT)

$(OUTPUT): $(INPUT) $(SUBDIR_FILES) $(AUXDIR) $(AUX_SUBDIRS)
	$(TEX) $(TEXOPTS) $< && cp $(AUXDIR)/$@ .

$(AUX_SUBDIRS):
	mkdir -p $(AUX_SUBDIRS)

$(AUXDIR):
	mkdir -p $(AUXDIR)
