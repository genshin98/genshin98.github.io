---
title = "代码测试"
date = 2022-04-05
---

```c++
#include <stdio.h>
#include <string.h>
#include <vector>
#include <map>
#include <set>
#include <iostream>
using namespace std;

const int N = 2e5 + 10;

int a[N];

bool cmp(int x, int y) {
	return x > y;
}

int main() {
	int n,k,x;
	scanf("%d%d%d", &n, &k, &x);
	for (int i = 0;i < n;i++) {
		int y;
		scanf("%d", &y);
		a[i] = y;
	}
	for (int i = 0;i < n && k > 0;i++) {
		int t = a[i] / x;
		if (t > k) {
			t -= k;
			a[i] -= k * x;
			k = 0;
		} else {
			a[i] %= x;
			k -= t;
		}
	}
	sort(a, a + n, cmp);
	long long ans = 0;
	for (int i = 0;i < n;i++) {
		if (k > 0) {
			k--;
		} else {
			ans += a[i];
		}
	}
	cout << ans;
	return 0;
}
```
