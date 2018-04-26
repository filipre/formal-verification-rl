# Literature

## Adversarial Examples

- http://www.cleverhans.io/security/privacy/ml/2017/06/14/verification.html
    - The challenge of verification and testing of machine learning (Ian Goodfellow and Nicolas Papernot)
    - attack vs. defense
    - testing vs. validation
    - adversarial examples
    - "These current verification systems are limited in scope because they verify only that the output class remains constant in some specified neighborhood of some specific point x"
    - "no free lunch" theorem
    - "Challenges often encountered in machine learning—such as the need to generalize to new inputs—may make this a particularly difficult goal to achieve, as indicated by efforts cited in this post [PT10, HKW16, KBD17]"
    - fuzzing

- https://arxiv.org/pdf/1712.09344.pdf
    - Whatever Does Not Kill Deep Reinforcement Learning, Makes It Stronger
    - https://github.com/tensorflow/cleverhans/tree/master/examples/RL-attack
    - FGSM attacks on Deep Q-Networks (DQNs)

- https://blog.xix.ai/how-adversarial-attacks-work-87495b81da2d
    - How Adversarial Attacks Work
    - 590 claps

## Formal Verification

- https://en.wikipedia.org/wiki/Computation_tree_logic
    - Computation tree logic

- https://en.wikipedia.org/wiki/Probabilistic_CTL
    - Probabilistic Computation tree logic

- http://citeseerx.ist.psu.edu/viewdoc/download?doi=10.1.1.80.309&rep=rep1&type=pdf
    - FORMAL VERIFICATION OF PROBABILISTIC SYSTEMS
    - Markov Decision Process, Timed Probabilistic Systems, and Formal Verification

- https://arxiv.org/pdf/1402.2967.pdf
    - Verification of Markov Decision Processes using Learning Algorithms
    - ...

- Probabilistic Verification?

- https://www.reddit.com/r/MachineLearning/comments/77uuov/p_verification_of_reinforcement_learning/
    - "The idea is that if you know certain properties of your network should hold true on certain part of your input domain, you can formally verify that is the case. Things like "no adversarial examples at a distance of less than epsilon around a given point" or "never predict this class when these conditions are satisfied on the input" kind of thing. You can check out paper like "Reluplex" by Guy Katz et al. or "Formal verification of piecewise Linear Networks" by Ruediger Ehlers if you're interested. (Sorry for no link, am on mobile)"

- https://link.springer.com/article/10.1007%2Fs10489-017-0999-8
    - ???

- https://arxiv.org/pdf/1705.01320.pdf
    - Formal Verification of Piece-Wise Linear Feed-Forward Neural Networks
    - Other stuff: https://www.google.de/search?q=formal+verification+of+Deep*+Neural+Networks&rlz=1C5CHFA_enDE716DE716&oq=formal+verification+of+Deep*+Neural+Networks&aqs=chrome..69i57.509j0j7&sourceid=chrome&ie=UTF-8
    - **looks promising**

- https://arxiv.org/pdf/1702.01135.pdf
    - Reluplex: An Efficient SMT Solver for Verifying Deep Neural Networks
    - **also looks promising**
    - CAV2017 Conference (Computer Aided Verification): https://www.youtube.com/watch?v=KiKS_zaPb64

- https://www.youtube.com/watch?v=dc7W3rI2hdc
    - "Value Iteration for Long-run Average Reward in Markov Decision Processes" T. Meggendorfer | CAV
    - ???

- https://www.youtube.com/watch?v=XHdVnGxQBfQ
    - "Safety Verification of Deep Neural Networks" Marta Kwiatkowska | CAV 2017
    - 1h
    - **reference to Autonoumous driving**
    - references to SMT (Z3)
    - verification for a **given** image and a **given** network. Then show "most" extreme picture that makes it fail or not
    - unclear which neighborhood to choose from (they focused on "natural" pertubations?)
    - https://www.youtube.com/channel/UCe3M4Hc2hCeNGk54Dcbrbpw **<-- very nice**

- https://nfulton.org/papers/aaai18.pdf
    - Safe Reinforcement Learning via Formal Methods; Toward Safe Control Through Proof and Learning
    - aaai18

## Reinforcement Learning

- https://towardsdatascience.com/introduction-to-various-reinforcement-learning-algorithms-i-q-learning-sarsa-dqn-ddpg-72a5e0cb6287
    - Introduction to Various Reinforcement Learning Algorithms. Part I (Q-Learning, SARSA, DQN, DDPG)
    - 2k claps
    - very short, not 100% clear

## Classical Formal Verification (SAT, SMT)

- https://yurichev.com/writings/SAT_SMT_draft-EN.pdf
    - many examples how to solve problems using SMT.
    - context to verificataion: https://en.wikipedia.org/wiki/Satisfiability_modulo_theories#Verification
    - A common technique is to translate preconditions, postconditions, loop conditions, and assertions into SMT formulas in order to determine if all properties can hold.
    - "Another approach is deductive verification. It consists of generating from the system and its specifications (and possibly other annotations) a collection of mathematical proof obligations, the truth of which imply conformance of the system to its specification, and discharging these obligations using either interactive theorem provers (such as HOL, ACL2, Isabelle, Coq or PVS), automatic theorem provers, or satisfiability modulo theories (SMT) solvers. This approach has the disadvantage that it typically requires the user to understand in detail why the system works correctly, and to convey this information to the verification system, either in the form of a sequence of theorems to be proved or in the form of specifications of system components (e.g. functions or procedures) and perhaps subcomponents (such as loops or data structures)." Wikipedia Formal Verification

- https://www.microsoft.com/en-us/research/wp-content/uploads/2016/02/nbjorner-smt-application-chapter.pdf
    - how to use SMT for program verification
    - is this related to us? Do we care about the "implementation", about the algorithms or about the probability model?

## Questions:

- what does "formal verification" mean? define neighborhood of a point and see how it ends up?
- Do we care about the "implementation", about the algorithms or about the probability model?
- include program verification? or just model verification? (theory vs. implementation)
- which direction do we want to go?
    - focus on DNN
    - focus on MDP
- Formal vs. Probabilistic Verification?
- Which RL Algorithm should we focus on? Tabular-Learning (easy?), DQN (very hard)
- Should we link it with Autonoumous driving (only very lightly)
- can we make similar statemens like in DNN: "When being in this neighborhood, we don't have ..."
- Decidable vs. Undecidable.
- Survey or Research?
- Formal Verification of an already trained model?
- Or formal verificatiaon that a model can learn actually learn? Convergence Rate?
- Formal Verification of Algorithms or Implementations? (Algorithms, right?)
