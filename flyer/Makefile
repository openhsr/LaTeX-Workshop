TEX := xelatex
TEXARGS := -halt-on-error -interaction=nonstopmode --output-directory=build

SOURCES := flyer.tex flyer-advanced.tex

# Get the main file from the file
PDFS  := $(patsubst %.tex, build/%.pdf, $(SOURCES))
SVGS  := $(patsubst %.tex, build/%.svg, $(SOURCES))

.PHONY: all
all: $(PDFS) $(SVGS)

build/%.pdf: %.tex $(SOURCES)
	mkdir -p build
	$(TEX) $(TEXARGS) $<
	$(TEX) $(TEXARGS) $<

build/%.svg: build/%.pdf
	dvisvgm --precision=5 --no-fonts --linkmark=none --pdf $< --output=$@ \
		--libgs=/opt/homebrew/Cellar/ghostscript/10.0.0/lib/libgs.dylib

.PHONY: clean
clean:
	@rm -vrd build
