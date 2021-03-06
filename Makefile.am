SUBDIRS = doc
EXTRA_DIST = Doxyfile trees/*tax* src/Makefile version src/boost src/checkfiles.sh bootstrap example/eg* doc/*.pdf doc/*.tex doc/manual.bbl doc/manual.blg 
#DISTFILES = $(DIST_COMMON) $(DIST_SOURCES) $(TEXINFOS) $(EXTRA_DIST)
distdir = $(PACKAGE)-$(VERSION)

bin_PROGRAMS = hybrid-Lambda
PROG = HYBRID-LAMBDA
check_PROGRAMS = hybrid-Lambda_dbg hybrid-Lambda_prof unit_tests
TESTS = unit_tests

common_flags = -O3 -g -std=c++0x -I src/ -I src/boost
hybrid_Lambda_CXXFLAGS = -DNDEBUG $(common_flags)#options for not showing debug messages.
hybrid_Lambda_dbg_CXXFLAGS = $(common_flags)
hybrid_Lambda_prof_CXXFLAGS = $(common_flags) -DNDEBUG -pg #options for not showing debug messages. -fpermissive

shared_src = src/hybridLambda.cpp \
				 src/node.cpp \
				 src/net.cpp \
				 src/sim_gt.cpp \
				 src/freq/freq.cpp \
				 src/plot/figure.cpp \
				 src/regular_math.cpp \
				 src/fastfunc.cpp \
				 src/random_generator.cpp \
				 src/mersenne_twister.cpp

debug_SOURCES = src/debug/net_debug.cpp \
			    src/debug/node_debug.cpp

hybrid_Lambda_SOURCES = $(shared_src) src/main.cpp
hybrid_Lambda_dbg_SOURCES = $(shared_src) $(debug_SOURCES) src/main.cpp
hybrid_Lambda_prof_SOURCES = $(shared_src) src/main.cpp

unit_tests_SOURCES = $(shared_src) tests/unittest/test_hybridLambda.cpp tests/unittest/test_simGt.cpp tests/unittest/test_runner.cpp

unit_tests_CXXFLAGS = -DUNITTEST -DNDEBUG -std=c++0x -I src/
unit_tests_LDADD= -lcppunit -ldl

include_HEADERS = src/sim_gt.hpp src/plot/figure.hpp src/freq/freq.hpp src/hybridLambda.hpp src/node.hpp src/net.hpp src/global.hpp \
				  src/fastfunc.hpp  src/hybridLambda.hpp src/random_generator.hpp src/global.hpp src/mersenne_twister.hpp \
				  src/node.hpp  src/regular_math.hpp

