
# Securing Password: Strengthening Data Protection with OpenSSL in Kali Linux


<h2>Description</h2>
In this project, I've developed a robust system that harnesses the power of OpenSSL in the Kali Linux command line to generate unique and secure encryption passwords. OpenSSL is renowned for its wide range of network security capabilities, boasting secure implementations of various cryptographic protocols and algorithms. The primary goal of this project is to enhance security by encrypting the generated passwords under a master password, providing an additional layer of protection against unauthorized access.

The process involves creating and encrypting passwords using different ciphers, bolstering the overall security of the system. Additionally, the project ensures the utmost security for secret files by encrypting them, while never exposing or storing the plaintext passwords on the disk. A significant aspect of this project is its provision for securely exchanging passwords.
Moreover, the system facilitates secure sharing of encrypted contents with specific individuals, without revealing the underlying passwords. This approach allows users to retain control over who can access decrypted content while preserving the confidentiality of sensitive data.


<h2>Utilities Used</h2>

- <b>OpenSSL</b> 
- <b>Kali Linux</b>
- <b>Bash Shell</b>
- <b>Virtual Machine</b>
- <b>Salting</b>
- <b>Symmetric Cryptography</b>
- <b>AES-256</b>

<h2>Organization</h2>
<p align="left">
<b>Cyber Connexion Cohort 7 program - Fields Institute - University of Toronto </b>

<h2>Project walk-through:</h2>
<p align="left">

<h3>Sample</h3>

To begin the project, I establish a directory named "OpenSSL_lab." As a demonstration, I employ a generic bash command to randomly generate a 32-byte hex-encoded string. Subsequently, the string is encrypted using the AES-256-CBC cipher and saved to a file. To ensure robust security, the encryption process employs a password with secure key derivation.
<br />
<br />
<img src="https://github.com/sdkallullathil/Encription_OpenSSL/blob/57e8206fda88538d8c2734d091d05fc704032dc0/sampl3.png" height="90%" width="90%" alt="Disk Sanitization Steps"/>
<br />
<br />
The "-iter" option in OpenSSL necessitates an integer argument, leading the program to iterate the key derivation function multiple times. This approach enhances protection against dictionary attacks. A higher value passed to "iter" signifies a more secure setup, but it may also incur a performance cost. To further bolster security, it is recommended to add the "-pbkdf2" option, which employs a more secure key derivation function, making it a crucial step in the process.


<h3>Password Management</h3>
I have successfully generated three distinct AES-256-CBC encrypted files: password1.enc, password2.enc, and password3.enc. Each file contains the ciphertext of a unique randomly generated password. All these encrypted password files are securely stored in a designated subdirectory named "OpenSSL_Lab/Password". In the subsequent stages of the project, these passwords will play a crucial role in encrypting three different secret texts, ensuring data confidentiality and reinforcing the overall security of the system.
<br />
<br />
<img src="https://github.com/sdkallullathil/Encription_OpenSSL/blob/65ab69e510141b60beca4b33f0576e5b966497b8/pass3.png" height="90%" width="90%" alt="Disk Sanitization Steps"/>
<br />
In the provided command, the -salt option is utilized in conjunction with OpenSSL's AES-256-CBC encryption to introduce a random salt value into the encryption process. This salt serves as an additional input to the encryption algorithm, bolstering the overall security of the encryption process.

A noteworthy aspect of this project is the utilization of the same keys for all three passwords, which are stored in a file named "pass.txt" for convenience in the lab setting. It is essential to acknowledge that this practice of storing passwords in plain text is not recommended for real-life scenarios. In actual implementations, a password manager should be used to ensure stronger security and confidentiality. Nevertheless, for the purpose of this lab, this approach streamlines the process and eliminates the need for repetitive password input.


I proceeded by generating three text files named secret1.txt, secret2.txt, and secret3.txt, each containing distinct text of my choice. The content of these files was set to "Peanut," "Dumbbells," and "Tennis ball," respectively. All plaintext secret files have been diligently organized within a subdirectory called "OpenSSL Lab/Plaintexts." This ensures proper organization and management of the secret data within the project.
<br />
<br />
<img src="https://github.com/sdkallullathil/Encription_OpenSSL/blob/2392752403022dd9f415e44e7fafbb72b76bf081/plain.png" height="90%" width="90%" alt="Disk Sanitization Steps"/>
<br />
<br />
Next, I securely encrypt each of the secret files using the openssl enc command with the cipher -cast-cbc. To ensure utmost security, the i-th secret file is encrypted using the i-th generated password, ensuring that each file has a unique password. In this encryption process, I take care to embed the decryption command within the encryption command, preventing the exposure of plaintext passwords to the disk.
<br />
<br />
<img src="https://github.com/sdkallullathil/Encription_OpenSSL/blob/7015afa9914f2eb250bcd5f8b07a3bd0c4377dac/cipher.png" height="90%" width="90%" alt="Disk Sanitization Steps"/>
<br />
<br />

The encrypted secret files are then stored in a dedicated subdirectory named "OpenSSL_Lab/Ciphertexts." It is essential to note that the security of these encrypted files relies solely on the strength of the master password. In case of publication on the internet, potential adversaries would need to crack a 32-byte randomly generated password to decrypt the files, enhancing the overall security of the project.

<h3>Password Exchange</h3>

Currently, I possess three distinct secrets, each encrypted with a different password, all of which I can access using the same master password. Now, let's consider a scenario where I want to share "secret 2" exclusively with my friend Bob while keeping the other secrets secure. To achieve this, I opt not to modify or decrypt the file "secret2.txt." Instead, I prefer to share secure access to the unencrypted contents of "password2.enc" with my friend.

To accomplish this secure sharing, I create a new file in my password directory titled "password2_4Bob.enc." This file securely stores the encrypted contents of "password2.enc." However, it is encrypted again using the "aes-256-cbc" cipher under the password "SuperSecurePassword4Bob," which only I and Bob are aware of. Throughout this process, I ensure not to save the plaintext of my password on the disk, maintaining the highest level of security and confidentiality. This method allows me to share specific access to the unencrypted data with Bob, preserving the integrity of the original files.
<br />
<br />
<img src="https://github.com/sdkallullathil/Encription_OpenSSL/blob/ccf6564d780de3c9c02f386699cc169ea67b6416/bob.png" height="90%" width="90%" alt="Disk Sanitization Steps"/>
<br />
<br />
To validate the encryption process, I test the system by decrypting "secret2.txt." However, instead of directly accessing the "password2.enc" file, I access the contents of the "password2_4Bob.enc" file. This approach allows me to securely access and retrieve the necessary information from "secret2.txt" while utilizing the additional encryption layer provided by "password2_4Bob.enc."
<br />
<br />
<img src="https://github.com/sdkallullathil/Encription_OpenSSL/blob/f50ff83b3c2f461db248e827082e30d0db7079bf/tesing.png" height="90%" width="90%" alt="Disk Sanitization Steps"/>
<br />
<br />

<h3>Conclusion</h3>

In conclusion, this portfolio project has successfully developed a robust and secure system that leverages the power of OpenSSL in the Kali Linux command line. By harnessing OpenSSL's capabilities and cryptographic protocols, the system achieves the primary goal of enhancing security by generating unique and secure encryption passwords.

The implementation involves utilizing different ciphers to strengthen the overall security of the passwords and ensuring that secret files are securely encrypted without exposing plaintext passwords to the disk. Additionally, the system provides a secure method for exchanging passwords and enables users to securely share encrypted contents with specific individuals, safeguarding sensitive data while maintaining control over access.

Through this project, the importance of secure password management and encryption techniques is highlighted, serving as an effective approach to safeguarding sensitive information in real-world scenarios. The integration of OpenSSL in Kali Linux demonstrates its versatility and effectiveness in strengthening data protection, making it a valuable addition to any security-focused project or application.

