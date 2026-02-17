# Makefile for "Gelar Sang Artisan" Book
# Engineered to keep the workspace pristine.

DOC=main
BUILDDIR=dist
OUTDIR=bin
OUTNAME=titled-artisans-prince.pdf
LATEX=pdflatex
LATEXFLAGS=-interaction=nonstopmode -halt-on-error -output-directory=$(BUILDDIR)

# Default run
all: pdf

# Create necessary directories
dirs:
	@mkdir -p $(BUILDDIR) $(OUTDIR)

# Main build process
pdf: dirs
	@echo "Building the artifact..."
	$(LATEX) $(LATEXFLAGS) $(DOC).tex
	# Uncomment next line if you have bibliography/references
	# bibtex $(BUILDDIR)/$(DOC) 
	$(LATEX) $(LATEXFLAGS) $(DOC).tex
	$(LATEX) $(LATEXFLAGS) $(DOC).tex
	@cp -f $(BUILDDIR)/$(DOC).pdf $(OUTDIR)/$(OUTNAME)
	@echo "DONE. Artifact deployed to: $(OUTDIR)/$(OUTNAME)"

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
