##
 # This file is part of an experimental software implementation of
 # temporal-pattern search utilizing the constrained multilinear
 # sieving framework;
 #
 #  "Pattern detection in large temporal graphs using algebraic fingerprints",
 #   A. Author(s), ICDM submission, 2019.
 #
 # This experimental source code is supplied to accompany the
 # aforementioned paper.
 #
 # The source code is configured for a gcc build to a native
 # microarchitecture that must support the AVX2 and PCLMULQDQ
 # instruction set extensions. Other builds are possible but
 # require manual configuration of 'Makefile' and 'builds.h'.
 #
 # The source code is subject to the following license.
 #
 # The MIT License (MIT)
 #
 # Copyright (c) 2019 A. Author(s)
 #
 # Permission is hereby granted, free of charge, to any person obtaining a copy
 # of this software and associated documentation files (the "Software"), to deal
 # in the Software without restriction, including without limitation the rights
 # to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
 # copies of the Software, and to permit persons to whom the Software is
 # furnished to do so, subject to the following conditions:
 #
 # The above copyright notice and this permission notice shall be included in
 # all copies or substantial portions of the Software.
 #
 # THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
 # IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
 # FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
 # AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
 # LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
 # OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN
 # THE SOFTWARE.
 #
##

MAKE = make
CC = gcc
CFLAGS = -O5 -Wall -march=native -std=c99 -fopenmp

all: LISTER

LISTER: lister.c builds.h gf.h ffprng.h
	$(CC) $(CFLAGS) -DLISTER_DEFAULT -o LISTER lister.c

clean:	
	rm -f *.o *.a *~ LISTER
