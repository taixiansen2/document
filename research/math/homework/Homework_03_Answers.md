# Homework 03

## Problem 1
**翻译题目：**
(a) 考虑流形 $GL_1(\mathbb{C}) = \mathbb{C}^\times \hookrightarrow \mathbb{C} = \mathbb{R}^2$。通过 $\mathbb{R}^2$ 的任意偏好坐标（笛卡尔或极坐标），写出 $GL_1(\mathbb{C})$ 上左不变向量场的一组基。它们也是右不变的吗？
(b) 考虑群 $P := \{\begin{pmatrix} a & b \\ 0 & 1 \end{pmatrix} \in GL_2(\mathbb{R})\}$。将 $P$ 视为嵌入 $\mathbb{R}^2$ 的流形。通过 $\mathbb{R}^2$ 的任意偏好坐标，写出 $P$ 上左不变向量场的一组基。它们也是右不变的吗？

**详细的中文作答：**
(a) 在笛卡尔坐标系下，记 $z = x+iy$。群乘法（左平移）由复数乘法给出：$L_{a+ib}(x+iy) = (ax-by) + i(bx+ay)$。
单位元为 $e = (1, 0)$。我们在单位元处取标准基底 $\partial_x|_e$ 和 $\partial_y|_e$，并通过左平移的微分将它们前推到全空间。
$(L_{x+iy})_* (\partial_x|_e) = \frac{\partial(ax-by)}{\partial a} \partial_x + \frac{\partial(bx+ay)}{\partial a} \partial_y = x\partial_x + y\partial_y$。
$(L_{x+iy})_* (\partial_y|_e) = \frac{\partial(ax-by)}{\partial b} \partial_x + \frac{\partial(bx+ay)}{\partial b} \partial_y = -y\partial_x + x\partial_y$。
因此，左不变向量场的一组基是 $X_1 = x\partial_x + y\partial_y$ 和 $X_2 = -y\partial_x + x\partial_y$。
由于 $GL_1(\mathbb{C})$ 是阿贝尔群，左平移和右平移是一样的，因此这些左不变向量场必然也是右不变的。

(b) 对于群 $P$，其元素可由 $(x, y)$ 参数化，表示矩阵 $\begin{pmatrix} x & y \\ 0 & 1 \end{pmatrix}$。群乘法为 $(x_1, y_1)(x_2, y_2) = (x_1 x_2, x_1 y_2 + y_1)$。
左平移为 $L_{(x_1, y_1)}(x_2, y_2) = (x_1 x_2, x_1 y_2 + y_1)$。
单位元为 $e=(1, 0)$。求导可得左不变向量场：
将 $(x_1, y_1)$ 记为 $(x, y)$，将单位元基底 $\partial_x, \partial_y$ 前推：
$(L_{x, y})_* (\partial_{x_2}|_e) = \frac{\partial(x x_2)}{\partial x_2} \partial_x + \frac{\partial(x y_2 + y)}{\partial x_2} \partial_y = x\partial_x$。
$(L_{x, y})_* (\partial_{y_2}|_e) = \frac{\partial(x x_2)}{\partial y_2} \partial_x + \frac{\partial(x y_2 + y)}{\partial y_2} \partial_y = x\partial_y$。
所以左不变向量场的一组基为 $Y_1 = x\partial_x$，$Y_2 = x\partial_y$。
我们再验证它们是否为右不变的：右平移为 $R_{(x_2, y_2)}(x_1, y_1) = (x_1 x_2, x_1 y_2 + y_1)$。
单位元处 $\partial_{x_1}$ 右平移得到的向量场在 $(x, y)$ 处为：$\frac{\partial(x_1 x)}{\partial x_1}\partial_x + \frac{\partial(x_1 y + y_1)}{\partial x_1}\partial_y = x\partial_x + y\partial_y \neq x\partial_x$。
这说明左不变向量场不是右不变的。

**简短必要的英文作答：**
(a) Using Cartesian coordinates $(x,y)$, the basis of left-invariant vector fields is $X_1 = x\partial_x + y\partial_y$, $X_2 = -y\partial_x + x\partial_y$. Yes, they are right-invariant since the group is Abelian.
(b) Using $(x,y)$ to denote the non-trivial entries, the basis of left-invariant vector fields is $Y_1 = x\partial_x$, $Y_2 = x\partial_y$. They are not right-invariant.

---

## Problem 2
**翻译题目：**
设 $B$ 是 $GL_3(\mathbb{R})$ 的标准 Borel 子群。写出 $B$ 的一个左 Haar 测度和右 Haar 测度。（模仿例 2.15 中的计算。）它的模特征 $\delta_B$ 是什么？

**详细的中文作答：**
群 $B$ 由形如 $x = \begin{pmatrix} x_{11} & x_{12} & x_{13} \\ 0 & x_{22} & x_{23} \\ 0 & 0 & x_{33} \end{pmatrix}$ ($x_{ii} \ne 0$) 的上三角矩阵组成。
使用勒贝格测度 $dx = dx_{11} dx_{12} dx_{13} dx_{22} dx_{23} dx_{33}$，我们需要找到左/右平移的雅可比行列式来构造 Haar 测度。
左平移 $L_g(x) = gx$：
$(gx)_{11} = g_{11}x_{11}$
$(gx)_{12} = g_{11}x_{12} + g_{12}x_{22}$
$(gx)_{13} = g_{11}x_{13} + g_{12}x_{23} + g_{13}x_{33}$
$(gx)_{22} = g_{22}x_{22}$
$(gx)_{23} = g_{22}x_{23} + g_{23}x_{33}$
$(gx)_{33} = g_{33}x_{33}$
该变换是一个分块下三角结构，其雅可比行列式为对角元素的乘积。即 $\det(L_g) = g_{11}^3 g_{22}^2 g_{33}$。
因此左 Haar 测度为 $d_L b = \frac{dx}{|x_{11}|^3 |x_{22}|^2 |x_{33}|}$。

同理，计算右平移 $R_g(x) = xg$：
$(xg)_{11} = x_{11}g_{11}$
$(xg)_{12} = x_{11}g_{12} + x_{12}g_{22}$
$(xg)_{13} = x_{11}g_{13} + x_{12}g_{23} + x_{13}g_{33}$
$(xg)_{22} = x_{22}g_{22}$
$(xg)_{23} = x_{22}g_{23} + x_{23}g_{33}$
$(xg)_{33} = x_{33}g_{33}$
雅可比行列式为 $\det(R_g) = g_{11} g_{22}^2 g_{33}^3$。
因此右 Haar 测度为 $d_R b = \frac{dx}{|x_{11}| |x_{22}|^2 |x_{33}|^3}$。

模特征 $\delta_B$ 满足 $d_R b = \delta_B(b) d_L b$。因此：
$\delta_B(b) = \frac{d_R b}{d_L b} = \frac{|b_{11}|^3 |b_{22}|^2 |b_{33}|}{|b_{11}| |b_{22}|^2 |b_{33}|^3} = \frac{|b_{11}|^2}{|b_{33}|^2}$。（注意：部分约定可能将其定义为倒数 $\Delta(g)$，这里由 $d_R = \delta_B d_L$ 给出。）

**简短必要的英文作答：**
Left Haar measure: $d_L b = \frac{dx_{11} dx_{12} dx_{13} dx_{22} dx_{23} dx_{33}}{|x_{11}|^3 |x_{22}|^2 |x_{33}|}$.
Right Haar measure: $d_R b = \frac{dx_{11} dx_{12} dx_{13} dx_{22} dx_{23} dx_{33}}{|x_{11}| |x_{22}|^2 |x_{33}|^3}$.
Modular character $\delta_B(b) = \frac{|b_{11}|^2}{|b_{33}|^2}$.

---

## Problem 3
**翻译题目：**
设 $G$ 是紧李群，$\chi: G \to \mathbb{C}^\times$ 是 $G$ 的一个连续特征。证明 $\int_G \chi(g) dg = 0$ 当且仅当 $\chi$ 是非平凡特征。

**详细的中文作答：**
（必要性）如果 $\chi$ 是平凡特征，即对所有 $g \in G$ 都有 $\chi(g) = 1$。因为 $G$ 是紧群，Haar 测度是有限的，所以 $\int_G 1 dg = \text{vol}(G) > 0$，因此积分不为零。
（充分性）如果 $\chi$ 是非平凡特征，则必然存在某个 $h \in G$，使得 $\chi(h) \neq 1$。
在积分 $\int_G \chi(g) dg$ 中，作换元 $g = hx$。由于 $dg$ 是左不变 Haar 测度，所以 $d(hx) = dx$。
于是有：
$\int_G \chi(g) dg = \int_G \chi(hx) dx = \int_G \chi(h)\chi(x) dx = \chi(h) \int_G \chi(x) dx$
移项得到：
$(1 - \chi(h)) \int_G \chi(g) dg = 0$
由于 $\chi(h) \neq 1$，即 $1 - \chi(h) \neq 0$，从而必然有 $\int_G \chi(g) dg = 0$。

**简短必要的英文作答：**
If $\chi$ is trivial, $\int_G \chi(g) dg = \text{vol}(G) > 0$. If $\chi$ is nontrivial, there exists $h \in G$ such that $\chi(h) \neq 1$. Using the left-invariance of Haar measure, $\int_G \chi(g) dg = \int_G \chi(hg) dg = \chi(h) \int_G \chi(g) dg$. Thus $(1-\chi(h))\int_G \chi(g) dg = 0$. Since $1-\chi(h) \neq 0$, the integral must be 0.

---

## Problem 4
**翻译题目：**
(a) 对 $\mathbb{R}$ 的所有酉特征进行分类。这里的 $\mathbb{R}$ 的酉特征指的是连续同态 $\chi: \mathbb{R} \to \mathbb{C}^\times$，且对所有 $a \in \mathbb{R}$ 都有 $|\chi(a)| = 1$。（提示：尝试对函数 $\int_x^{x+a} \chi(t)dt$ 求导并建立一个常微分方程。）
(b) 对 $S^1 \cong \mathbb{R}/\mathbb{Z}$ 的所有酉特征进行分类。（提示：应用同态 $\mathbb{R} \to \mathbb{R}/\mathbb{Z} \cong S^1$。）

**详细的中文作答：**
(a) 设 $\chi$ 是 $\mathbb{R}$ 的一个连续酉特征。因为它是同态，有 $\chi(t) \chi(a) = \chi(t+a)$。对 $t$ 积分得到 $\chi(a) \int_0^\epsilon \chi(t)dt = \int_0^\epsilon \chi(t+a)dt = \int_a^{a+\epsilon} \chi(u)du$。
因为 $\chi(0)=1$ 且连续，存在 $\epsilon > 0$ 使得 $\int_0^\epsilon \chi(t)dt \neq 0$。根据微积分基本定理，右侧 $\int_a^{a+\epsilon} \chi(u)du$ 作为 $a$ 的函数是可导的，这意味着 $\chi(a)$ 是可导的。
将 $\chi(x+y) = \chi(x)\chi(y)$ 两边对 $y$ 求导并令 $y=0$，得到 $\chi'(x) = \chi(x)\chi'(0)$。令 $\chi'(0) = k$，这是一个常系数线性微分方程，其唯一满足 $\chi(0)=1$ 的解为 $\chi(x) = e^{kx}$。
又因为 $|\chi(x)| = 1$，必有 $k$ 是纯虚数，即 $k = iy$，其中 $y \in \mathbb{R}$。所以所有酉特征的形如 $\chi_y(x) = e^{iyx}$，参数 $y \in \mathbb{R}$。

(b) $S^1 \cong \mathbb{R}/\mathbb{Z}$ 的酉特征对应于那些在核中包含 $\mathbb{Z}$ 的 $\mathbb{R}$ 的酉特征。即要求 $\chi_y(n) = 1$ 对所有 $n \in \mathbb{Z}$ 成立。
所以 $e^{iyn} = 1$ 对所有 $n \in \mathbb{Z}$ 成立。这要求 $y$ 必须是 $2\pi$ 的整数倍，即 $y = 2\pi k$ ($k \in \mathbb{Z}$)。
因此，$S^1$ 的所有酉特征形如 $\chi_k([x]) = e^{2\pi i k x}$，参数 $k \in \mathbb{Z}$。

**简短必要的英文作答：**
(a) A continuous homomorphism $\chi$ is differentiable by smoothing. Solving the ODE $\chi'(x) = \chi(x)\chi'(0)$ gives $\chi(x) = e^{kx}$. Since $|\chi(x)|=1$, $k=iy$ for $y \in \mathbb{R}$. So characters are $\chi_y(x) = e^{iyx}$ ($y \in \mathbb{R}$).
(b) Characters of $S^1 \cong \mathbb{R}/\mathbb{Z}$ must be trivial on $\mathbb{Z}$, meaning $e^{iy} = 1$, which requires $y = 2\pi k$ for $k \in \mathbb{Z}$. So the characters are $\chi_k([x]) = e^{2\pi i k x}$ ($k \in \mathbb{Z}$).

---

## Problem 5
**翻译题目：**
这是一个为下一个加分练习做准备的热身问题。证明 $SU(2)$ 中的每一个矩阵 $g$ 都可以写成如下乘积：
$g(\theta, \phi, \psi) = \begin{pmatrix} e^{i\psi} & 0 \\ 0 & e^{-i\psi} \end{pmatrix} \begin{pmatrix} \cos\theta & \sin\theta \\ -\sin\theta & \cos\theta \end{pmatrix} \begin{pmatrix} e^{i\phi} & 0 \\ 0 & e^{-i\phi} \end{pmatrix}$
其中 $\theta \in [0, \pi/2], \phi \in [0, \pi], \psi \in [-\pi, \pi]$。

**详细的中文作答：**
$SU(2)$ 中的任意元素都可以表示为 $g = \begin{pmatrix} a & b \\ -\bar{b} & \bar{a} \end{pmatrix}$，且满足 $|a|^2 + |b|^2 = 1$。
将题目中给定的三个矩阵相乘：
$\begin{pmatrix} e^{i\psi} & 0 \\ 0 & e^{-i\psi} \end{pmatrix} \begin{pmatrix} \cos\theta & \sin\theta \\ -\sin\theta & \cos\theta \end{pmatrix} \begin{pmatrix} e^{i\phi} & 0 \\ 0 & e^{-i\phi} \end{pmatrix} = \begin{pmatrix} e^{i(\psi+\phi)} \cos\theta & e^{i(\psi-\phi)} \sin\theta \\ -e^{-i(\psi-\phi)} \sin\theta & e^{-i(\psi+\phi)} \cos\theta \end{pmatrix}$
对比两式可以得到：
$a = e^{i(\psi+\phi)} \cos\theta$
$b = e^{i(\psi-\phi)} \sin\theta$
由于 $|a|^2 + |b|^2 = 1$，且要求 $\theta \in [0, \pi/2]$（此时 $\cos\theta, \sin\theta \ge 0$），所以可以直接取 $\theta = \arccos(|a|)$。这样就满足了 $|a| = \cos\theta$ 和 $|b| = \sin\theta$。
接着要满足相位。设 $a = |a|e^{i\alpha}$, $b = |b|e^{i\beta}$。只要选择 $\psi$ 和 $\phi$ 使得：
$\psi + \phi \equiv \alpha \pmod{2\pi}$
$\psi - \phi \equiv \beta \pmod{2\pi}$
我们可以在给定区间 $\phi \in [0, \pi], \psi \in [-\pi, \pi]$ 中找到一组解（如果边界取值可以加上对应的周期偏移），即可使所有矩阵如此分解。这就是著名的欧拉角分解。

**简短必要的英文作答：**
Multiplying the given matrices yields $\begin{pmatrix} e^{i(\psi+\phi)}\cos\theta & e^{i(\psi-\phi)}\sin\theta \\ -e^{-i(\psi-\phi)}\sin\theta & e^{-i(\psi+\phi)}\cos\theta \end{pmatrix}$. Any $g \in SU(2)$ is of the form $\begin{pmatrix} a & b \\ -\bar{b} & \bar{a} \end{pmatrix}$ with $|a|^2+|b|^2=1$. We can just match the magnitudes by letting $\theta = \arccos(|a|) \in [0, \pi/2]$, and match the phases by solving $\psi+\phi \equiv \arg(a)$ and $\psi-\phi \equiv \arg(b) \pmod{2\pi}$.

---

## Problem 6
**翻译题目：**
(加分题) 在课堂上，我们证明了 $SU(2)$ 微分同胚于一个球面。按照以下步骤写出 $SU(2)$ 上的一个 Haar 测度。
(a) $\mathbb{R}^4$ 的标准勒贝格测度限制在 $S^3$ 上时，是 $SO(4)$ 不变的。那个测度是什么（最好用笛卡尔坐标写出）？
(b) $SU(2)$ 的每个左平移都由一个旋转给出，即 $SO(4)$ 中的一个元素。因此 (a) 中的测度确实是 $SU(2)$ 的一个 Haar 测度。
(c) 使用问题 5 中的参数化写出一个 Haar 测度。（提示：在坐标变换时你需要计算雅可比行列式。）
(d) 如果我们将 $SU(2)$ 的总测度归一化为 1，证明以下积分公式：
$\int_{SU(2)} f(g) dg = \frac{1}{2\pi^2} \int_0^{\pi/2} \int_0^\pi \int_{-\pi}^\pi f(g(\theta, \phi, \psi)) \sin 2\theta d\psi d\phi d\theta$

**详细的中文作答：**
(a) 测度是由 $\mathbb{R}^4$ 中的体积形式 $dx_1 \wedge dx_2 \wedge dx_3 \wedge dx_4$ 与单位法向量场（欧拉向量场）收缩得到的，它在 $S^3$ 上的表达为：
$d\Omega = x_1 dx_2 \wedge dx_3 \wedge dx_4 - x_2 dx_1 \wedge dx_3 \wedge dx_4 + x_3 dx_1 \wedge dx_2 \wedge dx_4 - x_4 dx_1 \wedge dx_2 \wedge dx_3$。

(b) $SU(2)$ 作为流形同胚于 $S^3$。群 $SU(2)$ 在其自身上的左平移是等距同构，并且行列式为 1（因为群是连通的），所以对应于 $SO(4)$ 中的元素旋转。因为 $d\Omega$ 是 $SO(4)$ 不变的，它也就自然是在左平移下不变的，所以它是一个 Haar 测度。

(c) 使用欧拉角坐标参数化：
$x_1 + i x_2 = a = e^{i(\psi+\phi)}\cos\theta \implies x_1 = \cos(\psi+\phi)\cos\theta, x_2 = \sin(\psi+\phi)\cos\theta$
$x_3 + i x_4 = b = e^{i(\psi-\phi)}\sin\theta \implies x_3 = \cos(\psi-\phi)\sin\theta, x_4 = \sin(\psi-\phi)\sin\theta$
球面的诱导度量 $ds^2 = dx_1^2 + dx_2^2 + dx_3^2 + dx_4^2$。代入参数化坐标微分：
$ds^2 = d\theta^2 + \cos^2\theta d(\psi+\phi)^2 + \sin^2\theta d(\psi-\phi)^2 = d\theta^2 + d\psi^2 + d\phi^2 + 2\cos(2\theta)d\psi d\phi$。
黎曼流形上对应的体积形式为 $\sqrt{\det g} d\theta d\phi d\psi$。
计算度量张量的行列式：$\det g = 1 \cdot (1 - \cos^2(2\theta)) = \sin^2(2\theta)$。
因此 Haar 测度为 $\sin(2\theta) d\theta d\phi d\psi$。

(d) 为了归一化，我们计算全空间的体积：
$V = \int_0^{\pi/2} \int_0^\pi \int_{-\pi}^\pi \sin(2\theta) d\psi d\phi d\theta$。
$\int_{-\pi}^\pi d\psi = 2\pi$， $\int_0^\pi d\phi = \pi$。
$\int_0^{\pi/2} \sin(2\theta) d\theta = [-\frac{1}{2}\cos(2\theta)]_0^{\pi/2} = \frac{1}{2} - (-\frac{1}{2}) = 1$。
所以总测度为 $2\pi \times \pi \times 1 = 2\pi^2$。
当我们将测度除以 $2\pi^2$ 以达到归一化时，就证明了积分公式：
$\int_{SU(2)} f(g) dg = \frac{1}{2\pi^2} \int_0^{\pi/2} \int_0^\pi \int_{-\pi}^\pi f(g(\theta, \phi, \psi)) \sin 2\theta d\psi d\phi d\theta$。

**简短必要的英文作答：**
(a) The invariant volume form on $S^3$ is $d\Omega = x_1 dx_2 \wedge dx_3 \wedge dx_4 - \dots - x_4 dx_1 \wedge dx_2 \wedge dx_3$.
(b) Left translation by $SU(2)$ acts as isometries on $S^3$, giving $SO(4)$ matrices. Hence $d\Omega$ is left-invariant, making it a Haar measure.
(c) The induced metric on $S^3$ using the given parameters is $d\theta^2 + d\psi^2 + d\phi^2 + 2\cos(2\theta)d\psi d\phi$. The volume element is $\sqrt{\det g_{ij}} d\theta d\phi d\psi = \sin(2\theta) d\theta d\phi d\psi$.
(d) Integrating the measure gives the total volume $\int_0^{\pi/2} \sin(2\theta)d\theta \cdot \int_0^\pi d\phi \cdot \int_{-\pi}^\pi d\psi = 1 \cdot \pi \cdot 2\pi = 2\pi^2$. Normalizing by dividing by $2\pi^2$ yields the final integration formula.