---
description: 최대공약수 & 최소공배수
---

# GCD & LCD

{% hint style="info" %}
**유클리드호제법**

r = num1 % num2

GCD(num1, num2)= GCD(num2, r)

(r이 0이라면 그 때의 num2가 최대공약수)
{% endhint %}



```java
// num1 * num2 = gcm * lcm
function solution(num1, num2) {
    const gcd = (a, b) => a % b === 0 ? b : gcd(b, a % b);
    const lcm = (a, b) => a * b / gcd(a, b);
    return [gcd(num1, num2), lcm(num1, num2)];
}
```
