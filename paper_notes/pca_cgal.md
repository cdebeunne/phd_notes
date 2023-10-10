# Principal Component Analysis in CGAL

Author: Gupta

Year: 2008

Notes:
---
* How to compute the covariance of an arbitrary object?
* Each object has a canonical object $o_t$ whose covariance is known $M_{o_t}$
* e.g. : for a triangle $o_t = \{(0,0), (0,1), (1,0) \}$ and $M_{o_t} = [1/12, 1/24; 1/24, 1/12]$
* Then can recover the covariance for any object $u$ that can be obtain with an affine transformation of the canonical object $x_s = A_sx_o + V_s$, knowing the mass $m_s$ (ie the area or the volume), the center of mass $c_s$:
$$
M_s=\left(\frac{m_s}{m_o}\right)\left(A_s M_o A_s^T\right)+m_s\left(c_s V_s^T+V_s c_s^T-V_s V_s^T\right).
$$
* e.g. for a triangle  $
A_t=\left[\begin{array}{ll}
x_2-x_1 & x_3-x_1 \\
y_2-y_1 & y_3-y_1
\end{array}\right]
$, $V_t = [x_1, y_1 ]^T$, $m_0 = 1/2$ and $m_s = 1/2 |A_t|$ so:
$$
M_s=\left|A_t\right| A_t M_{o_t} A_t^T+\frac{1}{2}\left|A_t\right|\left(c_s V_t^T+V_t c_s^T-V_t V_t^T\right).
$$