# 모자이크

샐마는 벽에 점토 모자이크를 색칠할 계획이다. 
모자이크는 초기에 $N^2$개의 색칠되지 않은 $1\times1$ 정사각형 타일들로 이루어진 $N \times N$ 격자이다. 
모자이크의 행들은 위에서 아래 방향으로 $0$부터 $N-1$까지 번호가 붙어있고, 열들은 왼쪽에서 오른쪽으로 $0$부터 $N-1$까지 번호가 붙어있다. 
$i$ 행과 $j$ 열 ($0 \le i < N$, $0 \le j < N$) 의 타일은 $(i, j)$로 나타낸다. 각 타일은 흰색 ($0$으로 나타냄) 또는 검은색 ($1$로 나타냄)으로 색칠 해야만 한다.

모자이크를 색칠하기 위해 샐마는 우선 길이 $N$의 두 배열 $X$와 $Y$를 선택하는데, 배열의 각 원소는 $0$ 또는 $1$의 값을 가지고 $X[0] = Y[0]$을 만족한다. 그녀는 먼저 배열 $X$에 따라서 가장 위쪽 행($0$ 행)의 타일들을 색칠하는데, 타일 $(0, j)$의 색은 $X[j]$ ($0 \le j < N$)와 같다. 
그녀는 그 다음 배열 $Y$에 따라서 가장 왼쪽 열($0$ 열)의 타일들을 색칠하는데, 타일 $(i, 0)$의 색은 $Y[i]$ ($0 \le i < N$)와 같다. 

그 후 그녀는 모든 타일들을 색칠할 때까지 다음 과정들을 반복한다:
* 그녀는 위쪽 이웃 (타일 $(i-1, j)$)과 왼쪽 이웃 (타일 $(i, j-1)$)이 이미 모두 색칠된 임의의 색칠되지 않은 타일 $(i, j)$을 찾는다. 
* 그런 후, 그녀는 두 이웃 모두가 흰색이면 타일 $(i, j)$를 검은색으로, 그렇지 않으면 흰색으로 색칠한다. 

타일들의 최종 색깔은 샐마가 색칠하는 순서와 상관 없음을 보일 수 있다. 

야스민은 모자이크의 타일들의 색깔에 대해서 매우 호기심이 많다. 
그녀는 샐마에게 $0$부터 $Q-1$까지 번호가 붙은 $Q$개 질의를 묻는다. 질의 $k$ ($0 \le k < Q$)에서, 모자이크의 부분 직사각형 영역을 다음과 같이 제시한다:
* 가장 위쪽 행 $T[k]$와 가장 아래쪽 행 $B[k]$ ($0 \le T[k] \le B[k] < N$), 
* 가장 왼쪽 열 $L[k]$와 가장 오른쪽 열 $R[k]$ ($0 \le L[k] \le R[k] < N$).

질의에 대한 답은 이 부분 직사각형에 속하는 검은색 타일들의 수이다.
구체적으로, 샐마는 $T[k] \le i \le B[k]$, $L[k] \le j \le R[k]$를 만족하고 검은색인 타일 $(i, j)$가 몇 개 존재하는지 찾아야 한다. 

야스민의 질의들에 답하는 프로그램을 작성하시오.

## Implementation Details

당신은 다음 함수를 구현해야만 한다. 

```
std::vector&lt;long long&gt; mosaic(
	std::vector&lt;int&gt; X, std::vector&lt;int&gt; Y,
    std::vector&lt;int&gt; T, std::vector&lt;int&gt; B,
    std::vector&lt;int&gt; L, std::vector&lt;int&gt; R)
```

* $X$, $Y$: 각각 가장 위쪽 행 ($0$ 행) 과 가장 왼쪽 열 ($0$ 열) 의 타일들의 색깔을 나타내는 길이 $N$의 배열들.
* $T$, $B$, $L$, $R$: 야스민이 물은 질의들을 나타내는 길이 $Q$의 배열들.
* 함수는 길이 $Q$의 배열 $C$를 반환해야 한다. 여기서, $C[k]$는 질의 $k$ ($0 \le k < Q$)의 답이다.
* 이 함수는 각 테스트 케이스에 대해 정확히 한 번 호출된다. 

## Constraints

* $1 \leq N \leq 200\,000$
* $1 \leq Q \leq 200\,000$
* $0 \leq i < N$인 각 $i$에 대해서, $X[i] \in \{0, 1\}$ 이고 $Y[i] \in \{0, 1\}$
* $X[0] = Y[0]$
* $0 \leq k < Q$인 각 $k$에 대해서, $0 \leq T[k] \leq B[k] < N$ 이고 $0 \leq L[k] \leq R[k] < N$

## Subtasks

| Subtask | Score  | Additional Constraints |
| :-----: | :----: | ---------------------- |
| 1       | $5$    | $N \leq 2; Q \leq 10$
| 2       | $7$    | $N \leq 200; Q \leq 200$
| 3       | $7$    | $T[k] = B[k] = 0$ ($0 \leq k < Q$인 각 $k$에 대해)
| 4       | $10$   | $N \leq 5000$
| 5       | $8$    | $X[i] = Y[i] = 0$ ($0 \leq i < N$인 각 $i$에 대해)
| 6       | $22$   | $T[k] = B[k]$ 그리고 $L[k] = R[k]$ ($0 \leq k < Q$인 각 $k$에 대해)
| 7       | $19$   | $T[k] = B[k]$ ($0 \leq k < Q$인 각 $k$에 대해)
| 8       | $22$   | 추가적인 제약조건이 없다.

## Example

다음 호출을 생각해보자. 

```
mosaic([1, 0, 1, 0], [1, 1, 0, 1], [0, 2], [3, 3], [0, 0], [3, 2])
```

이 예제는 아래에 그림으로 보여진다. 왼쪽 그림은 모자이크의 타일들의 색깔을 보여준다. 중간과 오른쪽 그림은 각각 야스민이 첫번째와 두번째 질의에서 물은 부분 직사각형을 보여준다. 

![](example.png "550")

질의들(다시 말해서, 그늘진 직사각형 영역 속 $1$의 수)에 대한 답은 각각 $7$과 $3$이다. 그러므로, 함수는 $[7, 3]$를 반환해야 한다.

## Sample Grader

입력 형식:

```
N
X[0]  X[1]  ...  X[N-1]
Y[0]  Y[1]  ...  Y[N-1]
Q
T[0]  B[0]  L[0]  R[0]
T[1]  B[1]  L[1]  R[1]
...
T[Q-1]  B[Q-1]  L[Q-1]  R[Q-1]
```

출력 형식:

```
C[0]
C[1]
...
C[S-1]
```

여기서, $S$는 `mosaic`에 의해 반환된 배열 $C$의 길이이다.
