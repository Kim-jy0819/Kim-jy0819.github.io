---
layout: single
title: "경사하강법"
categories: ['AI', 'math']
use_math: true
---

# 경사하강법
경사하강법은 무어-펜로즈 역행렬을 구하지 않고, 비용이 최소가 되게 하도록 가중치를 구하는 방법입니다. 현재 위치에서 기울기값과 학습률을 곱하여 빼준 값을 다음 위치로 업데이트하여 일정 값 이하가 되도록 설정하면 만족할 만한 최소값을 얻을 수 있게 됩니다. 비용 함수를 계산할 때 사용하는 방법에는 L2노름이 사용됩니다. L2 노름은 유클리드 거리를 구하는 방법입니다. 여기서는 RMSE(편차 제곱의 평균 제곱근)와 동일한 의미로 사용됩니다(n: 데이터의 개수, d: 가중치 개수) .비용이자 목적식인 $\|y-x \beta\|_{2}\$ 의 Gradient를 구하여 경사하강법 식을 구해보겠습니다.



# $\|y-x \beta\|_{2}$

비용이자 목적식인 $\|y-x \beta\|_{2}$ 를 최솟값으로 만드는 벡터 $\beta\$를 구하기 위하여 벡터 $\beta$ 에 대하여 그레디언트 벡터를 구해야합니다. 벡터 $\beta\$의 k번째 원소 $\beta$ 에 대하여 목적식을 편미분 해줍니다. 위와 같은 식을 거쳐 나오면 그레디언트가 나옵니다. RMSE를 구하는 방식은 조금 복잡합니다.



$$
\begin{aligned}
&\partial_{\beta_{k}}\|y-x \beta\|_{2} \\
&=\partial \beta_{k}\left\{\frac{1}{n} \sum_{i=1}^{n}\left(y_{i}-\sum_{j=1}^{d} X_{i j} \beta_{j}\right)^{2}\right\}^{\frac{1}{2}} \\
&=\partial_{\beta k}\left[\frac{1}{n}\left\{\left(y_{1}-x_{11} \beta_{1} \cdots-x_{1 d} \beta_{d}\right)^{2}+\cdots+\left(y_{n}-x_{n 1} \beta_{1} \ldots-x_{n d} \beta_{d}\right)^{2}\right\}\right]^{\frac{1}{2}} \\
&=\frac{1}{2} n^{-\frac{1}{2}}\left\{-2 x_{1 k}\left(y_{1}-x_{11} \beta_{1} \cdots-x_{1 d} \beta_{d}\right) \quad \cdots-2 x_{n k}\left(y_{n}-x_{n 1} \beta_{1} \cdots-x_{n d} \beta_{d}\right)\right\} \\
&\quad\left\{\left(y_{1}-x_{11} \beta_{1} \cdots-x_{1 d} \beta_{d}\right)^{2}+\cdots+\left(y_{n}-x_{n 1} \beta_{1} \ldots-x_{n d} \beta_{d}\right)^{2}\right\}^{-\frac{1}{2}} \\
&=-\sum_{i=1}^{n} x_{i k}\left(y_{i}-\sum_{j=1}^{d} x_{i j} \beta_{j}\right)\left[n \sum_{i=1}^{n}\left(y_{i}-\sum_{j=1}^{d} x_{i j} \beta_{j}\right)^{2}\right]^{-\frac{1}{2}} \\
&=-\frac{x_{k}^{\top}(y-X \beta)}{n\|y-x \beta\|_{2}}
\end{aligned}
$$


# $\partial_{\beta_{k}}\|Y-x \beta\|_{2}^{2}$
$\partial_{\beta_{k}}\|Y-x \beta\|_{2}^{2}$ 의 그레디언트를 구해주면 조금 더 쉽게 그레디언트를 계산할 수 있습니다. 루트를 씌어주든 씌어주지 않든간에 상관없이 그레디언트의 방향에는 지장을 주지 않으므로, 계산이 편한 방식을 사용합니다.


$$
\begin{aligned}
&\partial_{\beta_{k}}\|Y-x \beta\|_{2}^{2} \\
&=\partial \beta_{k}\left\{\frac{1}{n} \sum_{i=1}^{n}\left(y_{i}-\sum_{j=1}^{d} X_{i j} \beta_{j}\right)^{2}\right\} \\
&=\partial_{\beta k}\left[\frac{1}{n}\left\{\left(y_{1}-x_{11} \beta_{1} \cdots-x_{1 d} \beta_{1}\right)^{2}+\cdots+\left(y_{n}-x_{n 1} \beta_{1} \cdots-x_{n d} \beta_{1}\right)^{2}\right\}\right] \\
&=\frac{1}{n}\left\{-2 x_{1 k}\left(y_{1}-x_{11} \beta_{1} \cdots-x_{1 d} \beta_{d}\right) \quad \cdots-2 x_{n k}\left(y_{n}-x_{n 1} \beta_{1} \cdots-x_{n d} \beta_{d}\right)\right\} \\
&=-\frac{2}{n} \sum_{i=1}^{n} x_{i k}\left(y_{i}-\sum_{j=1}^{d} x_{i j} \beta_{j}\right) \\
&=-\frac{2}{n} X_{k}^{\top}(y-X \beta)
\end{aligned}
$$


최종적으로 우리는 다음과 같은 그레디언트를 사용하여 경사하강법에 적용합니다.

$
\beta_{k+1}=\beta_{k}-\nabla_{\beta_{k}}\left\|y-\beta_{k}\right\|^{2}
$

