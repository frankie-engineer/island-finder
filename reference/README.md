# Solving Graph Problems Practice Part 1

In this practice, you will be solving a variation of the island size problem - 
counting the total number of islands in a graph.

Like most graph problems, you will be following these three steps to solve it:

1. Identify and define the type of graph
2. Implement the `getNeighbors` function
3. Traverse the graph

In this part, you will be implementing steps 1 and 2.

## Setup

1. Clone the starter
2. Install all packages with `npm install`
3. Read the instructions and specs to understand the problem
4. Implement the code until tests are green

## The problem

Given a binary matrix, return the number of islands found in the graph. An 
island consists of 1s that are adjacent in the northwest, north, northeast, east
southeast, south, southwest, and west directions. (All directions, diagonals 
included.) The following example has two islands.

Note that this is **not** an adjacency matrix!.

```js
matrix = [
    [1,0,1,0,1],
    [0,1,0,0,1],
    [1,0,0,1,1],
]

countIslands(matrix);  // 2
```

`countIslands(matrix)` takes in one argument: a binary matrix. It will return 
the number of islands consisting of adjacent 1s.


**Tip:** When working with 2d arrays, always use `row` and `col`, or row and
column, to access items in the matrix.  It's backwards from what you're used to!
If you try to use `y` and `x`, you **will** get confused and reference them out
of order, as `x` and `y`.

## Step 1: Identify and define the type of graph

There is no code to this part but take time to identify and define the graph.

1. Is this graph directed or undirected?
2. Is this graph cyclic or acyclic?
3. What are the nodes and what are the edges?
4. What kind of traversal or search will you need to solve this?

## Step 2: Implement the `getNeighbors` function

In order to traverse any graph, you need to implement the `getNeighbors`
function. In this graph, the nodes are coordinates containing 1s and the
neighbors are the adjacent 1s.

`getNeighbors(row, col, matrix)` takes in a row, column and matrix and returns
coordinates of all the adjacent squares containing 1s.

```js
[[1,1,1,0,0],
 [0,1,1,0,1],
 [0,1,1,0,1]]
```

For the above matrix, `getNeighbors(1, 1, matrix)` would return `[[0, 0], [0, 1]
, [0, 2], [1, 2], [2, 1], [2, 2]]` since the neighbors of row 1, col 1 are 
`[0, 0]`, `[0, 1]`, `[0, 2]`, `[1, 0]`,`[1, 2]`, `[2, 0]`, `[2, 1]`, and 
`[2, 2]`.  All of these contain 1s except for `[1, 0]` and `[2, 0]` which are 
excluded.

Read the specs in `test/island-spec.js` for more details.

At the end of this phase, you should be passing the first three test specs. You
will work on the last two specs in phase 2, explained in README-pt2.md.

# Solving Graph Problems Practice Part 2

In this practice, you will finish the island counting problem by using the
`getNeighbors` function from part 1 to count islands.

Like most graph problems, you will be following these three steps to solve it:

1. Identify and define the type of graph
2. Implement the `getNeighbors` function
3. Traverse the graph

You have completed steps 1 and 2 in part 1. In this part, you will finish step 
3.

## Setup

1. Continue working in the starter from phase 1
2. Install all packages with `npm install`
3. Read the instructions and specs to understand the problem
4. Implement the code until tests are green

## The problem (recall)

Given a binary matrix, return the number of islands found in the graph. An 
island consists of 1s that are adjacent in the northwest, north, northeast, east
southeast, south, southwest, and west directions. (All directions, diagonals 
included.) The following example has two islands.

```js
matrix = [
    [1,1,1,0,1],
    [0,0,0,0,1],
    [1,0,0,1,0],
]

countIslands(matrix);  // 3
```

`countIslands(matrix)` takes in one argument: a binary matrix. It will return 
the number of islands consisting of adjacent 1s.

## Step 3: Traverse the graph

Now that you have the getNeighbors function, you can traverse the graph looking
for islands. You should iterate through each index in the matrix one at a time
looking for 1s, finding all connected 1s, and marking them all as visited. You
should increment your island count every time you find a new "undiscovered" 1
that was not part of another island.

Pseudocode for a depth-first traversal is included in the starter file.

**hint** it may help to _stringify_ coordinates before adding them to the
visited set. Also, note that coordinates are unique _pairs_ of values and should
be stringified as such. (Meaning that you should ensure that pairs like row 1,
column 11 and row 11, column 1 are not stringified to be the same string.)
