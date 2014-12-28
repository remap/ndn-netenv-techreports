# change this to the file name of the paper 
PRJ = ndn-netenv-Open_mHealth
LATEX_OPT = --shell-escape

DVIOPT = -P cmz -t letter -G0

all : ${PRJ}.pdf 

#${PRJ}.dvi : *.tex *.bib 
#	latex ${PRJ}; bibtex ${PRJ}; latex ${PRJ}; latex ${PRJ}
${PRJ}.pdf : *.tex *.bib 
	pdflatex ${LATEX_OPT} ${PRJ} && (ls bu*.aux | xargs -n 1 bibtex) ; bibtex ${PRJ}.aux ; pdflatex ${LATEX_OPT} ${PRJ} ; pdflatex ${LATEX_OPT} ${PRJ} 

#${PRJ}.ps : ${PRJ}.dvi
#	dvips ${DVIOPT} -o ${PRJ}.ps ${PRJ}.dvi
#
#${PRJ}.pdf : ${PRJ}.ps
#	ps2pdf ${PRJ}.ps ${PRJ}.pdf
#
#dvi : ${PRJ}.dvi
#
#ps : ${PRJ}.ps
#
#pdf : ${PRJ}.pdf

#view : ${PRJ}.dvi
#	xdvi -s 0 ${PRJ}.dvi &

#viewps : ${PRJ}.ps
#	open ${PRJ}.ps &

view : ${PRJ}.pdf
	open ${PRJ}.pdf &

# change this to include what should be in the tarball,  use --exclude for exclusion.
pack : clean
	cd ..; /bin/rm -f ${PRJ}.tgz; tar -hzcf ${PRJ}.tgz ${PRJ} 

clean:
	/bin/rm -f *.toc *.aux ${PRJ}.bbl *.blg *.log *.dvi *~* *.bak *.out

distclean:
	/bin/rm -f *.toc *.aux ${PRJ}.bbl *.blg *.log ${PRJ}.dvi ${PRJ}.ps ${PRJ}.pdf *~* *.bak *.out

# watch the options to dvips, which extract differnt pages from the dvi file. 
cut : ${PRJ}.pdf
	pdfjam -o ${PRJ}-toc.pdf $< 1-2
	pdfjam -o ${PRJ}-summary.pdf $< 3
	pdfjam -o ${PRJ}-description.pdf $< 4-28
	pdfjam -o ${PRJ}-references.pdf $< 29-

