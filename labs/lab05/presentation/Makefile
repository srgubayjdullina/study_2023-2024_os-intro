SRC = presentation.md
FILES += $(patsubst %.md, %.pdf, $(wildcard *.md))
FILES += $(patsubst %.md, %.html, $(wildcard *.md))

FILTERS =
OPTIONS =PDF_ENGINE =
PDF_OPTIONS =FORMAT_OPTIONS = -t beamer --slide-level=2
FILTERS += -F pandoc-crossref
PDF_ENGINE += --pdf-engine=lualatex --pdf-engine-opt=--shell-escapeOPTIONS += --number-sections
BIB_OPTIONS = --citeproc
REVEALJS_THEME = beige

%.pdf: %.md -pandoc "$<" $(FILTERS) $(PDF_ENGINE) $(PDF_OPTIONS) $(BIB_OPTIONS) $(FORMAT_OPTIONS) $(OPTIONS) -o "$@"
all: $(FILES)

%.html: %.md
	-@pandoc "$<" --embed-resources --standalone -t revealjs -V theme=$(REVEALJS_THEME) -o "$@"

all: $(FILES)

clean:
	-@rm $(FILES) *~

cleanall: clean
