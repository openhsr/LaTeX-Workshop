snip.pdf: snip.tex
	xelatex --interaction=batchmode --halt-on-error --shell-escape $<

cont: snip.pdf
	xdg-open $<
	ls *.tex | entr -d make
