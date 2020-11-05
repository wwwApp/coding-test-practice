# find-all-combo
You need to find all the combinations of cloth
https://programmers.co.kr/learn/courses/30/lessons/42578

``` js

function solution(clothes) {
    let clothObj = {}
    
    clothes.forEach(cloth=> {
        const name = cloth[0]
        const type = cloth[1]
        if(clothObj[type]){
            // this specific type of cloth is counted
            // and this specific name of the cloth type is not counted yet
            clothObj[type].push(name)
            
        }else{
            // this specific type of cloth is not yet counted
            clothObj[type] = [name]
        }
    })
    
    // euqation to find all combination
    // (number of clothes in one type + 1) + (number of clothes in one type + 1) - 1
    // adding 1 counts for when you don't wear that type of cloth at all
    // subtracing 1 at the end removes the probability of not wearing anything
    // since you MUST wear at least one cloth per day
    
    let answer = 1;
    const keys = Object.keys(clothObj)
    
    for(let i = 0; i < keys.length; i++) {
        answer *= (clothObj[keys[i]].length + 1)
    }
    
    console.log(clothObj)
    
    return answer - 1;
}

```
