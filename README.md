# colorful-path

## Overview
This software repository contains an experimental software implementation of an algrebraic algorithm based on constrained multilinear seiving for solving a set of pattern-detection problems in temporal graphs. It is a parameterised algorithm, which runs in edge-linear time and the exponential complexity is restricted to size of the multiset query. The software is written in C programming language.

This version of the source code is realeased for ICDM - 2019 submission titled "Pattern detection in large temporal graphs using algebraic fingerprints". The source code is provided for the sole purpose of ensuring the reproducibility of the experimental results. A modularised version of this software will be release as open source in the camera-ready version of this paper.

## License
The source code is subject to MIT license.

## Compilation
The source code is configured for a gcc build. Other builds are possible but it might require manual configuration of the 'Makefile'.

Use GNU make to build the software. Check 'Makefile' for more details.

`make clean all`

## Using the software
Usage: 

`./LISTER <-oracle/first> -pre <0/1/2/3> -in <input file> -seed <random seed>`

Arguments:

        -oracle/first       : <oracle> to decide the existence of a solution
                              <first> extract a solution
                             
        -pre <0/1/2/3>      : <0> no preprocessing
                              <1> preprocessing step-1
                              <2> preprocessing step-2
                              <3> preprocessing step-1 and step-2
        -in <input file>    : read from <input file>
                              read from <stdin> by default
        -seed <random seed> : random seed input

## Input file format
We use dimacs format for the input graph. An example of input graph is available in `input-graph.g`.

### Parameter line
The first line of the input graph specifies the graph parameters:

`p motif nodes edges timestamp is-dir`  

        nodes     : number of nodes
        edges     : number of edges
        timestamp : maximum number of timestamps
        is-dir    : 0, undirected graph
                    1, directed graph

### Edge line
A line starting with `e` describe an edge  
`e src dest time`    
       
        src       : vertex id of source  
        dest      : vertex id of destination  
        time      : edge timestamp  

### Shade line
A line starting with `n` decribe the color shade
`n node color`

        node      : vertex id
        color     : color id in range 1 to 30
        
### Query line
A line starting with `k` specify the query parameters
`k count <shade-list>`
 
        count      : path length
        shade-list : list of colors in query
        
## Example

`$ ./LISTER -oracle -pre 0 -in input-graph.g`  
        
        invoked as: ./LISTER -oracle -pre 0 -in input-graph.g  
        no random seed given, defaulting to 123456789  
        random seed = 123456789  
        input: n = 10, m = 28, k = 4, t = 5 [0.06 ms] {peak: 0.00GiB} {curr: 0.00GiB}  
        build query: [zero: 8.21 ms] [pos: 0.04 ms] [adj: 0.02 ms] [adjsort: 0.02 ms] [shade: 0.01 ms] done. [8.89 ms] {peak: 0.00GiB} {curr: 0.00GiB}  
        no preprocessing, default execution  
        command: run oracle  
        oracle [temppath]: 0x8555131F14296FB9 0.50 ms [0.13GiB/s, 0.01GHz] 1 {peak: 0.00GiB} {curr: 0.00GiB} -- true
        command done [0.00 ms 0.23 ms 0.23 ms]  
        grand total [12.01 ms] {peak: 0.00GiB}  
        host: cs-119  
        build: multithreaded, prefetch, k_temp_path_genf, 2 x 256-bit AVX2 [4 x GF(2^{64}) with four 64-bit words] 
        compiler: gcc 5.4.0

The line `command done [0.00 ms 0.23 ms 0.23 ms]` specifies the runtime of execution.  
Here the first time `0.00 ms` is preprocessing time, decision/extraction time is `0.23 ms` and total time is `0.23 ms`.  

The `grand total [12.01 ms] {peak: 0.00GiB}` report the total runtime, which include graph-read time, query-build time, preprocess time and decision/extraction time. The memory usage reported in this line is the peak memory usage of the total run.

The reported runtimes are in milliseconds.
