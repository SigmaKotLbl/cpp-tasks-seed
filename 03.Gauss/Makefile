include ../Makefile.inc

CXXFLAGS = -std=c++17 -I../external/eigen -I../external/lazycsv/include
LDFLAGS = -L../external/lazycsv

release: gauss_solve

gauss_solve: Gauss_main.o Gauss_solve.o util.o
	$(LD) -o $@ $^ $(LDFLAGS)

debug: gauss_solve_debug

gauss_solve_debug: Gauss_main.d.o Gauss_solve.d.o util.d.o
	$(LD) -o $@ $^ $(LDFLAGS)

utest: Gauss_test.d.o Gauss_solve.d.o util.d.o
	$(LD) -o $@ $^ $(GTEST_LIBS) $(LDFLAGS)

run_utest: utest
	./$^

tidy:
	./tidy.sh

depends:
	makedepend -f Makefile.hdrdep *.cpp *.h 2>/dev/null || true

include Makefile.hdrdep
