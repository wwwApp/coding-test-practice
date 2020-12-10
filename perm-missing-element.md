# perm-missing-element

An array A consisting of N different integers is given. The array contains integers in the range [1..(N + 1)], which means that exactly one element is missing.

Your goal is to find that missing element.

Write a function:

function solution(A);

that, given an array A, returns the value of the missing element.

For example, given array A such that:

  A[0] = 2
  A[1] = 3
  A[2] = 1
  A[3] = 5
the function should return 4, as it is the missing element.

Write an efficient algorithm for the following assumptions:

N is an integer within the range [0..100,000];
the elements of A are all distinct;
each element of array A is an integer within the range [1..(N + 1)].

https://app.codility.com/programmers/lessons/3-time_complexity/perm_missing_elem/

``` js 

function solution(A) {
    // going to solve this by
    // sum of all els - sum of els in A
    // equation to find the sume of all els in the array 
    // (N * (1 + N)) / 2

    // since its missing one el
    // original array is 1 greater in length
    let allSize = A.length + 1
    let allSum = (allSize * (1 + allSize)) / 2
    let givenSum = A.reduce((sum,el)=>sum+el, 0)

    return allSum - givenSum
}

// this solution will fail more complicated tests
// such as if your missing item is first or last item
// function solution(A) {
//    A.sort()
//    for(let i=0; i <A.length; i++) {
//        let shouldBeNext = A[i] + 1;
//        if(shouldBeNext != A[i+1]){
//            return shouldBeNext
//        }
//    }
// }

```
