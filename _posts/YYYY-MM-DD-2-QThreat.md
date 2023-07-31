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

The discrete logarithm problem is relevant in classical cryptography as it has been a good candidate for a trapdoor function. In fact, Diffie-Hellman key exchange, the first published public-key cryptographic
protocol is based in this problem.

The discrete logarithm problem can be explain as having G =<g> a cyclyc group generated by g, written multiplicaticately. Give an element x belonging to G, the discrete logarithm of x in G with respect to g, or log_g x is the smallest positive integer α such that g^α = x. So, the discrete logarithm problem is the problem of calculating log_g x.

This problem seems a good trapdoor function, as we can compute efficiently the g^α. But given x, we don't know of any classical calculation method that does the calculation of log_g x in polynomial time. And this is the reason why it has been at the foundation of classical security key exchange protocols.

This problem is a good fit again for Shor's algorithm, because as we saw before factoring a number N we were able to adapt it as the calculation of discrete log in (Z_N)^x. Now we have a cyclic G and we will need to know the order of G. This periodicity is the key again to apply later the QFT inverse primitive, that provides the same exponential speed up vs the classical alternative.

## Impact of Quantum Attacks on RSA

Recap the RSA encryption process based on the difficulty of factoring the product of two large primes.
Illustrate how Shor's algorithm can efficiently factorize the RSA modulus on a powerful quantum computer.
Emphasize that this would compromise the security of RSA encryption and enable adversaries to decipher encrypted messages.

The factoring problem involves finding the prime factors of a composite number. RSA (Rivest–Shamir–Adleman) encryption relies on the factoring problem, where the security of RSA encryption is based on the difficulty of factoring the product of two large prime numbers. Given a public RSA key, it is computationally infeasible for classical computers to factorize the modulus (a large semiprime number) and retrieve the private key, ensuring the security of encrypted messages.

## Impact of Quantum Attacks on ECC

Explain the mathematical foundation of ECC, which relies on the difficulty of solving the discrete logarithm problem on elliptic curves.
Describe how Shor's algorithm can efficiently solve this problem on a quantum computer.
Highlight that this quantum attack would undermine the security provided by ECC.
Quantum computers pose a serious threat to classical cryptographic systems, thanks to algorithms like Shor's algorithm. Shor's algorithm leverages the inherent quantum parallelism to efficiently factor large numbers and solve discrete logarithm problems. This could render widely-used encryption schemes like RSA and ECC vulnerable to attacks. The implications of quantum attacks highlight the urgent need for adopting Post-Quantum Cryptography to ensure data security in the quantum era.

# Harvest Now, Decrypt Later - HNDL
Harvest Now, Decrypt Later (HNDL) refers to the idea that a nation-state can gain access to currently encrypted data and store it until a reliable quantum computer appears and then decrypt all data at that later time.

In term of data security we have to decide if this is a threat for our data and act accordingly to mitigate it if applies.
To analyse if our data is in risk of HDNL we have to know or estimate the answer to the following questions:

- **How long should our encrypted data be secured?**
This demands to know well several internal aspects:
- the **kind of data** we protect and the motivation. In some cases can be fiscal records and these have regulation, others are more business oriented (IP, patents, designs...) which could require specific times and others can be more IT (logs, backups) for safety measures, and many times a mix of them in databases or application records with personal and individual information forcing to apply the most demanding regulation. Anyway, all sensible data should be protected and we would apply a different and specific time criteria to each kind. Obviously, this list must include the certificates and keys for encryption, too.
- the **security mechanisms implemented/used**. By knowing the previous sensible data inventory, we should identify the ways implemented to protect the data. This requires to map data with the protocols and their implementation. As we have seen previously, the systems using public key exchange like RSA or ECC, are affected by the quantum threat in a different way than symmetric key algorythms like AES. 
- the **time needed to move to quantum-resistant algorythms**. If we decide at any time to change the way we protect our data (for an specific protocol or several) to quantum-resistant ones, how long it will take this process? This time correlates the availability of inventories for security protocols, sensible data and the complexity of the implementations.

- **When we'll have around a reliable quantum computer powerful enough?**
This a very discussed question. While the theoretical implications on the Shor algorythm are out of any discussion, the possibilities to run it to crack any of the current classical protocols like RSA are none. 
The current development stage for quantum computers is searching ways to reduce noise, increase the coherence times for qubits and the total number of qubits contributing to calculation (logical qubits). This is why current quantum computers is said to be in the Noisy Intermediate Scale Quantum (NISQ) era.
Based on the current capabilities of existing quantum computers, these are far from pose a threat, but if we look in the progression they have and the increase of economical investments these last years and the ecosystem growth, and how the number of patents have accelerated, the time required is reducing fast. Depending on this the most optimistic ones talk around 5 years while others consider much more than a decade.

Anyway, if we get our answers from the previous questions, now we can easily deduce "when we need to start worrying". 
When “X” (the amount of time that we want our data to be protected), plus “Y” (the time we need to transition the security implementations from classical to quantum-resistant), is greater than “Z” (the time we estimate for quantum processors to have reached a development level enough to breach existing encryption protocols).

![Mosca Inequality](images/Mosca_Inequality.png)

This I've found to be defined as the Mosca's Inequality, proposed by Michele Mosca in April 2015. [See slide 20](https://csrc.nist.gov/csrc/media/events/workshop-on-cybersecurity-in-a-post-quantum-world/documents/presentations/session8-mosca-michele.pdf) 

# Conclusion:
Shor's algorithm is the first to demonstrate the immense computational power of quantum computers in solving specific problems exponentially faster than classical computers. The ability to efficiently factorize large semiprime numbers and solve discrete logarithm problems compromises the security of classical cryptographic systems like RSA and ECC. The fast development of quantum computing technology and the protection duration required by sensible data, puts on the table the need to react and move to quantum-resistant cryptographic algorithms, such as those in Post-Quantum Cryptography. This becomes increasingly critical to avoid security ensure long-term data security in the quantum era.




