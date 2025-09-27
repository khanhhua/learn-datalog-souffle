DC=/opt/homebrew/bin/souffle

grammar:
	$(DC) -D - $@.dl

program:
	$(DC) -F ./facts -D - $@.dl

build:
	mkdir -p ./build

build/program.cpp:
	$(DC) program.dl -g $@

build/binary: build/program.cpp
	g++ -I/opt/homebrew/Cellar/souffle/HEAD-b37994d/include $< -std=c++17 -o $@

exec: build build/binary
	./build/binary -F ./facts -D -

