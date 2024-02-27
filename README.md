# networkR

```r
rm(list=ls())
library(igraph)

#####################
#  the node matrix
#####################
nodes <- read.table(header=TRUE,text='
   id	 name
    1     Dom
    2   Grace
    3    Adam
    4     Bob
    5   Manny
    6   Steve
    7     Ken
    8 Queenie
    9    Noah
   10    Cath
   11     Roy
   12   Ellie
   13     Ivy
   14     Pat
   15  Finley
   16   Orion
   17   Layla
   18    Jack
   19     Tim
   20   Helen')


###################################################
#  the connection data frame based on the seating 
#  arrangement in the first lecture
###################################################
cnts1 <- read.table(header=TRUE,text='
   source target
        1      2
	3      4
        4      5
        5      6
        7      8
        8      9
        9     10
       10     11
       11     12')

#  creating a graph 
g1 <- graph_from_data_frame(cnts1,dir=FALSE,vertices=nodes)

#  plot the graph created
plot(g1,vertex.size=22)
```
