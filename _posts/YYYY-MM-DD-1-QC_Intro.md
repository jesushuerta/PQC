# Introduction to Quantum Computing and the Quantum Threat to Cryptography

## Classical Computing vs. Quantum Computing

In the world of computing, a new paradigm is emerging with promising capabilities although still with limitations: quantum computing. The existing one, classical computing, powers our everyday computers. This relies on bits, represented as 0s and 1s, as the fundamental unit of information. These bits process data sequentially, limiting computational power for certain complexity problems.

Quantum computing, on the other hand, relies on the minimal unit of quantum information, the quantum bit or qubit, as the quantum counterpart of a classical bit. Quantum computing leans on three main phenomena that make very special the qubits so special. These 3 phenomena are:
* **Superposition**: Qubits can exist in multiple states simultaneously, thanks to this phenomenon. This allows quantum computers to perform parallel computations, resulting in exponentially higher processing capabilities for specific tasks.
* **Interference**: This specific capability is stressed by the quantum algorithms like Shor or Grover. It uses constructive interference to amplify the correct solution(s) to the problem to compute, and it uses destructive interference to minimize all other possible outcomes.
* **Entanglement**: is a feature that interconnects two or more qubits and maintain their states correlated regardless of the distance between them. This makes the state of any qubit depends on all the others. This is especially important in quantum communications, but also in quantum computing as processing one single qubit we are acting on all others entangled at once.

![3 main quantum phenomena in quantum computing](./images/quantum_phenomena.gif)

## The Quantum Threat to Cryptography

Beyond the hype surrounding quantum computing, it comes with certain remarkable advancements solving some complex problems that are intractable right now by classical computing. It is precisely this power that poses a significant threat to the security of classical cryptographic systems that have safeguarded our sensitive data for decades. This quantum threat appears mainly due to a very ingenious quantum algorithm developped in 1994 by the mathemantician Peter Shor.

###     Shor's Algorithm

Shor's algorithm wasn't the first quantum algorithm, because others like Deutsch or Deutsch-Jozsa appeared before, but we can say without discussion that this algorithm was a demonstration that quantum computers could provide an exponential speed up vs. classical computers based on Turing machines. This algorithm was designed to efficiently factorize large numbers. No algorithm has been published that can factor all integers in polynomial time and it is clear that factoring is an NP problem. Therefore, factoring large semiprime numbers is a very computationally intensive task for classical computers. It is precisely this complexity the protection key of widely-used public-key encryption algorithms like RSA (Rivest–Shamir–Adleman) and ECC (Elliptic Curve Cryptography).

###     Quantum Attacks on RSA and ECC

Traditional cryptographic methods like RSA and ECC rely on trapdoor functions, mathematical problems or functions that are easy to compute in one direction, but difficult to compute in the opposite direction.

RSA encryption uses as trapdoor function the multiplication of prime numbers (cypher) and factorization semiprime (decryption). While it is ease to multiply large prime numbers to encrypt the message, and use these prime numbers later to recover or decrypt the message, it is extremely difficult or time consuming to factorize the resulting semiprime to get these prime numbers. So, the message is protected while these primes are only known by the emitter and authorized receivers. However, Shor's algorithm, when executed on a powerful enough quantum computer, can rapidly factorize the RSA modulus, breaking the encryption and compromising the confidentiality of encrypted messages.

Similarly, ECC, another extensively used cryptographic method, relies on the complexity of solving the discrete logarithm problem on elliptic curves. However, Shor's algorithm can efficiently solve this problem on a quantum computer, undermining the security provided by ECC.

## The Significance of Quantum-Resistant and Quantum Cryptography

The quantum threat to classical cryptographic systems requires a response to defed the protection of sensible data and information. Two different approaches appear here. One begins with the exploration and adoption of quantum-resistant cryptographic techniques - Post-Quantum Cryptography (PQC). Post-Quantum Cryptography is based on computational security, this means a new generation of cryptographic algorithms that run on classical computers, explicitly designed to withstand attacks from quantum computers. The alternative approach is quantum cryptography, that is based on (quantum) physical security. So, any implementation of quantum cryptography requires a hardware. The cryptographic paradigm for quantum cryptography is known as Quantum Key Distribution (QKD). 

###     Characteristics of Post-Quantum Cryptography

Post-Quantum Cryptographic algorithms are also rooted in trapdoor functions, but now the mathematical problems must remain challenging for both classical and quantum computers to solve. They provide a robust defense against quantum attacks, ensuring the security and confidentiality of sensitive data in the quantum era. NIST started in 2016 a PQC Standardization Process resulting in four algorithms to be standardized, but opened again in 2022 for more and will evaluate during 2023 the 40 candidates submitted.

###     Quantum Key Distribution
Quantum Key Distribution or QKD fights the quantum threat with quantum physics. The assumption here that relying on this quantum phenomena the security is intrisic, so there is no way a hacker using quantum power can beat quantum cryptography. But this is true in theory. The ltechnological loopholes in the physical implementation can be exploited by hackers to break the protocol. This approach is also new, but advancements are progressing fast.

###     Ensuring Long-Term Security

The importance of PQC and QKD lie in its capability to ensure long-term security in the future quantum age. Both approaches can coexist and for sure will evolve. As quantum computing technology matures, classical cryptographic systems could become vulnerable to attacks making the transition to quantum-resistant solutions imperative. Inclusive current PQC algorithms considered secure today could present flaws later. Any PQC strategy should include the capabilities to ease a continuous transition process between algorithms, what is called crypto agility framework.

## Conclusion

Quantum computing holds immense promise for various fields, but it poses a significant challenge to classical cryptographic systems. Mainly, Shor's algorithm threatens the security provided by RSA and ECC, calling for the adoption of Post-Quantum Cryptography to safeguard our data and communications in the quantum era. New quantum algorithms may appear in the future demanding an strategy able to help with this initial transition to PQC and potential algorithm updates.