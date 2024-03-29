# Generated automatically from Makefile.in by configure.
# Makefile for units, a program for units conversion
#
# Copyright (C) 1996, 1997, 1999 Free Software Foundation, Inc
#
# This program is free software; you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation; either version 2 of the License, or
# (at your option) any later version.
#
# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
#
# You should have received a copy of the GNU General Public License
# along with this program; if not, write to the Free Software
# Foundation, Inc., 59 Temple Place, Suite 330, Boston, MA  02111-1307  USA
#    
#
# This program was written by Adrian Mariano (adrian@cam.cornell.edu)
#

SHELL = /bin/sh
exec_prefix = ${prefix}
prefix = /Users/macbook/units174
srcdir = .

CC = gcc

INSTALL = /usr/local/bin/ginstall -c
INSTALL_DATA = ${INSTALL} -m 644
INSTALL_PROGRAM = ${INSTALL}
MAKEINFO = makeinfo
TEXI2DVI = texi2dvi
LDFLAGS = 
LIBS=  -lreadline -lncurses -lm
ANSI2KNR = 
o = .o

bindir = ${exec_prefix}/bin
infodir = ${prefix}/info
mandir = ${prefix}/man

transform=s,x,x,

# datadir must end with a / or be empty
datadir = ${prefix}/share/
#datadir =
DEFS = -DUNITSFILE=\"$(datadir)units.dat\"  -DREADLINE  
CFLAGS = -g -O2
ALL_CFLAGS = $(DEFS) $(CFLAGS) -I$(srcdir)
COMPILE = $(CC) $(ALL_CFLAGS) $(LDFLAGS)

DISTFILES = README ChangeLog units.info units.doc getopt1.c units.dvi \
   Makefile.in units.c getopt.c getopt.h units.dat units.man units.texinfo \
   configure.in configure strfunc.c COPYING Makefile.dos install-sh \
   mkinstalldirs NEWS ansi2knr.1 ansi2knr.c aclocal.m4 texi2man INSTALL \
   parse.tab.c parse.y units.h

.SUFFIXES:
.SUFFIXES: .c .o ._c ._o

.c.o:
	$(COMPILE) -c $<

.c._c:	$(ANSI2KNR)
	$(ANSI2KNR) $< > $*.tmp && mv $*.tmp $@
 
._c._o:
	@echo $(COMPILE) -c $<
	@rm -f _$*.c
	@ln $< _$*.c && $(COMPILE) -c _$*.c && mv _$*.o $@ && rm _$*.c
 
.c._o:	$(ANSI2KNR)
	$(ANSI2KNR) $< > $*.tmp && mv $*.tmp $*._c
	@echo $(COMPILE) -c $*._c
	@rm -f _$*.c
	@ln $*._c _$*.c && $(COMPILE) -c _$*.c && mv _$*.o $@ && rm _$*.c

all: units units.1

ansi2knr: ansi2knr.o
	$(COMPILE) -o ansi2knr ansi2knr.o $(LIBS)

units$o: units.c

parse.tab.c: parse.y
	bison parse.y

parse.tab$o: parse.tab.c

OBJECTS = units$o
$(OBJECTS): $(ANSI2KNR)

units: $(OBJECTS) parse.tab.o getopt.o getopt1.o 
	$(CC) $(LDFLAGS) -o units $(OBJECTS) parse.tab.o getopt.o getopt1.o  $(LIBS)

install: units units.dat install-doc
	$(srcdir)/mkinstalldirs $(bindir) $(datadir)
	$(INSTALL_PROGRAM) units $(bindir)/`echo units|sed '$(transform)'`
	$(INSTALL_DATA) $(srcdir)/units.dat $(datadir)units.dat

install-strip: units units.dat install-doc
	$(INSTALL_PROGRAM) -s units $(bindir)/`echo units|sed '$(transform)'`
	$(INSTALL_DATA) $(srcdir)/units.dat $(datadir)units.dat

install-doc: install-man install-info

install-man: units.1
	$(srcdir)/mkinstalldirs $(mandir)/man1
	$(INSTALL_DATA) units.1 $(mandir)/man1/`echo units|sed '$(transform)'`.1

units.man: units.texinfo texi2man
	./texi2man units.texinfo > units.man

units.1: units.man
	sed s!@DATAFILE@!$(datadir)units.dat! $(srcdir)/units.man > units.1

install-info: $(infodir)/units.info

$(infodir)/units.info: units.info
	$(srcdir)/mkinstalldirs $(infodir)
# There may be a newer info file in . than in srcdir.
	-if test -f units.info; then d=.; \
	   else d=$(srcdir); fi; \
	$(INSTALL_DATA) $$d/units.info $@; \
# Run install-info only if it exists.
# Use `if' instead of just prepending `-' to the
# line so we notice real errors from install-info.
# We use `$(SHELL) -c' because some shells do not
# fail gracefully when there is an unknown command.
	if test -f $(infodir)/dir; then \
	  if $(SHELL) -c 'install-info --version' \
	     >/dev/null 2>&1; then \
	     install-info --dir-file=$(infodir)/dir \
	               $(infodir)/units.info; \
	  else true; fi \
	else true; fi

Makefile: Makefile.in config.status
	./config.status

uninstall: 
	-rm -f $(bindir)/`echo units|sed '$(transform)'` \
	       $(mandir)/man1/`echo units|sed '$(transform)'`.1 \
	       $(infodir)/units.info $(datadir)units.dat
	@if test -f $(infodir)/dir; then \
	  echo You may need to remove units.info from $(infodir)/dir; \
	else true; fi

clean mostlyclean: 
	-rm -f *.o units units.fn units.ky units.pg units.tp units.vr \
             units.log units.dvi units.1 units.cp distname .chk units.toc \
	     units.aux units.cps units.op $(ANSI2KNR) *._o *._c

distclean: clean
	-rm -f config.* Makefile TAGS

maintainer-clean: clean
	-rm -f units.doc units.info units.dvi units-*.tar.gz parse.tab.c

dist: $(DISTFILES)
	echo units-`sed -n -e '/#.*VERSION/s/.*"\(.*\)"/\1/gp' \
	    $(srcdir)/units.c` > distname
	-rm -r `cat distname` `cat distname`.tar `cat distname`.tar.gz
	mkdir `cat distname`
	dst=`cat distname`; for f in $(DISTFILES); do \
	   ln $(srcdir)/$$f $$dst/$$f || { echo copying $$f; \
	          cp -p $(srcdir)/$$f $$dst/$$f ; } \
	done
	chmod 777 `cat distname`
	tar cf `cat distname`.tar `cat distname`
	gzip `cat distname`.tar
	-rm -rf `cat distname` distname

dvi: units.dvi

units.dvi: units.texinfo
	$(TEXI2DVI) $(srcdir)/units.texinfo

info: units.info

units.info: units.texinfo
	$(MAKEINFO) $(srcdir)/units.texinfo

units.doc: units.1
	nroff -man $(srcdir)/units.1 | col -b > units.doc

doc: units.dvi units.info units.doc

check: all
	@echo Checking units
	@./units -f $(srcdir)/units.dat \
	      '(((square(kiloinch)+2.84m2) /0.5) meters^2)^(1|4)' m \
	    | sed -n -e 's/	\* //p' > .chk
	@if [ "`cat .chk`" = 6 ]; then echo Units seems to work; \
	   else echo Something is wrong: units failed the check: ;cat .chk; fi
	@rm -f .chk

configure: configure.in
	autoconf

TAGS: units.c
	etags $(srcdir)/units.c $(srcdir)/parse.y


smalldist: units.c units.h parse.y parse.tab.c
	echo units-`sed -n -e '/#.*VERSION/s/.*"\(.*\)"/\1/gp' \
	    $(srcdir)/units.c` > distname
	-rm -r `cat distname` `cat distname`.tar `cat distname`.tar.gz
	tar cf `cat distname`.tar units.c units.h  parse.y  parse.tab.c\
	   getopt1.c getopt.c getopt.h
	gzip `cat distname`.tar

# Tell versions [3.59,3.63) of GNU make not to export all variables.
# Otherwise a system limit (for SysV at least) may be exceeded.
.NOEXPORT:
