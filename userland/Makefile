# This is where you can add project directories to the build-chain
PROJECTS:=arguments cat echo serviced ls mesg mkdir sh shutdown syslogd touch write_test rm sigtest
ALLPROJECTS:=$(PROJECTS:%=all-%)
CLEANPROJECTS:=$(PROJECTS:%=clean-%)
INSTALLPROJECTS:=$(PROJECTS:%=install-%)

.PHONY: $(ALLPROJECTS) $(CLEANPROJECTS) $(INSTALLPROJECTS) all clean install

export DESTDIR
export CC=$(TARGET)-gcc
export LD=$(CC)

all: $(ALLPROJECTS)

clean: $(CLEANPROJECTS)

install: $(INSTALLPROJECTS)

$(ALLPROJECTS):
	$(MAKE) -C $(@:all-%=%) all

$(CLEANPROJECTS):
	$(MAKE) -C $(@:clean-%=%) clean
	
$(INSTALLPROJECTS):
	mkdir -p $(DESTDIR)/bin
	$(MAKE) -C $(@:install-%=%) install
