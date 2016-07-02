
test: diff

run:
	rm -rf tmp
	mkdir tmp
	cp -ip 01-before tmp/.
	../sh-frcode def-vars tmp/01-before > tmp/decode.sh
	bash tmp/decode.sh > tmp/02-after

diff: run
	diff tmp/01-before tmp/02-after

clean:
	rm -rf tmp
