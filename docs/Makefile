# Minimal makefile for Sphinx documentation
#

# You can set these variables from the command line, and also
# from the environment for the first two.
SPHINXOPTS    ?=
SPHINXBUILD   ?= sphinx-build
SOURCEDIR     = source
BUILDDIR      = build

# Put it first so that "make" without argument is like "make help".
help:
	@$(SPHINXBUILD) -M help "$(SOURCEDIR)" "$(BUILDDIR)" $(SPHINXOPTS) $(O)

.PHONY: help Makefile

# Catch-all target: route all unknown targets to Sphinx using the new
# "make mode" option.  $(O) is meant as a shortcut for $(SPHINXOPTS).
%: Makefile
	@$(SPHINXBUILD) -M $@ "$(SOURCEDIR)" "$(BUILDDIR)" $(SPHINXOPTS) $(O)
	echo "Completed HTML text generation, run 'make view'"

clean:
	rm -rf build
	echo "Deleted directory build/"

	rm -rf source/modules
	echo "Deleted directory source/modules"
	echo "Completed HTML text generation, run 'make ibm_zos_cics'"

ibm_zos_cics:
	mkdir build
	mkdir -p source/modules
	# mv ../plugins/modules/__init__.py ../plugins/modules/__init__.py.skip
	ansible-doc-extractor --template templates/module.rst.j2 source/modules ../plugins/modules/*.py
	echo "Completed restructured text generation, run 'make html'"
	# mv ../plugins/modules/__init__.py.skip ../plugins/modules/__init__.py
view:
	open build/html/index.html