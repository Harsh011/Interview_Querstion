<details>
<summary>
<h3>01. Sum of the Natural Number 1 to n </h3>
</summary>

```js
function sum(num) {
  let sum = 0;
  for (let i = 1; i <= num; i++) {
    sum += i;
  }

  return sum;
}

console.log(sum(5)); // 15
console.log(sum(10)); // 55

// Another methods

function sumNum(num) {
  return (num * (num + 1)) / 2;
}

console.log(sumNum(5)); // 15
console.log(sumNum(10)); // 55
```
</details>