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

# Small decryption exponent

# Common Modulus

# Blinding signature

# Issues faced
Working with large numbers meant that trying to obtain the cube root would result in overflow errors<br>
We implemented a function that takes advantage of the decimal module's high precision to compute 1/3 to a minimum of 27 digits (Going higher for larger numbers)<br>
To get the cube root of a large number, we would raise that number to the power of the high precision decimal form of 1/3 and round it

# Conclusion
