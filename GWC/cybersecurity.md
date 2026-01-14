# Cybersecurity

<aside>
📝

Intro to Cybersecurity

> In what ways is cybersecurity a social justice issue?
> 
- Project 1
    - representation and individuals that are in leadership/part of the cybersecurity field are inequal
    - data breach: incidents where information is taken, unconsented
    - [have i been pwned](https://haveibeenpwned.com/): check if your email has been part of a data breach
    - why python is used in cybersec: easy learning & implementation, and also open source
    
    > CIA Triad (principles to guide data protections
    > 
    > - C: Confidentiality: only authorized users have access to data
    > - I: Integrity: ensures data can be trusted, and hasn’t been tampered with
    > - A: Availability: networks, system,s and applications are up and running to authorized users whenever they want to use them.
- Project 2
    - data breach: when one of CIA triad gets endangered.
    - causes of data breaches:
        - vulnerability: technical, social, physical
    - NIST framework and cybersec careers
        1. identify - pen testers
        2. protect - cryptographer
        3. detect - cyber forensics
        4. respond - cybersec engineers
        5. recover
    - Lockheed Martin’s Cyber Breach Chain
        - 
</aside>

<aside>
📝

Intro to Cryptography

- Project 1 (Hello Caesar’s Cipher)
    - cryptography: science of secret messages
    - encryption: to make it unreadable
        - decryption: reverse of encryption
    - cipher: set of rules to convert normal text → ciphertext
    - key: locks message so only certain people can read it
    
    - cryptopgrapher: works to develop more secure systems
    - cryptanalyst: works to crack or break systems
    - ciphers: shifting by a set number (the key)
    
    ```python
    # for loops for strings:
    name = "Jana"
    for character in name:
    	print(character)
    	
    # will output:
    # J
    # A
    # N
    # A
    
    # find method (indexOf() for java):
    greeting = "hello"
    print(greeting.find("o")
    ```
    
- Project 2 (Cipher Usability)
    
    > Components of Usability
    > 
    > - Learnability
    > - Efficiency
    > - Memorability
    > - Error Tolerance
    > - Satisfaction
    - you only need to declare a variable as global inside a function if you modify it
- Project 3 (Cracking Caesar’s Cipher)
    - decrypting cipher vs. cracking a cipher:
        - someone attempting to decode a secret message
    - string formatting
    
    ```python
    print("the %s ate the %s that ate the %s." % ("cat", "dog", "rat))
    ```
    
    - measuring security of a cipher:
        1. key length
            - convert key # to binary, call it n-bit key
            - higher n = more complex/secure
        2. algorithm complexity
        3. methods used to crack cipher
</aside>