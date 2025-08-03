``` javascript

function attackerSuccessProbability(q, z) {
  // q 는 공격자의 전체 해시 파워를 의미
  // z 는 정직한 노드가 생성하는 블록의 개수

  const p = 1.0 - q; //  정직한 노드의 해시파워

  const lambda = z * (q / p); //  정직한 노드가 z개의 블록을 만드는 동안 공격자가 평균적으로 만들 것으로 기대되는 블록 수
  let sum = 1.0; // 전체 확률 1.0

  for (let k = 0; k <= z; k++) {
    // 공격자가 정직한 노드의 z개의 블록만큼 k개의 블록을 차례대로 만듬

    let poisson = Math.exp(-lambda); //  푸아송 분포의 초기값 (k=0일 때 확률)

    for (let i = 1; i <= k; i++) {
      poisson *= lambda / i; //  공격자가 k개의 블록을 만들 확률
    }

    sum -= poisson * (1 - Math.pow(q / p, z - k));

    //  Math.pow(q / p, z - k)  공격자는 z-k 만큼 블록에서 밀리고 있는 상황에서 공격자가 정직한 노드를 따라잡을 확률 (k가 높아질수록 따라잡을 확률이 높아짐)
    //  1 - Math.pow(q / p, z - k)   공격자가 z-k 만큼의 차이를 따라잡지 못할 확률
    // poisson * (1 - Math.pow(q / p, z - k)) 공격자가 k개의 블록을 만들었을때 공격에 실패할 확률 
    // sum -=  "k개의 블록이 만들어질 때 정직한 노드를 따라잡지 못해 공격에 실패할 확률을 전체 1에서 계속 빼준다."
  }

  return sum;
}

// 예시 1: 공격자가 전체 해시 파워의 10%를 가지고 있고,
// 정직한 체인보다 5개의 블록이 뒤처진 경우
const q1 = 0.1;
const z1 = 5;
const probability1 = attackerSuccessProbability(q1, z1);
console.log(
  `공격자의 전체 해시파워= ${q1}, 정직한 체인보다  = ${z1}개 뒤처진 경우 공격자의 공격 성공 확률: ${probability1}`
);
```
