# tape-equilibrium

A non-empty array A consisting of N integers is given. Array A represents numbers on a tape.

Any integer P, such that 0 < P < N, splits this tape into two non-empty parts: A[0], A[1], ..., A[P − 1] and A[P], A[P + 1], ..., A[N − 1].

The difference between the two parts is the value of: |(A[0] + A[1] + ... + A[P − 1]) − (A[P] + A[P + 1] + ... + A[N − 1])|

In other words, it is the absolute difference between the sum of the first part and the sum of the second part.

For example, consider array A such that:

  A[0] = 3
  A[1] = 1
  A[2] = 2
  A[3] = 4
  A[4] = 3

We can split this tape in four places:

P = 1, difference = |3 − 10| = 7
P = 2, difference = |4 − 9| = 5
P = 3, difference = |6 − 7| = 1
P = 4, difference = |10 − 3| = 7

Write a function:

function solution(A);

that, given a non-empty array A of N integers, returns the minimal difference that can be achieved.

For example, given:

  A[0] = 3
  A[1] = 1
  A[2] = 2
  A[3] = 4
  A[4] = 3

the function should return 1, as explained above.

Write an efficient algorithm for the following assumptions:

N is an integer within the range [2..100,000];
each element of array A is an integer within the range [−1,000..1,000].
Copyright 2009–2020 by Codility Limited. All Rights Reserved. Unauthorized copying, publication or d

https://app.codility.com/programmers/lessons/3-time_complexity/tape_equilibrium/

``` js 
// score of 85%
// some test cases fail with this...
function solution(A) {
    let leftSum = 0;
    let rightSum = A.reduce((sum,el)=>sum+=el, 0);
    let minDiff = Math.abs(leftSum - rightSum);

    for(let i=0; i < A.length - 1; i++) {
        leftSum += A[i]
        rightSum -= A[i]
        let diff = Math.abs(leftSum - rightSum)

        minDiff = minDiff > diff ? diff : minDiff;
    }

    return minDiff
}

// This solution is not efficient
// due to the use of slice in a loop
// function solution(A) {
//     let minDiff = 0;
// 
//     for(let i=1; i < A.length; i++) {
//         let firstSum = A.slice(0,i).reduce((sum,el)=>sum+=el, 0);
//         let secondSum = A.slice(i).reduce((sum,el)=>sum+=el, 0);
//         let diff = Math.abs(firstSum - secondSum)
// 
//         minDiff = minDiff === 0 ? diff : Math.min(diff,minDiff);
//     }
// 
//     return minDiff
// }

```
