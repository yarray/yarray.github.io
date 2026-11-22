TEMPLATE = resume.html5
COMMON = -s -t html5 --section-divs -f markdown+autolink_bare_uris -c resume.css

HTML_DEPS_CN = resume-cn.md $(TEMPLATE) header.html banner-cn.html work-cn.html contacts-cn.html footnote-cn.html
HTML_DEPS_EN = resume.md $(TEMPLATE) header.html banner-en.html work-en.html contacts-en.html footnote-en.html

all: index.html resume-cn.html resume-en.html

html: all

index.html: $(HTML_DEPS_CN)
	cat resume-cn.md | pandoc $(COMMON) --template=$(TEMPLATE) -V lang=zh-CN -M title="杨岸然简历" -H header.html -B banner-cn.html -A contacts-cn.html -A work-cn.html -A footnote-cn.html -o $@

# legacy URL that search engines indexed — same Chinese page
resume-cn.html: index.html
	cp index.html $@

resume-en.html: $(HTML_DEPS_EN)
	cat resume.md | pandoc $(COMMON) --template=$(TEMPLATE) -V lang=en -M title="Anran Yang — Resume" -H header.html -B banner-en.html -A contacts-en.html -A work-en.html -A footnote-en.html -o $@

ifeq ($(OS),Windows_NT)
  # on Windows
  RM = cmd //C del
else
  # on Unix
  RM = rm -f
endif

clean:
	$(RM) index.html resume-cn.html resume-en.html
