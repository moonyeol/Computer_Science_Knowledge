---
layout: post
title: Greedy Algorithm
subtitle: 
gh-repo: 
gh-badge: [star, fork, follow]
tags: 알고리즘
categories : algorithm
comments: true
---

# 탐욕 알고리즘 (Greedy Algorithm)

그리디 알고리즘은 **동적 프로그래밍** 사용 시 지나치게 많은 일을 한다는 것에서 착안하여 고안된 알고리즘입니다. 동적 프로그래밍을 대체하는 것은 아니고 같이 쓰이며 서로 보완하는 개념입니다.

 미래를 생각하지 않고 각 단계에서 가장 최선의 선택을 하는 기법입니다. 이렇게 각 단계에서 최선의 선택을 한 것이 전체적으로도 최선이길 바라는 알고리즘이죠.

물론 모든 경우에서 그리디 알고리즘이 통하지는 않습니다. 쉬운 예를 들자면 지금 선택하면 1개의 마시멜로를 받고, 1분 기다렸다 선택하면 2개의 마시멜로를 받는 문제에서는, 그리디 알고리즘을 사용하면 항상 마시멜로를 1개밖에 받지 못합니다. 지금 당장 최선의 선택은 마시멜로 1개를 받는 거지만, 결과적으로는 1분 기다렸다가 2개 받는 게 최선이기 때문이죠.

하지만 그리디 알고리즘이 통하는 몇몇 문제들이 있습니다.



활동 선택 문제

활동 선택 문제는 쉽게 말하면 한 강의실에서 여러 개의 수업을 하려고 할 때 한 번에 가장 많은 수업을 할 수 있는 경우를 고르는 겁니다.

아래에서 Si는 시작시간, Fi는 종료시간입니다. 같은 강의실을 사용해야 하므로 A1과 A4는 동시에 선택할 수 없습니다. A1과 A2도 시간이 겹치므로 선택할 수 없습니다. 그렇지만 A1과 A3는 선택할 수 있죠. 이렇게 선택하여 가장 많은 수업을 할 수 있는 경우를 찾는 겁니다.

![greedy1](..\assets\post_img\greedy1.png)

결과적으로 보면 A1, A3, A6, A8이나 A1, A3, A7, A9 등을 고르면 정답입니다.

이 문제는 동적 프로그래밍을 통해서도 풀 수 있습니다. 하나의 예를 들어 G18을 A1이 종료된 후부터, A8이 시작하기 전 활동들의 집합이라고 보면, G18 = {A3, A5, A6, A7}입니다. 이 중에서 최적의 조합(활동들이 겹치지 않고 개수는 최대)을 B18이라고 하면, 하나의 예로 B18 = {A3, A6}라고 할 수 있습니다. {A3, A7}도 되겠네요.

B18에서 A6를 골랐다고 칩시다. A6를 고르면 이제 문제는 두 개로 쪼개집니다. G16과 G68에서 각각 최적인 B16와 B18을 찾는 거죠. 이제 B16과 B18의 개수와 A6 1개를 더하면 최적 활동의 개수를 알 수 있습니다. 이를 식으로 나타내면 **C[i,j] = max(C[i,k] + C[k,j] + 1)**이 됩니다. C는 집합 Gij의 최적 개수를 나타냅니다. max는 B18에서 A6 말고 다른 것을 골랐을 때의 경우도 모두 생각해서 그 중 최적을 찾는 겁니다.

이렇게 동적 프로그래밍으로 할 수도 있지만, 문제는 이렇게 하면 모든 C들을 구해야한다는 겁니다. 하지만 우리는 **그리디 알고리즘**으로 더 효율적으로 풀 수 있습니다.

직관적으로 생각하면, 최적의 해를 구하기 위해서는 첫 번째 활동이 최대한 일찍 끝나면 됩니다. 그래야 다른 활동들을 더 많이 선택할 수 있기 때문이죠. 위의 경우에서는 첫 선택으로 가장 빨리 끝나는 A1을 골라야겠죠. A1을 골랐다면 이제 A2와 A4는 고를 수 없습니다(A1이랑 겹침). 그 다음 선택은 다음으로 일찍 끝나는 A3가 될 겁니다. 그 다음은 A6, 마지막은 A8이 되어 최종적으로 {A1, A3, A6, A8}이 됩니다.

일단 끝나는 시간 순으로 정렬한 후, 반복문을 돌며 집합의 끝나는 시간이 다음 행동의 시작 시간보다 작은 경우 집합에 추가하면 됩니다.



### 분할 가능 배낭 문제

배낭문제이지만, 물건이 무거울 경우 쪼개서 넣을 수 있습니다. 즉 무게가 초과할 거 같은면 물건을 쪼개서 일부만 넣을 수 있다는 것이죠.

그리디 알고리즘으로 간단하게 풀 수 있습니다. 직관적으로 생각해봅시다. 물건을 쪼갤 수 있다는 가정 하에서는 무게 대비 가치가 높은 것들을 먼저 넣는 게 최선입니다.

![greedy2](..\assets\post_img\greedy2.png)

무게 제한이 50입니다. 1번 물건을 먼저 선택하고, 2번, 3번 순으로 넣습니다. 3번은 무게 초과이기 때문에 20만큼만 쪼개서 넣으면 됩니다.

이런 경우도 위의 활동 선택 문제처럼, 앞에서부터 그때 그때 가장 최선인 선택을 하면 결과적으로도 최선입니다.

