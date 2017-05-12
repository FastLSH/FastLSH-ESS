
<img src="https://cloud.githubusercontent.com/assets/11495951/24863839/066e138c-1e35-11e7-914f-6fa56a334d2f.png" alt="FastLSH_LOGO" style="width: 100px;"/>

# FastLSH-ESS
It contains the FastLSH core engine. After compilation, two executable files `FastLSH` and `ParaGen` will be generated.

## Functions
* Basic FastLSH exectuion flow
* Multithread execution

## Compilation 
    >cmake .
    >make

## Change Parameters
There are two ways to change parameters
1. edit arguments file `./FastLSH_Arguments`  
`
#This is the file for passing the arguments to FastLSH.
#Use '#' for comment, try not to put extra line in between.
#Make sure you name it "FastLSHargs" and put it in the same directory of your FastLSH exec file.
#
#N<int>: number of points(lines,rows) in the dataset
1000
#Q<int>: number of points(lines,rows) in the queryset
1000
#D<int>: number of dimensions (columns)
57
#L<int>: number of group hash 
200
#K<int>: number of hash functions in each group hash
1
#W<double>: bucket width
1.2
#T<int>: threshold
10
#Compute Mode(0/1): 0-normal((g-collisionmatrix-> candidate)need more memory)   1-quickMode(need less memory, the collision matrix won't be generated
1
#Thread Mode (0-3): 0-singleThread 1-openMP, 2-stdthread 3-pthread
2
#useHDFS (Y/N): Whether to load from HDFS 
N
#Input Path for datasetN:  the file path to load datasetN from, if use HDFS, use the HDFS path. 
./tests/dataset/dataset1000NoIndex.csv
#Input Path for datasetQ:  the file path to load datasetQ from, if use HDFS, use the HDFS path. 
./tests/dataset/dataset1000NoIndex.csv
#Output Path: the file path to save the candidateSet to
candidate.csv
`

    
2. Input parameters during execution

## Execution
    ./FastLSH
    
## Generate Parameters
    ./ParaGen





