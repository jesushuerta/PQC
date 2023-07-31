# Quantum Threat and Cryptanalysis

Let's explore here in more detail the quantum threat to classical cryptographic systems and the well-known algorithm that poses a significant risk to their security - Shor's algorithm. Understanding the implications of quantum attacks on widely-used encryption schemes like RSA, ECC and others will highlight the need to move to quantum-resistant cryptographic solutions. Knowing how long the data has to be protected and guessing a date for potential availability of reliable quantum computers, the urgency for action is revealed. But let's go step by step.

## Quantum Threat to Classical Cryptographic Systems

Define the quantum threat as the potential of quantum computers to break classical cryptographic schemes efficiently.
Discuss how quantum computers exploit certain mathematical properties to outperform classical computers in specific computations.
Explain that the realization of large-scale quantum computers poses a significant risk to the security of classical encryption.

## Introducing Shor's Algorithm

Around 1990 quantum computers were only a theoretical idea on which many academical minds were working, after their first introduction by Richard Feynman one decade before. At this moment, this new computer was considered only to avoid the difficulties that classical computers have to simulate quantum mechanical systems. The proposal was to create a new computer based on the quantum mechanics principles and this way avoid the usual restrictions imposed on simulations running on classical computers. So, the initial purpose devised for quantum computers was physics simulation. 
Although other algorithms appeared before, it was the Shor's algorithm, proposed in 1994 by mathematician Peter Shor, which opened the possibility to use the quantum computation to calculate easily other problems that aren't easy for traditional computers. To be precise, the Shor's algorithm is able to factorize large numbers in polinomial time as it uses less steps to do it. This is an exponential speed up versus the best algorithm known today to factorize on classical computation. Shor's algorithm solves also easily discrete logarithm problems, which is also an NP problem.
Precisely, the complexity related with solving these factorization and discrete logarithm problems were at the foundation for some cryptographic schemas, as these functions were the protection as the complex direction of their trapdoors funcions. Any eavesdropper using a classical computer will find these problems computationally hard, but now with a reliable quantum computer would be able to do these tasks exponentially faster. Therefore, the cryptographic schemes using this functions, such as RSA and ECC will not be secure when these new computers are ready. Shor's algorithm demonstrates the potential of quantum computers to solve specific problems exponentially faster than classical computers, highlighting the quantum threat to classical cryptography, and opening a broad research field around quantum algorithms and complexity problems.

## Shor's Algorithm for Factoring

Let's see whay the factoring problem is solved by Shor's algorithm so fast.
Our factoring problem starts with a known number N, such that N=p*q, where p and q are positive prime numbers we want to find.

There are several ideas that Shor introduce to solve this, first is to associate the factoring problem with finding the order of a function.

Consider a number x co-prime with N and let's consider a function x^r mod N. The order of this function will be the smallest r that accomplish: 
```console
x^r mod N = 1
```

Where is the relationship between this and the factoring problem?

Supose we can find that r is equal to 2 and therefore 
```console
x^2 mod N = 1 (1<x<N-1)
```
Then
```console
x^2 - 1 mod N = x^2 - 1 = 0 (N)
(x+1)(x-1) = 0 (N)
```

So, this means that x+1 or x-1 is a divider of N, and therefore it is one of our solutions p or q.


How then we proceed to do the calculation?

Let's select a random number "a" co-prime with N, and we search the order for a^r Mod N.
Here we can have a solution where r is pair or odd:
- r is pair ==> the solution is x = a^(r/2)
- r is odd ==> we start again selecting a different "a" number co-prime

This function is a periodic one, and we can observe the repetitive pattern shown in an example for a=3 and N=55 in the picture:

![periodic function](images/periodic_function.jpg)

The periodiciy in the example is r=20. Other values will produce a different line, but it will be again a repetitive pattern, and we will have another r value.

This periodicity is key here as the problem has turn from find the factors to find a frequency multiple of two for this function.

The algorithm has three main stages:
- **quantum period finding**: used to identify the repetitive pattern lenghts 
- **quantum Fourier transform**: here the periodicities are converted to frequencies, and here rely the speed up of the algorithm as a classical Fourier transform takes around N log(N) = n*2^n steps to Fourier transform N =  2^n numbers, while the quantum equivalent can be done with only log^2(N) = n^2 steps. This is exponential advantage.
- **classical post-processing**: the result (frequency) measured will be processed using the fraction continues method to get the final result.

## Shor's Algorithm for Discrete Logarithms

Explore how Shor's algorithm can be adapted to solve the discrete logarithm problem.
Describe the quantum parallelism that allows quantum computers to search through multiple possible solutions simultaneously.
Show how Shor's algorithm's exponential speedup breaks the computational hardness of discrete logarithms.

## Impact of Quantum Attacks on RSA

Recap the RSA encryption process based on the difficulty of factoring the product of two large primes.
Illustrate how Shor's algorithm can efficiently factorize the RSA modulus on a powerful quantum computer.
Emphasize that this would compromise the security of RSA encryption and enable adversaries to decipher encrypted messages.

The factoring problem involves finding the prime factors of a composite number. RSA (Rivest–Shamir–Adleman) encryption relies on the factoring problem, where the security of RSA encryption is based on the difficulty of factoring the product of two large prime numbers. Given a public RSA key, it is computationally infeasible for classical computers to factorize the modulus (a large semiprime number) and retrieve the private key, ensuring the security of encrypted messages.

## Impact of Quantum Attacks on ECC

Explain the mathematical foundation of ECC, which relies on the difficulty of solving the discrete logarithm problem on elliptic curves.
Describe how Shor's algorithm can efficiently solve this problem on a quantum computer.
Highlight that this quantum attack would undermine the security provided by ECC.

Teacher's Explanation:
Quantum computers pose a serious threat to classical cryptographic systems, thanks to algorithms like Shor's algorithm. Shor's algorithm leverages the inherent quantum parallelism to efficiently factor large numbers and solve discrete logarithm problems. This could render widely-used encryption schemes like RSA and ECC vulnerable to attacks. The implications of quantum attacks highlight the urgent need for adopting Post-Quantum Cryptography to ensure data security in the quantum era.

Teacher's Question:
Based on what we've discussed today, why is it crucial to explore cryptographic solutions that can resist quantum attacks, and how can Post-Quantum Cryptography address this challenge?

---------





The Discrete Logarithm Problem and ECC:
The discrete logarithm problem involves finding the exponent 'x' in the equation 'g^x ≡ h (mod p)', where 'g' is a generator of a finite cyclic group, 'h' is a given element in the group, and 'p' is a large prime number. Discrete logarithm forms the basis of elliptic curve cryptography (ECC), where the security of ECC relies on the difficulty of solving this problem.

Shor's Algorithm for Discrete Logarithms:
Shor's algorithm can be adapted to solve the discrete logarithm problem on elliptic curves. The steps are similar to those for factoring, with the key difference being the quantum period finding step for the discrete logarithm problem.

Conclusion:
Shor's algorithm demonstrates the immense computational power of quantum computers in solving specific problems exponentially faster than classical computers. The ability to efficiently factorize large semiprime numbers and solve discrete logarithm problems undermines the security of classical cryptographic systems like RSA and ECC. As quantum computing technology progresses, the need for quantum-resistant cryptographic algorithms, such as those in Post-Quantum Cryptography, becomes increasingly critical to ensure long-term data security in the quantum era.




