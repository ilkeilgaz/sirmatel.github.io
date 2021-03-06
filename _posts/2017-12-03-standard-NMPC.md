---
layout: post
title: Nonlinear model predictive control with MATLAB and CasADi
excerpt:
comments: true
category: blog
---

In this post we will study how to implement a nonlinear model predictive control (NMPC) scheme with MATLAB and CasADi. We will use the nonlinear system from Chen and Allgöwer (1998)[^Chen1998] as example, which has the following dynamics:

$$\begin{align*}
\dot{x}_1(t) & = x_2(t) + u(t) \left( \mu + (1 - \mu)x_1(t) \right) \\
\dot{x}_2(t) & = x_1(t) + u(t) \left( \mu - 4(1 - \mu)x_2(t) \right).
\end{align*}$$

NMPC involves finite horizon constrained nonlinear optimal control problems in the following form

$$\begin{align*}
\text{minimize} & \quad \int_{0}^{T}{\left\Vert x(t)\right\Vert^2_Q + \left\Vert u(t)\right\Vert^2_R} ~dt  \\
\text{subject to} & \quad x(0) = x_0 \\
& \quad \text{for } t \in [0,T]: \\
& \qquad \dot{x}(t) = f(x(t),u(t)) \\
& \qquad x(t) \in \mathcal{X} \\
& \qquad u(t) \in \mathcal{U},
\end{align*}$$

where $x(t) \in \mathcal{R}^n$ is the state, $u(t) \in \mathcal{R}^m$ is the control input, the function $f(\cdot)$ represents the dynamics, $\mathcal{X}$ and $\mathcal{U}$ are the sets expressing state and control input constraints, respectively, $x_0$ is the measurement, $T$ is the prediction horizon, whereas $Q \in \mathcal{R}^{n \times n}$ and $R \in \mathcal{R}^{m \times m}$ are matrices specifying the weights on the state and control input, respectively.

We first need to define the 

{% highlight ruby %}
def show
  @widget = Widget(params[:id])
  respond_to do |format|
    format.html # show.html.erb
    format.json { render json: @widget }
  end
end
{% endhighlight %}

[^Chen1998]: Chen, H., & Allgöwer, F. (1998). A Quasi-Infinite Horizon Nonlinear Model Predictive Control Scheme with Guaranteed Stability. Automatica, 34(10), 1205-1217. Available at: [https://engineering.purdue.edu/~zak/ECE680/Chen-Allgower_1998.pdf](https://engineering.purdue.edu/~zak/ECE680/Chen-Allgower_1998.pdf).













