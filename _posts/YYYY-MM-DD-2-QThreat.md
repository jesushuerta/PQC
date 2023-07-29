# Quantum Threat and Cryptanalysis

Let's explore here in more detail the quantum threat to classical cryptographic systems and the well-known algorithm that poses a significant risk to their security - Shor's algorithm. Understanding the implications of quantum attacks on widely-used encryption schemes like RSA, ECC and others will highlight the need to move to quantum-resistant cryptographic solutions. Knowing how long the data has to be protected and guessing a date for potential availability of reliable quantum computers, the urgency for action is revealed. But let's go step by step.

## Quantum Threat to Classical Cryptographic Systems

Define the quantum threat as the potential of quantum computers to break classical cryptographic schemes efficiently.
Discuss how quantum computers exploit certain mathematical properties to outperform classical computers in specific computations.
Explain that the realization of large-scale quantum computers poses a significant risk to the security of classical encryption.

## Introducing Shor's Algorithm

Around 1990 quantum computers were only a theoretical idea on which many academical minds were working, after their first introduction by Richard Feynman one decade before. At this moment, this new computer was considered only to avoid the difficulties that classical computers have to simulate quantum mechanical systems. The proposal was to create a new computer based on the quantum mechanics principles and this way avoid the usual restrictions imposed on simulations running on classical computers. So, the initial purpose devised for quantum computers was physics simulation. 
Although other algorithms appeared before, it was the Shor's algorithm, proposed in 1994 by mathematician Peter Shor, which opened the possibility to use the quantum computation to calculate easily other problems that aren't easy for traditional computers. To be precise, the Shor's algorithm is able to factorize large numbers in polinomial time. This is an exponential speed up versus the best algorithm known today to factorize on classical computation. Shor's algorithm solves also easily discrete logarithm problems, which is also an NP problem.
Precisely, the complexity related with solving these factorization and discrete logarithm problems were at the foundation for some cryptographic schemas, as these functions were the complex direction of their trapdoors funcions. Any eavesdropper using a classical computer will find these problems computationally hard, but now with a reliable quantum computer would be able to do these tasks exponentially faster. Therefore, the cryptographic schemes using this functions, such as RSA and ECC will not be secure when these new computers are ready. Shor's algorithm demonstrates the potential of quantum computers to solve specific problems exponentially faster than classical computers, highlighting the quantum threat to classical cryptography, and opening a broad research field around quantum algorithms and complexity problems.

## Shor's Algorithm for Factoring

Let's go in deep with the factoring problem and how Shor's algorithm solves it so fast.
Obviously, it will leverage quantum primitives, parallelism and quantum Fourier transform, to factorize semiprime numbers.
The steps involved are
- quantum period finding 
- quantum Fourier transform
- classical post-processing.
Demonstrate how Shor's algorithm significantly reduces the computational effort required to factorize large numbers compared to classical methods.

### Quantum Period Finding:

Select a random number 'a' between 1 and N-1, where N is the semiprime number to be factored.
Compute the value of 'a^x mod N' for a set of increasing powers of 'x' until finding a value of 'r' where 'a^r mod N = 1'.

### Quantum Fourier Transform (QFT):

Represent 'r' as a fraction 'p/q' in binary notation.
Use QFT to find the period 'r' by estimating 'q' and approximating 'p/q'.

### Classical Post-Processing:

Use continued fraction expansion to obtain the most probable 'q' and 'p/q' values.
If 'q' is even and 'a^(r/2) mod N ≠ N-1', then the factors of N are 'gcd(a^(r/2) ± 1, N)'.
The key insight behind Shor's algorithm is that the quantum Fourier transform enables the quantum computer to find the period 'r' much faster than classical algorithms. The period 'r' reveals valuable information about the factors of N, leading to the factorization of the original semiprime number.



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




