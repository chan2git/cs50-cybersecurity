# Lecture 0: Securing Accounts


### Authentication
Authentication is the process of proving who you are.

### Authorization

Authorization dictates whether or not you should have access to a resource after you have authenticated yourself.

### Password

Passwords are intended to be known only by the authenticated user, so they can be a method of authentication.

### Dictionary Attack

An attack where a threat actor utilizes a wordlist file based on a theme, leaked passwords, most commonly used passwords, or curated strings to try and compromise your credentials.

### Brute Force Attack

An attack where a threat actor utilizes a software/script/tool (or manually) attempts to try all possible string combination as a password to eventually compromise your credentials.


### Password Complexity and Requirements

The shorter the password length, the lower amount of possible password permutations. For example, a 4 digit password comrposied of numbers from 0-9 (0000 - 9999) allows for up to 10,000 different combinations (10^4). A Python script can be written to methodically generate and print all the 10,000 different combinations within mere milliseconds.

```
from string import digits

for i in digits:
    for j in digits:
        for k in digits:
            for l in digits:
                print(i, j, k l)

```

If we use 4 letters (upper and lower, so 52 possible characters per string place), this increases the possible password combinations to 7,311,614 (54^4). Updating our Python script with these parameters now finishes the computation in only a few seconds.


```
from string import ascii_letters

for i in ascii_letters:
    for j in ascii_letters:
        for k in ascii_letters:
            for l in ascii_letters:
                print(i, j, k l)
```

If we use all 94 possible characters per string place, this increases the possible password combination to 78,074,896 (96^4). This would now finish outputting in perhaps right under a minute.

```
from string import ascii_letters, digits, punctuation

for i in ascii_letters + digits + punctuation:
    for j ascii_letters + digits + punctuation:
        for k in ascii_letters + digits + punctuation:
            for l in ascii_letters + digits + punctuation:
                print(i, j, k l)

```

The longer the password string, the more resource it'll take to brute-force. For example, simply requiring a password string to be at least 8 characters long could generate a possible 6 quadtrillion combinations (96^8). One thing to keep in mind is usability vs security. If the password is too long and complex, it may discoruage users from wanting to use the system or cause users to forget the passwords.

NIST provides the following recommendations for password best practices:
- Memorized secrets shall be at least 8 characters in length
- Verifiers should permit subscriber-chosen memorized secrets of at least 64 characters in length. All printing ASCII characters as well as the space character should be accepted in addition to Unicode characters.
- Verifiers shall comparea the propsective secrets against a list of values that are commonly-used, expected, or compromised (previously breached corpuses, dictionary words, repetiitive/sequential characters, context-specific words such as name of the service, username, etc)
- Memorized secret verifiers shall not permit the subscriber to store a hint that is accessible to an unauthenticated claimant. Verifiers shall not prompt subscribers to use a specific type of information when choosing memorized secrets ("What was the name of your first pet?")
- Verifiers should not require memorized secrets to be changed arbitrarily (e.g. periodically)
    - Forcing users to change passwords too frequently may incentivize them to exert less effort to meet requirements but make it easier to remember (e.g apple123 becomes apple456)
    - Users may forget their passwords and have a hard time tracking it


### Password Lockout

Multiple failed attempts may cause a lockout policy/procedure to activate which can make threat actors to wait. This increases the amount of effort it takes to gain access. After x amount of failed attempts, the device (e.g. a phone) could wipe itself clean. This makes the threat actor's attempt more risky and may make them move on to easier targets.

### Two-Factor Authentication / Multi-Factor Authentication

An authentication method that requires multiple types of authentication factors to login.
- Knowledge factor is a factor that may be information only you should know (e.g. a password string)
- Possession factor is a factor that is associated with something that only you should possess (e.g. an temporary authentication token generated on your personal device, One-Time Password, etc.)
- Inherence factor is a factor is related to an inherent trait that is unique to you (e.g. fingerprint). Often associated with biometrics.



### SIM-swapping
An attack where a threat actor convinces the victim's mobile carrier to swap SIM information. When information (e.g. one-time passcode to text) is sent to the victim, it ends up going to the threat actor

### Keylogging
Software or malware that is recording keystrokes where the record will be sent back to the threat actor, which likely contains sensitive information such as credentials.


### Credential Stuffing

The process where a threat actor identifies a list of credentials belonging to users for a particular application, and uses this information to 'stuff' the credentials into a different application.