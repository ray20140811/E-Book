ORG_FILES := $(wildcard *.org)
MD_FILES := $(patsubst %.org, %.md, $(ORG_FILES))

all: $(MD_FILES)

%.md: %.org
	emacs $< --batch -f org-md-export-to-markdown -f save-buffer

.PHONY: clean
clean:
	rm -f $(MD_FILES)


