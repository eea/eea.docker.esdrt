define HELP=
	All done, now run:
	$ docker-compose up -d
	$ docker-compose exec plone bash
	$ ./bin/standalone fg
endef


all: dirs git perms help

dirs:
	mkdir -p ./src ./data/filestorage ./data/blobstorage

git:
	git clone git@github.com:eea/esdrt.theme.git ./src/esdrt.theme
	git clone git@github.com:eea/esdrt.content.git ./src/esdrt.content

perms:
	sudo setfacl  -R -m u:500:rwX src/ data/
	sudo setfacl -dR -m u:500:rwX src/ data/

help:
	$(info $(HELP))

