## Process this file with automake to produce Makefile.in

ACLOCAL_AMFLAGS = -I m4

AM_CPPFLAGS = $(LUA_INCLUDE)

lualib_LTLIBRARIES = curses.la

curses_la_SOURCES = lcurses.c
curses_la_LDFLAGS = -module $(CURSES_LIB)

release: distcheck
	git diff --exit-code && \
	git tag -a -m "Release tag" rel-`echo $(VERSION) | sed -e 's/\./-/g'` && \
	git push && \
	woger lua-l lcurses lcurses "release $(VERSION)" "Lua bindings for curses" release-notes-$(VERSION)
