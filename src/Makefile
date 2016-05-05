LIBNAME:=cmdliner
VERSION:=0.9.8
DESCRIPTION:=Declarative definition of command line interfaces for OCaml
REQUIRES:=
OPT:=ocamlfind ocamlopt -g
OCAMLC:=ocamlfind ocamlc -g 
LIBSRC:=\
	cmdliner.mli cmdliner.ml

all: META cmdliner.cma cmdliner.cmxa

cmdliner.cma: cmdliner.mli cmdliner.ml
	$(OCAMLC) -o $@ -a $(LIBSRC)

cmdliner.cmxa: cmdliner.mli cmdliner.ml
	$(OPT) -o $@ -a $(LIBSRC)

META: Makefile
	echo "description = \"$(DESCRIPTION)\"" > $@
	echo "version = \"$(VERSION)\"" >> $@
	echo "archive(byte) = \"$(LIBNAME).cma\"" >> $@
	echo "archive(native) = \"$(LIBNAME).cmxa\"" >> $@
#	echo "requires = \"$(REQUIRES)\"" >> $@

install:
	ocamlfind install $(LIBNAME) *.a *.cm[ioxa] *.cmx[as] cmdliner.mli META

uninstall:
	ocamlfind remove $(LIBNAME)

reinstall:
	make uninstall
	make install

clean:
	rm -f *.cmi *.cmo *.cmx *.cma *.a *.cmxa *.o

rebuild:
	make clean
	make all
