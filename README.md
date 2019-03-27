# Whitepaper

This is the whitepaper for the high-level purpose of Token Ibis as an
idea and movement.

# Content

This document is written with emacs org mode and automatically
compiled into either latex->pdf for human readability or
semi-automatically into ascii for reference on the bitcoin blockchain.

Only the original org file, the latex class, and references are
tracked on git. However, all artifacts and build products are kept on
git lfs for quick access.

# Build

The build is guaranteed to work with the following setup:

- texlive (apt package)
- emacs26 (apt package)
- org-ref (emacs package)

Finally, here is the relevant emacs.d configuration:

```elisp
  (with-eval-after-load 'ox-latex
    (add-to-list 'org-latex-classes
                 '("custom"
                   "\\documentclass{custom}"
		   ("\\section{%s}" . "\\section*{%s}")
		   ("\\subsection{%s}" . "\\subsection*{%s}")
		   ("\\subsubsection{%s}" . "\\subsubsection*{%s}")
		   ("\\paragraph{%s}" . "\\paragraph*{%s}")
		   ("\\subparagraph{%s}" . "\\subparagraph*{%s}"))))
  (setq org-latex-pdf-process
	'("pdflatex -interaction nonstopmode -output-directory %o %f"
          "bibtex %b"
          "pdflatex -interaction nonstopmode -output-directory %o %f"
          "pdflatex -interaction nonstopmode -output-directory %o %f"))
```
