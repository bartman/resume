XML=resume.xml
#example1.xml example2.xml

HTML=$(XML:.xml=.html)
FO=$(XML:.xml=.fo)
TEXT=$(XML:.xml=.text)

all: index.html html text

html: ${HTML} ;
fo:   ${FO} ;
text: ${TEXT} ;

XALAN=`pwd`/xalan

%.html: %.xml
	java -cp ${XALAN}/xalan.jar org.apache.xalan.xslt.Process -in $< -xsl xsl/html.xsl -out $@

%.fo: %.xml
	java -cp ${XALAN}/xalan.jar org.apache.xalan.xslt.Process -in $< -xsl xsl/fo.xsl -out $@

%.text: %.xml
	java -cp ${XALAN}/xalan.jar org.apache.xalan.xslt.Process -in $< -xsl xsl/text.xsl -out $@

index.html: resume.html
	ln -s resume.html index.html

clean:
	rm -f *~ *.html *.fo *.text

#xsl/html.xsl:
#	cd xsl ; wget http://xmlresume.sourceforge.net/xsl/html.xsl
