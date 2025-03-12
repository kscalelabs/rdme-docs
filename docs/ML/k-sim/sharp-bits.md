---
title: Debugging NANs
deprecated: false
hidden: false
metadata:
  robots: index
---
If you add new robot or testing training algorithm you might run into NANs. A good starting point is to see JAX [documentation](https://docs.jax.dev/en/latest/notebooks/Common_Gotchas_in_JAX.html#debugging-nans) how to approach analyzing them.

We have identified some common issues that cause NANs:

1. JAX cache reuse (remove the compilation cache)
2. Different machines (see [https://github.com/google/brax/issues/501](https://github.com/google/brax/issues/501))
3. MJX logic (additional forward pass helps stabilize the dynamics before step)
4. Appropriate XML definition (for example gain size on light joints)
5. Solver type, iteration steps, and physical timestamp