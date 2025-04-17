# likelihood（似然） 
概率是给定参数，数据有多可能出现

似然是给定数据，参数有多合理，用来评估哪个参数最能解释数据

# Fisher Information
wiki：https://en.wikipedia.org/wiki/Fisher_information
在数理统计中，fisher info是用来度量随机变量X所携带的关于对X进行建模的分布的未知参数theta的信息量的方法，观测信息的期望 or 得分的方差
> In mathematical statistics, the Fisher information is a way of measuring the amount of information that an observable random variable X carries about an unknown parameter θ of a distribution that models X.

**socre：** $\frac{\partial}{\partial \theta} \log f(X; \theta)$
 
如果$\theta$ 是 true parameter（ie X确实是根据$f(X;\theta)$ 进行分布），score的期望evaluated at the $\theta$ 是0

期望为零的推导：

$$
\begin{align*}
&\mathbb{E} \left[ \left. \frac{\partial}{\partial \theta} \log f(X; \theta) \right| \theta \right] \\
&= \int_{\mathbb{R}} \frac{\frac{\partial}{\partial \theta} f(x; \theta)}{f(x; \theta)} f(x; \theta) \, dx \\
&= \frac{\partial}{\partial \theta} \int_{\mathbb{R}} f(x; \theta) \, dx \\
&= \frac{\partial}{\partial \theta} 1 \\
&= 0.
\end{align*}
$$



Fisher信息的定义（score的方差）：

$$
\begin{align*}
& \mathcal{I}(\theta) \\
&= \mathbb{E} \left[ \left(  \frac{\partial}{\partial \theta} \log f(X; \theta) \right)^2   \middle| \theta \right]\\
&= \int_{\mathbb{R}} \left( \frac{\partial}{\partial \theta} \log f(x; \theta) \right)^2 f(x; \theta) \, dx
\end{align*}
$$


## fisher info为什么这么定义
https://math.stackexchange.com/questions/265917/intuitive-explanation-of-a-definition-of-the-fisher-information

