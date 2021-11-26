# CZ4010-Cryptography-Project

This is a project conducted by Ong Yi Shen and Davin Ryo Tanada 
as the CZ4010 second semester project. This project involves demonstrations
of multiple potential attacks against the RSA cryptosystem.

The project will demonstrate the following attacks:
- Small encryption exponent
- Small decryption exponent
- Common Modulus
- Blinding signature

The attacks on textbook RSA are done on python running in jupyter notebook. These codes will be functional using Python 3.8.0 and newer.

# Small encryption exponent
This attack will work if both the message or encryption key is sufficiently small that M^e<N, where N=pq. This means that the ciphertext is simply M^e.
The attacker could perform an e-th root of the ciphertext, resulting in the message. This is especially vulnerable in larger size N's, where it will be likelier to have M^e being smaller than N.

This can be prevented by using a larger exponent, or padding M to match the size of N.
# Small decryption exponent
RSA is open to attacks in the decryption key being used is sufficiently small, since it can be tempting to use smaller d's for faster decryptions. Wiener's attack will succeed for d< 1/3(n^(1/4)). This is improved by Boneh and Durfee by requiring it to be less than n^0.292. Larger e's tend to mean small d's, although this is not always the case. 

The solution is by simply not using a small d.
# Common Modulus
This attack uses the modulus N as its weak spot. It requires two ciphertexts, both corresponding the same plaintext and N, but different encryption keys e1 and e2. The extended Euclidean algorithm will be performed on these two known encryption keys to extract two integers a1 and a2 so that e1a1+e2a2=1. The attacker will raise the messages to the power of a1 and a2 respectively. This results in M^(e1a1) mod N and M^(e2a2) mod N (either a1 and a2 will be negative, so the ciphertext with the negative a will be inversed mod N and then raised to the power of the absolute value of said a). Both of these values will be multiplied, and the result will be M mod N.

This can be prevented by switching N's after every message.
# Blinding signature
This has the attacker directly approaching the system. This involves RSA in signatures. Signatures will be the message raised to the power of d, so the attacker will send a message (M(R^e)). The returned signature will be (M(R^e))^d. R^ed will be R mod N, so the signature will be R(M^d). The attacker finishes this attack by dividing this signature with their R, resulting in M's signature, M^d.

The solution is to pad messages before signing.

# Issues faced
- Working with large numbers meant that trying to obtain the cube root would result in overflow errors
- We implemented a function that takes advantage of the decimal module's high precision to compute 1/3 to a minimum of 27 digits (Going higher for larger numbers)
- To get the cube root of a large number, we would raise that number to the power of the high precision decimal form of 1/3 and round it

# Conclusion
- While RSA is easy to implement, it is not advisable to create a cryptosystem from the ground up.
- As demonstrated, there are many pitfalls in RSA's implementation, leading to vulnerabilities.
- A good practice is to use secure cryptographic libraries in which their security has been proven to be sufficient.
