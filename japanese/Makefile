DC=/opt/homebrew/bin/souffle

grammar:
	$(DC) -D - $@.dl

program:
	$(DC) -F ./facts -D - $@.dl

build:
	mkdir -p ./build

build/program.cpp:
	$(DC) program.dl -g $@
	sed -i.bk "1s/^/#define USE_SQLITE 1\n/" $@

build/binary: build/program.cpp
	g++ $< -std=c++17 -o $@ \
		-I/opt/homebrew/Cellar/souffle/HEAD-b37994d/include \
		-L../lib -lsqlite3

exec: build build/binary
	./build/binary -F ./facts -D -

