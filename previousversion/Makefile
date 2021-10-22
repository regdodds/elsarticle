#
# Makefile - makes $(E).pdf
#
# Put the old version of your paper into D
#
thedocument = breakselsarticle

D=previousversion/$(thedocument)

#
#         new version of your paper into E

E=$(thedocument)

#  To get differences, run:
#
#      make clean; make; make diff
#
#
#      The differences are in the file called differences.pdf


Epdf=$(E).pdf
Etex=$(E).tex
#  WWW=../../www/latex/

all:	$(Epdf)

$(Epdf):	$(E).dvi 
#	dvips -o $(D).ps $(D).dvi   #This creates a ps version of thesis from dvi file
#  pstops creates the 4up-ps 
#	pstops '4:0@.55(0,14cm)+1@.55(9.5cm,14cm)+2@.55(0,0)+3@.55(9.5cm,0)' $(Dps) 4up-$(Dps)
#  creates pdf from dvi 
#	dvipdf $(D).dvi             #This creates a pdf version of thesis from dvi file
#	chmod 644 $(Dps)
#	chmod 644 4up-$(Dps)
#	chmod 644 $(Dtex)
#  Uncommented this moves ps and 4up-ps pages to web location at $(WWW)
#	-cp 4up-$(Dps) $(WWW)
#	-cp $(Dps) $(WWW)
#	-cp $(Dtex) $(WWW)
#	gv $(Dps)
#	make clean
#	pdflatex $(E)  1> output 2>&1
#	dvips $(D).dvi
#	ps2pdf $(D).ps

$(E).dvi: $(E).tex $(E).bib 
	touch $(E).dvi # This is inherited from running latex 
	echo "$E.tex $(E).dvi $(E).tex"
	-rm -f *.aux
	pdflatex $(E) 1> junk 2>&1 
#	bibtex $(E)
	pdflatex $(E) 1> junk 2>&1
	pdflatex $(E) 1> junk 2>&1
	rm junk $(E).dvi
#	make diff
#	make diff
#	make diff


*chapter.dvi: *chapter.tex 
	echo "$E.tex $(E).dvi $(E).tex"
	echo "dummy operation on $(@)"

bibliography.dvi: acknowledgements.tex
	echo "$E.tex $(E).dvi $(E).tex"
	echo "dummy operation on $(@)"

appendix*.dvi: appendix*.tex
	echo "$E.tex $(E).dvi $(E).tex"
	echo "dummy operation on $(@)"

       #                 old      new
diff:  #                  D        E
	-latexdiff --flatten --append-safecmd=mgc --append-safecmd=mgs --append-safecmd=mgss --append-safecmd=fullcite --append-safecmd=ignore $(D).tex $(E).tex > diff.tex
	-pdflatex diff.tex 1> junk 2>&1
	-pdflatex diff.tex 1> junk 2>&1
	-pdflatex diff.tex 1> junk 2>&1
#	-okular differences.pdf
#	scp diff.pdf mac:/G/hons_MSc_and_PhDs/kuda/2021_paper2/elsevier_format/.
	rm junk

clean:
	-rm -f differences*
	-rm -f diff*
	-rm -f similarity*
	-rm -f $(D).aux
	-rm -f *chapter.aux
	-rm -f *.aux
	-rm -f *.blg
	-rm -f $(E).cre
	-rm -f $(E).crf
	-rm -f $(E).dvi
	-rm -f $(E).idx
	-rm -f $(E).ilg
	-rm -f $(E).ind
	-rm -f $(E).lof
	-rm -f $(E).log
	-rm -f $(E).lot
	-rm -f $(E).log
	-rm -f *.log
	-rm -f $(E).not
	-rm -f $(E).cb
	-rm -f $(E).ptc
	-rm -f 4up-$(E).ps
	-rm -f 4up-$(E).pdf
	-rm -f $(E).ps
#	-rm -f $(E).pdf
	-rm -f $(E).toc 
	-rm -f *.out 
	-rm -f *.spl 
	-rm les*.aux
	-rm *~
	-rm *.bak
	-rm figures/*.bak
	-mkdir ../backup
	-rm -r backup
	-cp -R * ../backup/.
	-mv ../backup .
	-rm comment.cut

cleanup:
	-rm -f $(E).pdf
	-rm -f $(E).ps
	-make clean
	-rm -rf backup

cleanall:
	-make clean
	-rm -rf backup
