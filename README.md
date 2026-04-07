# 📘 NLMS 演算法說明（Normalized Least Mean Squares）

---

## 📌 題目說明

本文件說明 **NLMS（Normalized Least Mean Squares）演算法** 的數學表示與更新公式。

---

## 🖼️ 演算法示意圖

![NLMS公式](https://i.imgur.com/your-image.png)

> 上圖為題目提供之 NLMS 演算法公式（Initialization 與 Computation）。

---

## 📐 數學公式

### 🔹 Initialization（初始化）

[
\hat{h}(0) = zeros(p)
]

---

### 🔹 Computation（計算步驟）

對於每個時間點 ( n = 0,1,2,... )

#### 1️⃣ 輸入向量

[
x(n) = [x(n), x(n-1), ..., x(n-p+1)]^T
]

#### 2️⃣ 誤差計算

[
e(n) = d(n) - \hat{h}^H(n)x(n)
]

#### 3️⃣ 權重更新

[
\hat{h}(n+1) = \hat{h}(n) + \frac{\mu e^*(n)x(n)}{x^H(n)x(n)}
]

---

## 💡 重點整理

* 使用 **正規化** 提升穩定性
* 適用於自適應濾波（Adaptive Filtering）
* 比 LMS 收斂更穩定

---

## 🧑‍💻 程式碼範例

```python
import numpy as np

def nlms(x, d, mu, p):
    h = np.zeros(p)
    for n in range(p, len(x)):
        x_vec = x[n:n-p:-1]
        y = np.dot(h, x_vec)
        e = d[n] - y
        h = h + (mu * e * x_vec) / (np.dot(x_vec, x_vec) + 1e-6)
    return h
```

---

## 📊 表格說明

| 符號     | 意義   |
| ------ | ---- |
| (x(n)) | 輸入訊號 |
| (d(n)) | 期望輸出 |
| (e(n)) | 誤差   |
| (h(n)) | 權重向量 |

---

## 🔗 參考資料

* Adaptive Filter 課程筆記
* 數位訊號處理教材

---

## 📌 待辦事項

* [x] 建立 GitHub
* [x] 上傳 README
* [ ] 補充更多說明

---

## 🎯 結論

NLMS 是一種改良的 LMS 演算法，透過正規化提升收斂效果與穩定性。

---
