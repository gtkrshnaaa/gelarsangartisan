# Makefile for "Gelar Sang Artisan" Book
# Engineered to keep the workspace pristine.

DOC=main
BUILDDIR=dist
OUTDIR=bin
OUTNAME=gelar-sang-artisan.pdf
LATEX=pdflatex
LATEXFLAGS=-interaction=nonstopmode -halt-on-error -output-directory=$(BUILDDIR)

# Default run
all: pdf

# Create necessary directories
dirs:
	@mkdir -p $(BUILDDIR) $(OUTDIR)

# Main build targets
pdf: ebook print

ebook: dirs
	@echo "Building E-book artifact (A5 Digital)..."
	$(LATEX) $(LATEXFLAGS) $(DOC).tex
	$(LATEX) $(LATEXFLAGS) $(DOC).tex
	$(LATEX) $(LATEXFLAGS) $(DOC).tex
	@cp -f $(BUILDDIR)/$(DOC).pdf $(OUTDIR)/gelar-sang-artisan-ebook.pdf
	@echo "DONE. E-book deployed to: $(OUTDIR)/gelar-sang-artisan-ebook.pdf"

print: dirs
	@echo "Building Print artifact (A5 Standard)..."
	$(LATEX) $(LATEXFLAGS) "\def\isprint{1} \input{$(DOC).tex}"
	$(LATEX) $(LATEXFLAGS) "\def\isprint{1} \input{$(DOC).tex}"
	$(LATEX) $(LATEXFLAGS) "\def\isprint{1} \input{$(DOC).tex}"
	@cp -f $(BUILDDIR)/$(DOC).pdf $(OUTDIR)/gelar-sang-artisan-print-a5.pdf
	@echo "DONE. Print version deployed to: $(OUTDIR)/gelar-sang-artisan-print-a5.pdf"

# Dependencies (Ubuntu/Debian) - One time setup
install:
	@echo "Provisioning LaTeX environment..."
	sudo apt update && sudo apt install -y \
	texlive-latex-base texlive-latex-extra \
	texlive-fonts-recommended texlive-fonts-extra \
	texlive-science texlive-bibtex-extra

# Cleaning the build artifacts
clean:
	@echo "Cleaning temporary files in $(BUILDDIR)..."
	@rm -f $(BUILDDIR)/*.aux $(BUILDDIR)/*.log $(BUILDDIR)/*.toc \
	$(BUILDDIR)/*.out $(BUILDDIR)/*.lof $(BUILDDIR)/*.lot \
	$(BUILDDIR)/*.bbl $(BUILDDIR)/*.blg

# Deep clean (reset project)
reset: clean
	@echo "Removing output directories..."
	@rm -rf $(BUILDDIR) $(OUTDIR)

.PHONY: all dirs pdf install clean reset
