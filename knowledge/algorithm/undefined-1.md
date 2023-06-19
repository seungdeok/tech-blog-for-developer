# 소수 찾기

### 에라토스테네스의 체

> * O(nlogn)
> * 검사한 원소의 배수를 선택지에서 소거해나가는 방식



```javascript
function getPrimes(num) {
    const primes = [false, false, ...Array(num - 1).fill(true)]; // 0, 1은 소수가 아니다.
    for (let i = 2; i * i <= n; i++) {
        if (primes[i]) {
            for (let j = i * 2; j <= num; j += i) {
                primes[j] = false;
            }
        }
    }
    
    return primes.filter(Boolean);
}
```
