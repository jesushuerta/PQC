# Post-Quantum Cryptography Fundamentals

## Introduction to Post-Quantum Cryptography

The term Post-Quantum Cryptography or PQC appears in the early 2000's and the first international workshop on this topic was the [PQCrypto 2006](https://postquantum.cr.yp.to/) conference covering this topic. The idea behind PQC is to identify cryptographical schemas able to run on classical computers and able to resist a quantum computer attack. It emerges as an effort to keep long term security on classical information systems by developping new algorythms. Let's see the fundamental principles and its diverse categories, based on their unique matematical construts

The content below:

[Categories of Post-Quantum Cryptographic Algorithms](#categories-of-post-quantum-cryptographic-algorithms)
- [Lattice-Based Cryptography](#lattice-based-cryptography)
- [Code-Based Cryptography](#code-based-cryptography)
- [Hash-Based Cryptography](#hash-based-cryptography)
- [Multivariate Cryptography](#multivariate-cryptography)

[Mathematical Basis of Post-Quantum Cryptographic Algorithms](#mathematical-basis-of-post-quantum-cryptographic-algorithms)
- [Lattice Problems and Complexity](#lattice-problems-and-complexity)
- [Error-Correcting Codes and Decoding](#error-correcting-codes-and-decoding)
- [Hash Functions and Collision Resistance](#hash-functions-and-collision-resistance)
- [Algebraic Equations and Polynomial Systems](#algebraic-equations-and-polynomial-systems)

[Conclusion](#conclusion)

## Categories of Post-Quantum Cryptographic Algorithms
Cryptographic systems can be classified in diverse categories depending on their security pilar, which is the reason of their security strentgh. There are many of these categories, but here the focus is in those that apparently could be the source for quantum-resistant algorythms. Others like the categories for public key exchange protocols that are broken by Shor's algorythm, such as factoring or discrete logs (Elliptic Curve Cryptography, ECC), are excluded.

### Lattice-Based Cryptography
Lattice-based cryptography in encryption and signatures harnesses the mathematical properties of lattices, which are highly structured grids of points in high-dimensional spaces. The lattice problems like finding short bases or vectors for typically special lattices, constitutes the basis for his security. Popular lattice-based algorithms include:

* **NTRU (N-th degree Truncated Polynomial Ring)**: NTRU is a lattice-based public-key encryption and digital signature scheme. NTRU's security foundation lies in searching the smallest length vector within an specific lattice structure and dealing with factorization of certain complex polynomials. This approach makes NTRU twice as fast as RSA for encryption and three times quicker when it comes to decryption.

* **NewHope**: An important feature of basing cryptography on the ring learning with errors problem is the fact that the solution to the RLWE problem can be used to solve a version of the shortest vector problem (SVP) in a lattice (a polynomial-time reduction from this SVP problem to the RLWE problem has been presented[1]).

### Code-Based Cryptography
Code-based cryptography relies on the computational hardness of decoding specific error-correcting codes. These codes are typically resistant to quantum attacks, making code-based schemes attractive for quantum-resistant cryptography. Key examples include:

* **McEliece Cryptosystem**: McEliece is a classic code-based encryption system based on the intractability of decoding random linear codes.

* **BIKE (Bit-flipping Key Encapsulation)**: BIKE is a code-based key encapsulation mechanism that offers strong security guarantees against quantum adversaries.

### Hash-Based Cryptography
Hash-based cryptography exploits the properties of hash functions, digital signatures, and Merkle trees to secure data and transactions. These schemes rely on the collision resistance of hash functions. Notable examples are:

* **XMSS (Extended Merkle Signature Scheme)**: XMSS is a hash-based signature scheme that provides forward security and post-quantum security.

* **SPHINCS (SPHINCS+)**: SPHINCS is a stateless hash-based signature scheme designed for practical use in a post-quantum setting.

### Multivariate Cryptography
Multivariate cryptography builds on the intractability of solving systems of multivariate polynomial equations. These schemes rely on the difficulty of finding the private key from a given public key. Major multivariate algorithms include:

* **HFE (Hidden Field Equations)**: HFE is a multivariate public-key cryptosystem that offers post-quantum security using complex algebraic equations.

* **Rainbow**: Rainbow is another multivariate signature scheme designed to provide quantum-resistant security.

## Mathematical Basis of Post-Quantum Cryptographic Algorithms

The security of Post-Quantum Cryptographic algorithms hinges on various mathematical assumptions and computational hardness problems. These problems often involve lattice structures, error-correcting codes, hash functions, and algebraic equations. The difficulty of solving these mathematical challenges forms the core of the security of Post-Quantum Cryptography.

### Lattice Problems and Complexity
Lattice problems, such as finding short vectors in high-dimensional spaces, are central to the security of lattice-based cryptographic schemes. Solving these problems is believed to be computationally intractable for both classical and quantum computers.

### Error-Correcting Codes and Decoding
Code-based cryptographic algorithms rely on the hardness of decoding random linear codes. The decoding process becomes exponentially challenging as the code size increases, leading to quantum-resistant security.

### Hash Functions and Collision Resistance
Hash-based cryptographic algorithms leverage the collision resistance property of hash functions, making it computationally infeasible to find two different inputs with the same hash value.

### Algebraic Equations and Polynomial Systems
Multivariate cryptographic algorithms use systems of multivariate polynomial equations that are difficult to solve, forming the basis of their security.

## Conclusion

Post-Quantum Cryptography presents a diverse array of cryptographic schemes, each designed to provide quantum-resistant security. These schemes rely on distinct mathematical constructs, such as lattices, error-correcting codes, hash functions, and algebraic equations. The security of Post-Quantum Cryptography is rooted in the computational hardness of these mathematical problems, ensuring that quantum adversaries cannot break the cryptographic schemes. In the next chapter, we will further explore the principles of Post-Quantum Cryptography and discuss the cryptographic agility required for a secure transition to the quantum-resistant era.




- Code-based encryption: McEliece cryptosystem has survived since 1978. Short ciphertexts and large public keys. Security relies on hardness of decoding error-correcting codes.
- Hash-based signatures: very solid security and small public keys. Require only a secure hash function (hard to find second preimages).
- Multivariate-quadratic signatures: short signatures and large public keys. Security relies on hardness of solving systems of multivariate equations over finite fields.
- Isogeny-based encryption: new kid on the block, promising short keys and ciphertexts and non-interactive key exchange. Security relies on hardness of finding isogenies between elliptic curves over finite fields.

Warning: These are categories of mathematical problems;
individual systems may be totally insecure if the problem is not used correctly.
