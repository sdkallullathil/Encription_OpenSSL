
# Secure Encryption Passwords with OpenSS


<h2>Description</h2>
In this portfolio project, I have developed a robust system that utilizes OpenSSL in the Kali Linux command line to generate unique and secure encryption passwords. OpenSSL is a powerful tool renowned for its wide range of network security capabilities, including secure implementations of various cryptographic protocols and algorithms. The core objective of this project is to enhance security by encrypting the generated passwords under a master password. This additional layer of encryption ensures that the passwords themselves remain secure and protected from unauthorized access.The process involves creating and encrypting passwords using different ciphers to bolster the overall security. Additionally, the system effectively safeguards secret files by encrypting them and ensures that the plaintext passwords are never exposed or stored on the disk.<br/><br/>

Furthermore, the system provides a secure method for sharing encrypted contents with specific individuals without revealing the underlying passwords. By employing this approach, users can maintain control over who can access the decrypted content while preserving the confidentiality of sensitive data. In conclusion, this portfolio project showcases the implementation of a comprehensive and secure encryption password system utilizing OpenSSL. The integration of various cryptographic techniques strengthens data protection, making it suitable for safeguarding sensitive information in real-world applications.


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
<img src="https://github.com/sdkallullathil/Encription_OpenSSL/blob/a9f7ebb48db698797b1d1a5eee224b4bf09085e2/sample1.png" height="90%" width="90%" alt="Disk Sanitization Steps"/>
<br />
<br />
The "-iter" option in OpenSSL necessitates an integer argument, leading the program to iterate the key derivation function multiple times. This approach enhances protection against dictionary attacks. A higher value passed to "iter" signifies a more secure setup, but it may also incur a performance cost. To further bolster security, it is recommended to add the "-pbkdf2" option, which employs a more secure key derivation function, making it a crucial step in the process.


<h3>Password Management</h3>
I have successfully generated three distinct AES-256-CBC encrypted files: password1.enc, password2.enc, and password3.enc. Each file contains the ciphertext of a unique randomly generated password. All these encrypted password files are securely stored in a designated subdirectory named "OpenSSL_Lab/Password". In the subsequent stages of the project, these passwords will play a crucial role in encrypting three different secret texts, ensuring data confidentiality and reinforcing the overall security of the system.
<br />
<br />
<img src="https://github.com/sdkallullathil/Encription_OpenSSL/blob/b65cc4bc423527d2cb6d56a906407e696ad4d9e5/pass.png" height="90%" width="90%" alt="Disk Sanitization Steps"/>
<br />
<br />

For convenience in this lab setting, I have employed the same keys for all three passwords, which are stored in a file named "pass.txt." It's important to note that this practice of storing passwords in plain text is not recommended in real-life scenarios. In actual implementations, I would use a password manager to ensure stronger security and confidentiality. However, for the purpose of this lab, it simplifies the process and avoids the need to repeatedly type the password.


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

<h3>Monitoring</h3>

To ensure the files' hash values remain unchanged over time, I implement a continuous monitoring mechanism. The process involves calculating the hashes of all files in the targeted folder every 10 seconds using PowerShell's "Start-Sleep" command for efficient timing. These calculated hashes serve as the keys, which I then use to compare against the previously stored values in the dictionary.

<br />
<br />
<img src="https://github.com/sdkallullathil/Powershell_project/blob/8126c957742c5b2c5c5eec75396dd761fd7c3056/script.png" height="90%" width="90%" alt="Disk Sanitization Steps"/>
<br />
<br />

By continuously comparing the latest hash values with their corresponding baseline entries in the dictionary, I can promptly detect any alterations or modifications to the files. This approach allows me to maintain the integrity and security of the files within the folder and ensures that any discrepancies are promptly identified and addressed.

The File Integrity Monitor has three key monitoring functionalities,<br /><br />
<b>Change Detection</b>
<br /> 
The program periodically calculates and compares the file hashes with their previously recorded values. If any modifications are made to the files, the program quickly identifies the changes by detecting differences in the hash values. When a file's hash differs from its previous value, the program generates an alert to notify the user about the detected change. This proactive approach helps users respond promptly to any unauthorized alterations or data tampering.
<br />
<br />
<br />
The content in the file "d.txt" before editing.
<br />
<img src="https://github.com/sdkallullathil/Powershell_project/blob/de35fe0025e8ca26173a321b9f7116add473b45f/textnochange.png" height="90%" width="90%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
<br />
The output of the monitor.
<br />
<img src="https://github.com/sdkallullathil/Powershell_project/blob/873207275d29be02010f65ddcc68d88ff74edddc/nochange.png" height="90%" width="90%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
<br />
The content in the file "d.txt" after editing.
<br />
<br />
<br />
<br />
<img src="https://github.com/sdkallullathil/Powershell_project/blob/d44a212d8a301f37fa45189bab214bf0c77b903b/textxhange.png" height="90%" width="90%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
<br />
The output of the monitor.
<br />
<br />
<br />
<br />
<img src="https://github.com/sdkallullathil/Powershell_project/blob/1bf9ed487286ebbcbee4ae69949738d46705e271/change.png" height="90%" width="90%" alt="Disk Sanitization Steps"/>
<br />
<br />
<b>New File Monitoring</b>
<br />
The File Integrity Monitor is equipped to handle new files added to the monitored folder. Whenever a new file is detected, the program captures its details and generates a corresponding hash. The file's path and its hash value are then added to a comprehensive list of monitored files stored in the dictionary. This enables the program to maintain an up-to-date record of all files and ensures that new additions are included in the monitoring process.
<br />
<br />
<br />
<br />
An new file "d-copy.txt" is created.
<br />
<br />
<br />
<br />
<img src="https://github.com/sdkallullathil/Powershell_project/blob/a3f89e9d508d61aca4369c5a27062c95eadd2bc4/create1.png" height="90%" width="90%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
<br />
The output of the monitor.
<br />
<br />
<br />
<br />
<img src="https://github.com/sdkallullathil/Powershell_project/blob/c4fd8d84b5df3d57a445b959034d45e38b452bfb/newcreated.png" height="90%" width="90%" alt="Disk Sanitization Steps"/>
<br />
<br />
<b>File Deletion Tracking</b>
<br />
The program continuously tracks the presence of files within the designated folder. If a file is deleted, the File Integrity Monitor promptly identifies the absence by detecting the missing file path in the folder. The program then raises a notification to alert the user about the deleted file. This feature helps users stay informed about any unexpected deletions and aids in identifying potential security issues or unintentional data loss.
<br />
<br />
<br />
The file "d.txt" is deleted.
<br />
<br />
<br />
<br />
<img src="https://github.com/sdkallullathil/Powershell_project/blob/070b4a5b28b117712d4d1f45895ca295c18483a6/delete1.png" height="90%" width="90%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
<br />
The output of the monitor.
<br />
<br />
<br />
<br />
<img src="https://github.com/sdkallullathil/Powershell_project/blob/c823beecaad8b5ba6ff85db4c5147d4c414acec2/delete.png" height="90%" width="90%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
<br />

<h3>Conclusion</h3>

By developing this File Integrity Monitor using PowerShell, I aimed to provide a reliable and straightforward solution for maintaining data integrity in a specific folder. It offers comprehensive monitoring capabilities, ensuring the integrity and security of the files within the designated folder. It provides real-time alerts and tracking for changes, additions, and deletions, enabling users to take immediate action when necessary.Users can rest assured that any changes to files within the monitored folder will be promptly detected and reported, helping them respond quickly to potential security threats or unintended modifications. 

