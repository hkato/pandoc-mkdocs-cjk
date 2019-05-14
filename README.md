# pandoc-mkdocs-cjk

[![](https://images.microbadger.com/badges/image/katojp/pandoc-mkdocs-cjk.svg)](https://microbadger.com/images/katojp/pandoc-mkdocs-cjk "Get your own image badge on microbadger.com")
[![](https://images.microbadger.com/badges/version/katojp/pandoc-mkdocs-cjk.svg)](https://microbadger.com/images/katojp/pandoc-mkdocs-cjk "Get your own version badge on microbadger.com")

CJK(Chinese-Japanese-Korean) support version of [pandoc-mkdocs](https://hub.docker.com/r/silentstorm/pandoc-mkdocs/)

## Example

A .gitlab-ci using this image could look like this:

```YAML
image: katojp/pandoc-mkdocs-cjk
    
build_pdf:
  stage: build
  script:
  - mkdocscombine -o combined.md
  - pandoc --toc -V documentclass=bxjsarticle -V classoption=pandoc,ja=standard --latex-engine=xelatex -f markdown+grid_tables+table_captions -o document.ja.pdf combined.md
  artifacts:
    paths:
    - "document.ja.pdf"
    
build_html:
  stage: build
  script:
  - mkdocs build
  artifacts:
    paths:
    - "site/"
```
