# unfinished-runner
Find ONE runnder who did not finish the race given the array of participants and the array of completion, which is always one item shorter
https://programmers.co.kr/learn/courses/30/lessons/42576?language=javascript#

``` js
/**

Trying to implement python's collections so you have obj that holds runner's name
and the number of their occurrences in each array
Then, you can do subtraction b/t two objects and find the one participant with occurence > 0

*/

function collectionCounter(arr){
    let obj = {}
    
    for(let i = 0; i <arr.length; i++) {
        if(obj.hasOwnProperty(arr[i])) {
            obj[arr[i]]++
        }else {
            obj[arr[i]] = 1
        }
    }
    
    return obj;
}

function solution(participant, completion) {
    const partCounter = collectionCounter(participant)
    const compCounter = collectionCounter(completion)
    
    const keys = Object.keys(compCounter)
    for(let i = 0; i<keys.length;i++) {
        partCounter[keys[i]] -= compCounter[keys[i]]
    }
    
    return Object.keys(partCounter).find(key=>partCounter[key] > 0)
}


/**

// try with perfect accuracy but zero performance
// using splice to remove already checked participant and return the person lasted after loop

function solution(participant, completion) {

    completion.forEach(name => {
        const index = participant.indexOf(name)
        if(index >= 0){
            participant.splice(index,1)
        }
    })

    return participant[0];
}

*/


```
