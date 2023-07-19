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
        - given: 
            - ∇f(0, 0) = ⟨3,−1⟩
            - G(x, y) = f(sin(x2 + y2 − 1), xy^3 + ye^x)
            - ask ∇G(1, 0), df/dx = 1, df/dy=0
        - G(x, y) = f(sin(x^2 + y^2 - 1), xy^3 + ye^x)
        - ∂G/∂x = ∂f/∂x * ∂(sin(x^2 + y^2 - 1))/∂x + ∂f/∂y * ∂(xy^3 + ye^x)/∂x
        - ∂G/∂y = ∂f/∂x * ∂(sin(x^2 + y^2 - 1))/∂y + ∂f/∂y * ∂(xy^3 + ye^x)/∂y
        - Calculate the partial derivatives of f at the point (0, 0):
        - ∂f/∂x = 3
        - ∂f/∂y = -1
        - Substitute the values of the partial derivatives of f into the expressions for ∂G/∂x and ∂G/∂y.

- Q3
    - Find the directional derivative of f(x, y) = xexy + y2 at P = (0, 1) in the direction of maximal increase of the function g(x, y) = x3y2 at Q = (1,−1).

    - My Answer: 
        - Compute the gradient of the function g(x, y) at the point Q. The gradient of g(x, y) is given by: ∇g(x, y) = (∂g/∂x, ∂g/∂y)
        - f(x, y) = xexy + y2
        - P = (0, 1)
        - g(x, y) = x3y2
        - Q = (1,−1)
        - get U = (∇g(x, y)) / ||∇g(x, y)||
        - D_u(f) = ∇f(x, y) ⋅ U
        - ∇f(x, y) = (∂f/∂x, ∂f/∂y)
        - ∇f(x, y) at point P = (0, 1).

- Q4
    - Let c ∈ R be a constant and define f(x, y) = x2 + cxy + y2. Here we’ll examine how c affects the critical points of f.
    - (a) First, verify that f has a critical point at the origin (no matter what c is).
    - (b) For which values of c does f have a saddle point at the origin?
    - (c) For which values of c does f have a local min at the origin?
    - (d) For which values of c does f have a local max at the origin?

    - My Answer: 
        - Given:
            - f(x, y) = x2 + cxy + y2
            - how c affects the critical points of f.
            - find critical points
            - each situation
        - (a)
            - ∂f/∂x = 2x + cy
            - ∂f/∂y = cx + 2y
            - 2x + cy = 0 ...(1)
            - cx + 2y = 0 ...(2)
            - By substituting y = (-2/c)x from equation (2) into equation (1), we get:
            - 2x + c*(-2/c)x = 0
            - 2x - 2x = 0
            - 0 = 0
            - Since 0 = 0 is always true, it implies that any value of x and y satisfies equations (1) and (2), including x = 0 and y = 0. Therefore, f has a critical point at the origin (0, 0) for any value of c.
        - (b)
            - Second Derivative Test $D = fxxfyy-fxy^2$
                - D>0 and f_xx>0, local min
                - D>0 and f_xx<0, local max
                - D<0, saddle point
                - D=0, no information

- Q5
    - If f : R2 → R is twice continuously differentiable and has a local extreme at (a, b), show that fxx(a, b) and fyy(a, b) have the same sign.

    - My Answer: 
        - as local extreme at (a, b)
        - so must be
        - D>0 and f_xx>0, local min or
        - D>0 and f_xx<0, local max
        - either case, D>0, so fxxfyy-fxy^2 > 0, 
        - but -fxy^2 must be negative, only case is fxxfyy must be positive, so they must have same sign