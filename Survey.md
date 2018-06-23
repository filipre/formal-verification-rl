*Notes!! Most of the text is copied and not our own words*

# Challenges in the Verification of Reinforcement Learning Algorithms

- Assumptions: Environment, Platform, Data, Algorithm

- **verification conditions**> from a suitably annotated program and allow the user to complete the proof by applying fully automated proof tools such as CVC4 [3] and Z3
- **Model checking**: unreachability of bad states via state space exploration
Verification of Markov Decision Processes using Learning Algorithms
- **Problem**: Machine Learning Algorithms are not fixed but change depending on the data they learn from
- Probabilistic model checking
- Runtime Verification (RV) [20,25,37], where monitors detect and respond to property violations at runtime
- **Problem**: Designing specifications

- Verification of Offline Learners: After training, the algorithm does not change anymore and verification can be done offline. Model behaves deterministic.
- Verification of Online Learners:
    - monitor for violations of the specified assumptions to ensure the system is operating in the environment considered in its specification and training.

- Model-based: Model is given, e.g. as a MDP. After taking an action a, only certain actions are possible
- Model-Free Learning: no model of the environment and system response is known. There- fore any action is possible in any state, and any action can lead to any other state.
    - model can be learned while learning, but heavily depending on training data
    - usually the case for Atari Games, ...

**Problem** Predictability/Exploration Conflict

## What can be Verified

- Offline
    - State to action mappings: “From all states in this set, never do this action”
    - Action sequences: Assuming the environment model is in the form of a Markov decision process, requirements can be verified in some probabilistic temporal logic specification -> PRISM
    - Algorithm properties independent of data: e.g. Convergence
    - Validating assumptions on training data: independence, id. sampled, variable ranges, skewness, ...

- Online / During Runtime
    - State to action mappings
    - Action sequences
    - Monitoring (violations of) assumptions.
    - Input instance in training data: Find out, when there is an unknown situation that wasn't in the data. **The question how to check if an instance of data was present in the input data is tricky however.**

## Related Work

- Thrun [41]: This method propagates bounds on input variables through the network to produce a bound on the output variable(s)
- Katz et al. [24]: suggests a method to extend SMT solvers, allowing for the verification of constraints on deep neural networks.

# Safe Model-based Reinforcement Learning with Stability Guarantees

- intermediate policies may be unsafe, break the system, or harm their environment.
- ... needs to consider its ability to safely recover from exploratory actions
- This ability to recover is known as asymptotic stability in control theory [4]. Specifically, we care about the region of attraction of the closed-loop system under a policy. This is a subset of the state space that is forward invariant so that any state trajectory that starts within this set stays within it for all times and converges to a goal state eventually.
- **starting from an initial, safe policy we can expand our estimate of the region of attraction by collecting data inside the safe region and adapt the policy to both increase the region of attraction and improve control performance**
- The goal is to safely learn about the dynamics from measurements and adapt the policy for perfor- mance, without encountering system failures
- Thus, the policy not only defines performance as in typical RL, but also determines safety and where we can obtain measurements.

- see Figure 1 for explanation. They use a specific function well known in control theory:
Lyapunov function To satisfy the specified safety constraints for safe learning, we require a tool to determine whether individual states and actions are safe. In control theory, this safety is defined through the region of attraction, which can be computed for a fixed policy using Lyapunov functions [4].

## Related Work

- In risk-sensitive RL, one specifies risk-aversion in the reward [7]
- Both [11] and [12] introduce algorithms to safely explore MDPs so that the agent never gets stuck without safe actions. All these methods require an accurate probabilistic model of the system.
- High-probability worst-case safety guarantees are available for methods based on Bayesian optimiza- tion [15] together with Gaussian process models (GP, [16]) of the cost function.
- In [20, 21], a priori known, safe global backup policies are used, while [22] learns to switch between several safe policies. **Problem**: Getting to these safe policies in the first place
- Other approaches use model predictive control with constraints, a model-based technique where the control actions are optimized online.
- **fixed control theory**: In control, stability of a known system can be verified using a Lyapunov function [27], ...


# Safe Reinforcement Learning via Formal Methods

- even the best models are incomplete.
- best of both worlds: the exploration and op- timization capabilities of learning along with the safety guar- antees of formal verification.
- runtime monitoring
- When a model violation is detected, the agent abandons ef- ficiency and instead attempts to learn a control strategy that guides the agent to a modeled portion of the state space.
- Justified Speculative Control (JSC): combines verified runtime monitoring – backed by formally verified models – with reinforcement learning.
    - no modeling inaccuracy: actions are constrained to a set of veri- fied control actions
    - modeling inaccuracy is detected: system is justified in taking actions that are unverified and possibly unsafe with respect to the (inaccurate) model.
- Verification results establish the safety of a set of actions, but do not solve the optimization problem
- usage of KeYmaera X (Fulton et al. 2015) for differential dynamic logic (Platzer 2008; 2012b; 2012a; 2017) to verify the CPS controller for its model.
- Controller Monitors: that monitor whether or not the controller portion of a hybrid systems model has been violated.
    - CM : S × A → Bool
- Model monitor:
    - MM : S × A × S → Bool
- we distinguish between optimizing among known safe policy options and speculating about portions of the state space that are not a priori modeled
- strength: we leverage formal verification, and preserve these results during exploration.

## Reinforcement Learning

- The safety results in this paper consider a completely generic approach.
- Model Monitors check if the model is correct / modeled correctly
- Controller Monitor check if an action is safe

```
JSCGeneric(init, (S,A,R,E), choose, update, done, CM, MM) {
  prev := curr := init;
  a0   := NOP;
  while (!done(curr)) {
    if (MM(prev, a0, curr))
      u := choose({a ∈ A | CM(a,curr)});
    else
      u := choose(A);
    prev := curr;
    curr := E(u, prev);
    update(prev, u, curr);
  }
}
```

- The paper proves that any safe action will keep the system safe

## Use Case: Adaptive Cruise Control

- it explains, how to model this


## Related Work

- Simplex
- There are a myriad of approaches toward safe reinforce- ment learning that do not take advantage of formal verifica- tion. Many of these approaches are summarized in (Garc ́ıa and Ferna ́ndez 2015),
  - modification of the optimality criterion
  - modification of the exploration process.
- the agent may only choose from a set of control actions that are a priori known to be safe (Garc ́ıa and Ferna ́ndez 2015). There are several approaches with this ba- sic flavor (Kadota, Kurano, and Yasuda 2006; Geibel 2006; Moldovan and Abbeel 2012).
- another: adopts worst case criterion (Heger 1994) or risk-sensitive criterion (Tamar, Xu, and Mannor 2013; Nilim and Ghaoui 2005), in which the optimization criterion is modified to re- flect safety concerns.
- analysis of the policy constructed from a learning process (Katz et al. 2017). These approaches are appropriate when the learning phase is not safety-critical, but not appropriate when the system must behave safely while learning.


# A Comprehensive Survey on Safe Reinforcement Learning

- Safe RL
  - Optimization Criterion
    - Worst Case Criterion
      - due to inherent uncertainty [...] and parameter uncertainty [...]
    - Risk Sensitive Criterion
    - Constrained Criterion
    - Other Optimization Criteria
  - Exploration Process
    - External Knowledge
      - Providing Initial Knowledge
      - Deriving a Policy from Demonstrations
      - Teacher Advice
    - Risk-directed Exploration















# General Notes

## Problems:

- most RL algorithms use function approximations
- Predictability/Exploration Conflict

## Our assumptions:

- Specifications are given by an autonomous driving expert (-> refer to literature)
