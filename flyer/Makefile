TEX := xelatex
TEXARGS := -halt-on-error -interaction=nonstopmode --output-directory=build

SOURCES := flyer.tex

# Get the main file from the file
MAIN := $(shell sed -ne 's/^.*\!TeX root =\(.*\)$$/\1/ p' $(SOURCES))
PDF  := $(patsubst %.tex, build/%.pdf, $(MAIN))
SVG  := $(patsubst %.tex, build/%.svg, $(MAIN))

ifeq ($(strip $(MAIN)),)
MAIN := $(error Failed to identify TeX root, try adding \
	`% !TeX root = <filename>` to your main tex file)
endif

.PHONY: all
all: $(PDF) $(SVG)

build/%.pdf: %.tex $(SOURCES)
	mkdir -p build
	$(TEX) $(TEXARGS) $<
	$(TEX) $(TEXARGS) $<

build/%.svg: build/%.pdf
	dvisvgm --precision=5 --no-fonts --linkmark=none --pdf $< --output=$@

.PHONY: clean
clean:
	@rm -vrd build
