.SILENT:

.PHONEY:

.DEFAULT: build


wiki=enwiki-latest-pages-articles1


#enwiki-latest-articles1.xml.bz2:
#$(wiki).xml.bz2:
	# https://dumps.wikimedia.org/enwiki/latest/enwiki-latest-stub-articles1.xml.gz
	# https://dumps.wikimedia.org/enwiki/latest/enwiki-latest-pages-articles1.xml-p10p30302.bz2
#	curl -o $(wiki).xml.bz2 https://dumps.wikimedia.org/enwiki/latest/$(wiki).xml-p10p30302.bz2

	#curl -o $(wiki).bz2 https://dumps.wikimedia.org/enwiki/latest/`curl -s https://dumps.wikimedia.org/enwiki/latest/ | grep -o -E '$(wiki)-[^.]+.bz2' | sort -u`


#enwiki-latest-articles1.xml:
#$(wiki).xml: $(wiki).xml.bz2
#	bzip2 -k -d $(wiki).xml.bz2

data:
	@echo data

build: mycores stop data
	docker-compose up

stop:
	docker-compose down

mycores:
	- mkdir mycores
	- sudo chown 8983:8983 mycores

clean:
	- sudo rm -rf mycores
	- sudo mkdir mycores
	- sudo chmod -R a+rw mycores

commit:
	curl http://localhost:8983/solr/my_collection/update --data '<commit/>' -H 'Content-type:text/xml; charset=utf-8'

import:
	curl http://localhost:8983/solr/my_collection/update -H "Content-Type: text/xml" --data-binary @data-load.xml

delete:
	curl http://localhost:8983/solr/my_collection/update --data '<delete><query>*:*</query></delete>' -H 'Content-type:text/xml; charset=utf-8'

count:
	curl http://localhost:8983/solr/my_collection/select?q=*:*
