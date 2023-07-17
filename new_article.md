title: MAT232 - Calculus of Several Variables - maximum and minimum values + Lagrange multipliers
# title: MAT232 - Calculus of Several Variables - maximum and minimum values + Lagrange multipliers


- Q1:
    - Let f : Rn → R and α : R → Rn be differentiable functions. Show that (f ◦ α)′(t) = ∇f(α(t)) · α′(t)
    - My Answer: 
        - z=f(x,y) and a(t)=<g(t), h(t)>
        - by chain rule,we have
        - [f(a(t))]'= df/dx * dx/dt + df/dy*dy/dt
        - gradient f(x,y) = <df/dx, df/dy>
        - a'(t) = <g'(t), h'(t)>
        - y=h(t)
            - dy/dt = h'(t)
        - x=g(t) -> dx/dt=g'(t)
        - = <df/dx, df/dg> * <g'(x), h'(x)>
        - gradient f(a(t)) * a'(t)
- Q2
    - Suppose f : R2 → R is a differentiable function such that ∇f(0, 0) = ⟨3,−1⟩. If G(x, y) = f(sin(x2 + y2 − 1), xy^3 + ye^x), compute ∇G(1, 0).
    - My Answer: 
        - 

- Q3
    - Find the directional derivative of f(x, y) = xexy + y2 at P = (0, 1) in the direction of maximal increase of the function g(x, y) = x3y2 at Q = (1,−1).

    - My Answer: 
        - 
```

```
Q4
Let c ∈ R be a constant and define f(x, y) = x2 + cxy + y2. Here we’ll examine how c
affects the critical points of f.
(a) First, verify that f has a critical point at the origin (no matter what c is).
(b) For which values of c does f have a saddle point at the origin?
(c) For which values of c does f have a local min at the origin?
(d) For which values of c does f have a local max at the origin?

My Answer: 
```

```
Q5
If f : R2 → R is twice continuously differentiable and has a local extreme at (a, b), show that fxx(a, b) and fyy(a, b) have the same sign.

My Answer: 
```