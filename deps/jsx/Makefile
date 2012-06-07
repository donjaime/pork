
JOBS:=4

all:

setup:
	npm install
	perl web/setup.pl

# e.g. make test JOBS=2
test:
	prove --jobs "$(JOBS)" t/*.t t/*/*.jsx

optimize-bench:
	prove xt/optimize-bench/*.jsx

web:
	perl web/build.pl
	bin/jsx --enable-source-map --output fib.js example/fib.jsx
	mkdir -p web/source-map
	mv fib.js web/source-map/
	mv fib.js.mapping web/source-map/
	mkdir -p web/source-map/example
	cp example/fib.jsx web/source-map/example/

server:
	node web/server.js

# for authors
web.jsx:
	idl2jsx/build.pl
	idl2jsx/maketest.pl > t/lib/010.web.jsx
	bin/jsx --test t/lib/010.web.jsx

.PHONY: test web server
