# Sorting Template

## Javascript sort method

```javascript
function sortCustom(arr) {
    return arr.sort(conditionFunction());
}
```



## Selection sort using Javascript

```javascript
function selectionSort(arr) {
    let tempArr = arr.slice();
    for (let i = 0; i < tempArr.length; i++) {
        let minIndex = i;
        for (let j = i; j < tempArr.length; j++) {
            if (tempArr[minIndex] > tempArr[j]) {
                minIndex = j;
            }
        }
    
        if (minIndex !== i) {
            let temp = tempArr[i];
            tempArr[i] = tempArr[minIndex];
            tempArr[minIndex] = temp;
        }
    }
    
    return tempArr;
}
```



## Condition Function

```javascript
// 1. 비우면 유니코드 순서(문자는 대문자 < 소문자)로 오름차순
// 2. 대소문자 구분 없이 진행 String.toUpperCase()
function confitionFunc(a, b) {
    if (숫자 오름차순) {
       return a - b;
    }
    
    if (숫자 내림차순) {
       return b - a;
    }
    
    if (문자 오름차순) {
       if (a > b) {
          return 1;
       } else if (a < b) {
          return -1;
       } else {
          return 0;
       }
    } 
    
    if (문자 내림차순) {
       if (a > b) {
          return -1;
       } else if (a < b) {
          return 1;
       } else {
          return 0;
       }
    } 
}
```
