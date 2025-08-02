```javascript
function attackerSuccessProbability(q, z) {
  const p = 1.0 - q;
  const lambda = z * (q / p);
  let sum = 1.0;

  for (let k = 0; k <= z; k++) {
    let poisson = Math.exp(-lambda);
    for (let i = 1; i <= k; i++) {
      poisson *= lambda / i;
    }
    sum -= poisson * (1 - Math.pow(q / p, z - k));
  }

  return sum;
}

```
