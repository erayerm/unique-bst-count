# unique-bst-count
# unique-bst-count

Given a number 'num', how many unique binary trees include 1 to n? (0<n<15)

For example, they are the trees for "num = 3"

```

   1         3     3      2      1
    \       /     /      / \      \
     3     2     1      1   3      2
    /     /       \                 \
   2     1         2                 3

Output: 5
   
```

My Code:

```cpp
int totalTrees(int num){
  
    vector<int> myVector;
    int rightSide = 0;
    int leftSide = 0;
    int sum = 0;
  
    for (int i = 1; i <= num; i++){
        for(int j = 1; j <= i; j++){
            if(j == 1)
                leftSide = 1;
            else
                leftSide = myVector[j-2];
            if(j == i)
                rightSide = 1;
            else
                rightSide = myVector[i-j-1];
            
            sum+=leftSide*rightSide;
        }
        myVector.push_back(sum);
        sum=0;
    }
    return myVector[num-1];
}
```

Example of my logic that I use on my code:
```

For "num = 4" I'm calculating when a number is at the top of the tree for each number.

When 1 is on the top there should be 3 numbers on the right and 0 numbers on the left
  There are 5 possible (num = 3's output) trees on the right and 1 possible (empty) tree on the left.
  So there will be 5 (5*1) trees when number 1 is on top.
  
When 2 is on the top there should be 2 numbers on the right and 1 number on the left
  There are 2 possible (num = 2's output) trees on the right and 1 possible (num = 1's output) tree on the left.
  So there will be 2 (2*1) trees when number 2 is on top.
  
When 3 is on the top there should be 1 number on the right and 2 numbers on the left
  There is 1 possible (num = 1's output) tree on the right and 2 possible (num = 2's output) trees on the left.
  So there will be 2 (1*2) trees when number 3 is on top.
  
When 4 is on the top there should be 0 numbers on the right and 3 numbers on the left
  There is 1 possible (empty) tree on the right and 5 possible (num = 3's output) trees on the left.
  So there will be 5 (1*5) trees when number 4 is on top.

Summing all of the possibilities gives me the answer which is 14.
```
