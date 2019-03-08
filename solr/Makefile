.SILENT:

.PHONEY:

.DEFAULT: build


wiki=enwiki-latest-pages-articles1


#enwiki-latest-articles1.xml.bz2:
$(wiki).xml.bz2:
	# https://dumps.wikimedia.org/enwiki/latest/enwiki-latest-stub-articles1.xml.gz
	# https://dumps.wikimedia.org/enwiki/latest/enwiki-latest-pages-articles1.xml-p10p30302.bz2
	curl -o $(wiki).xml.bz2 https://dumps.wikimedia.org/enwiki/latest/$(wiki).xml-p10p30302.bz2
	#curl -o $(wiki).bz2 https://dumps.wikimedia.org/enwiki/latest/`curl -s https://dumps.wikimedia.org/enwiki/latest/ | grep -o -E '$(wiki)-[^.]+.bz2' | sort -u`


#enwiki-latest-articles1.xml:
$(wiki).xml: $(wiki).xml.bz2
	bzip2 -k -d $(wiki).xml.bz2

build: mycores stop $(wiki).xml
	docker-compose up

stop:
	docker-compose down

mycores:
	- mkdir mycores
	- sudo chown 8983:8983 mycores
