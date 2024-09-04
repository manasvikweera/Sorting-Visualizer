# suduko-solver

suduko_solver Given a partially filled 9×9 2D array ‘grid[9][9]’, the goal is to assign digits (from 1 to 9) to the empty cells so that every row, column, and subgrid of size 3×3 contains exactly one instance of the digits from 1 to 9.

# Approach:

Like all other Backtracking problems, Sudoku can be solved by one by one assigning numbers to empty cells. Before assigning a number, check whether it is safe to assign. Check that the same number is not present in the current row, current column and current 3X3 subgrid. After checking for safety, assign the number, and recursively check whether this assignment leads to a solution or not. If the assignment doesn’t lead to a solution, then try the next number for the current empty cell. And if none of the number (1 to 9) leads to a solution, return false and print no solution exists.

# Algorithm:

Create a function that checks after assigning the current index the grid becomes unsafe or not. Keep Hashmap for a row, column and boxes. If any number has a frequency greater than 1 in the hashMap return false else return true; hashMap can be avoided by using loops. Create a recursive function that takes a grid. Check for any unassigned location. If present then assign a number from 1 to 9, check if assigning the number to current index makes the grid unsafe or not, if safe then recursively call the function for all safe cases from 0 to 9. if any recursive call returns true, end the loop and return true. If no recursive call returns true then return false. If there is no unassigned location then return true. Complexity Analysis:

Time complexity: O(9^(nn)). For every unassigned index, there are 9 possible options so the time complexity is O(9^(nn)). The time complexity remains the same but there will be some early pruning so the time taken will be much less than the naive algorithm but the upper bound time complexity remains the same.

Space Complexity: O(n*n). To store the output array a matrix is needed.


## CLI-Binary-Tree-Visualisation
A program that visualises a binary tree in Command Line Interface

# Goal Representation

              5                                 1 spaces (assume)


              5
             / \
            4   7                               3 spaces



              5
       (e)  /   \
          4  (b)  7                             7 spaces
         / \     / \
        5   4   6   8                           3 spaces





    (a)         9        (a)                      14 - 10         6 - 4        2 - 1      (2^i - 2) - 2^(i-2)
            /       \                                             11           5          (2^(i+1) - 1) - 2^(i-1)
        5               7                         15 spaces
      /(c)\    (d)    /   \
     4     7         8     9                     7 spaces
    / \     / \     / \     / \
    5  4   6   8   4   8   4   1                   3 spaces



# Distances within various components

    (a) pow(2, height - level) - 2

    (b) pow(2, height - level + 1) - 1
                    (or)
        pow(2, height - level + 1) - digits

        where, digits is the no of digits of the previous node value to make up for extra digits

    (c)  pow(2, height - level - 1) - 1

    (d) pow(2, height - level + 1) - pow(2, height - level - 1) - 1

    (e) pow(2, height - level) - pow(2, height - level - 2) - 2


 # Algorithm    
    queue nodes and edges initially empty
    push head into nodes

    for i = 0 to height - 1 :
            push nodes.front into edges
            temp <- pop(nodes)
            apply (a)
            if temp != NULL print value
            else print " "
            for k = 1 to pow(2, level) - 1:
                    push nodes.front into edges
                    temp <- pop(nodes)
                    apply (b)
                    if temp != NULL print value
                    else print " "
            apply (a)
            print linefeed

            if level != height - 1:
                    apply (e)
                    for k = 0 to pow(2, level) - 1:
                            temp <- pop(edges)
                            if temp->left != NULL print "/"
                            else print " "
                            push temp->left into nodes
                            apply (c)
                            if temp->right != NULL print "\"
                            else print " "
                            push temp->right into nodes
                            apply (d)
                    apply (e)
                    print linefeed


                    

# key points 
    1. Values and edges are printed separately using two queue each feeding
       the other

    2. Nulls are taken into account for non-existent nodes and space
       is printed in place of edges and values










 
    
