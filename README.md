# Visualising and analysing network data in R

## Step 1: Create the node matrix
The code block below creates a matrix with two columns, one with the ids and the other with the names of the students. Copy, paste and run the code block below in RStudio.
```r
#rm(list=ls())
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
```

## Step 2: Record the connections of students based on the seating arrangement

The code below creates the connection data frame that captures the seating arrangement recorded in a lecture. The arrangement can be found on [Slide 12 of this presentation](https://docs.google.com/presentation/d/1iLb8AgVCaw7t4xEBdy8dU-cVZhQiCZURTyABgDLQRTo/edit#slide=id.g2bd34ca12e8_0_1). There are three more connections missing. Add them in then run this block of code in RStudio. You can find [the complete connections here](https://github.com/gqlNU/networkR/issues/1#issue-2158630532) if you get stuck.

```r
###################################################
#  the connection data frame based on the seating 
#  arrangement in the first lecture
###################################################
cnts <- read.table(header=TRUE,text='
 source target
      1      2
      3      4
      4      5
      5      6
      7      8
      8      9
#  three more connections are missing, add them in


')
```

## Step 3: create visualise the graph using <code>igraph</code>
You need to install and load the package. 

**Note:** you only need to install a package once but you need to load the packge every time you reopen RStudio. 

When the code is run successfully, you will have a graph as displayed on [Slide 13 in the lecture](https://docs.google.com/presentation/d/1iLb8AgVCaw7t4xEBdy8dU-cVZhQiCZURTyABgDLQRTo/edit#slide=id.g2bcc7878f8f_0_26).

```r
install.packages('igraph',repos='http://cran.r-project.org')
library(igraph)
```

The code below creates and plot the network.
```r
#  creating a graph 
g <- graph_from_data_frame(cnts,           # the connection matrix
                           dir=FALSE,      # this specifies an undirected graph (i.e. no arrows on the edges)
                           vertices=nodes) # the labels of the nodes come from the node matrix

#  plot the graph
plot(g,
     vertex.size=22)  # vertex.size specifies the size of the nodes
```
