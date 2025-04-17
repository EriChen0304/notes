# GPT make all
# Uhlmann Fidelity, Affinity 与测地线距离

本笔记整理了 Uhlmann Fidelity 和 Affinity 的定义、推导过程、几何解释以及它们在测地线距离（geodesic distance）中的应用。内容包括类比理解、纯态与混态的区别处理，以及相关量子信息几何背景。

---

## 一、定义

### 1. Uhlmann Fidelity

量子态 \( \rho \) 与 \( \sigma \) 之间的保真度（Fidelity）定义为：

\[
F(\rho, \sigma) = \left( \operatorname{Tr} \sqrt{ \sqrt{\rho} \sigma \sqrt{\rho} } \right)^2
\]

性质：
- \( 0 \leq F(\rho, \sigma) \leq 1 \)
- 纯态下：\( F(|\psi\rangle, |\phi\rangle) = |\langle \psi | \phi \rangle|^2 \)
- \( F = 1 \) 当且仅当 \( \rho = \sigma \)
  
这个定义源于量子力学测量的本质：\( |\langle \psi | \phi \rangle|^2 \) 就是从一个态“跳转”到另一个态的概率。

---

### 2. Affinity（亲和度）

\[
A(\rho, \sigma) = \operatorname{Tr}( \sqrt{\rho} \sqrt{\sigma} )
\]

- 与 Fidelity 取值范围相同。
- 纯态下退化为 \( |\langle \psi | \phi \rangle| \)。

Affinity 和 Fidelity 均可用作量子态“相似度”的度量，但计算方式不同。

---

## 二、Uhlmann 定理与纯态提升（Purification）

### Uhlmann 定理（Uhlmann's Theorem）

对于任意密度矩阵 \( \rho \)、\( \sigma \)，存在其在更大 Hilbert 空间中的“纯态提升” \( |\Psi_\rho\rangle, |\Psi_\sigma\rangle \)，满足：

\[
\operatorname{Tr}_{\text{ancilla}}(|\Psi_\rho\rangle \langle \Psi_\rho|) = \rho
\]

且：

\[
\max_{|\Psi_\rho\rangle, |\Psi_\sigma\rangle} |\langle \Psi_\rho | \Psi_\sigma \rangle| = \sqrt{F(\rho, \sigma)}
\]

**含义**：Fidelity 等价于两态纯态提升之间最大内积的平方。

---

## 三、测地线距离（Geodesic Distance）

### 1. 纯态空间中的测地线

在复 Hilbert 空间中，纯态 \( |\psi\rangle, |\phi\rangle \) 可视为单位球面上的点，其测地线长度（夹角）为：

\[
L_{\text{geo}}(|\psi\rangle, |\phi\rangle) = \arccos |\langle \psi | \phi \rangle|
\]

这是 Fubini–Study 度量诱导的几何距离。

---

### 2. 混态空间中的测地线（通过 Uhlmann Fidelity）

根据 Uhlmann 定理，Fidelity 的平方根表示纯态提升之间的最大内积。因此测地线自然推广为：

\[
L^{\text{SLD}}_{\text{geo}}(\rho, \sigma) = \arccos \sqrt{F(\rho, \sigma)}
\]

这就是 **Bures 距离** 所诱导的测地线长度。

---

### 3. Affinity 与 WY 距离

Wigner–Yanase（WY）度量诱导的测地线为：

\[
L^{\text{WY}}_{\text{geo}}(\rho, \sigma) = \arccos A(\rho, \sigma)
\]

Affinity 在该度量下具有“余弦夹角”的几何意义。

---

## 四、比较表格

| 距离类型       | 使用的量     | 测地线公式                               | 对应度量结构             |
|----------------|--------------|------------------------------------------|--------------------------|
| Bures 距离     | Fidelity     | \( \arccos \sqrt{F(\rho, \sigma)} \)     | SLD Fisher 信息度量       |
| WY 距离        | Affinity     | \( \arccos A(\rho, \sigma) \)             | Wigner–Yanase 度量       |

---

## 五、类比理解（纯态 vs 混态）

- 对于纯态：内积 \( \langle \psi | \phi \rangle \) 就是“夹角的余弦”，自然定义测地线。
- 对于混态：通过 Uhlmann 的提升方式，将“夹角”概念推广到混态空间。
- Fidelity 是混态空间中的“余弦夹角”，测地线长度由 \( \arccos \sqrt{F} \) 给出。
- Affinity 对应于另一种度量（WY），但几何意义类似：重叠程度 → 夹角。

---

如需进一步推导 Bures 距离的形式，或者希望从量子 Fisher 信息的角度看测地线近似展开，可以继续深入。




---

# 态的提升（Purification）

### 一、基本定义

给定一个混态 $\rho$，定义在系统的 Hilbert 空间 $\mathcal{H}_S$ 上。

我们可以找到一个更大的 Hilbert 空间 $\mathcal{H}_S \otimes \mathcal{H}_A$（引入一个辅助系统 $A$），以及一个纯态 $|\Psi\rangle$，使得：

$$
\rho = \operatorname{Tr}_A\left( |\Psi\rangle \langle \Psi| \right)
$$

这就叫做 **态的提升**（Purification）。

---

### 二、具体例子

设混态：

$$
\rho = \frac{1}{2} |0\rangle\langle 0| + \frac{1}{2} |1\rangle\langle 1| = \frac{I}{2}
$$

它是一个 2 维系统的最大混态。

构造一个纯态：

$$
|\Psi\rangle = \frac{1}{\sqrt{2}} \left( |0\rangle_S \otimes |0\rangle_A + |1\rangle_S \otimes |1\rangle_A \right)
$$

这个纯态定义在 $\mathcal{H}_S \otimes \mathcal{H}_A$ 上。

对 $A$ 取偏迹：

$$
\rho_S = \operatorname{Tr}_A\left( |\Psi\rangle\langle\Psi| \right) = \frac{I}{2}
$$

于是我们得到了 $\rho$，说明 $|\Psi\rangle$ 是 $\rho$ 的一个提升。

---

### 三、物理意义

- **混态**表示系统部分失去了信息（比如由于纠缠、噪声、部分测量等）。
- **提升**表示：你可以把一个“有信息缺失”的混态，看作是某个更大系统中的纯态，只是你没看到全貌。
- 这为比较两个混态之间的相似度（比如 Uhlmann Fidelity）提供了物理基础。

---

### 四、Uhlmann Fidelity 中的应用

Uhlmann Fidelity 的定义就是基于所有可能提升之间重叠最大值：

$$
F(\rho, \sigma) = \left( \max_{|\Psi_\rho\rangle, |\Psi_\sigma\rangle} |\langle \Psi_\rho | \Psi_\sigma \rangle| \right)^2
$$

其最终数学表达式为：

$$
F(\rho, \sigma) = \left( \operatorname{Tr} \sqrt{ \sqrt{\rho} \, \sigma \, \sqrt{\rho} } \right)^2
$$

---

如果你希望，我可以把这个整理为 `.md` 文件内容，或者继续写关于 Uhlmann 定理更具体的形式与证明。你想深入哪一部分我都可以接着帮你展开。