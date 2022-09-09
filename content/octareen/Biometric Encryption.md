## Other links 
- https://link.springer.com/chapter/10.1007/978-981-16-7618-5_46
- Matching templates after extracting them: 
	- https://github.com/adafruit/Adafruit-Fingerprint-Sensor-Library/issues/9
		- check show_fingerprint_template
- N.K.Ratha,J. H.ConnellandR.M.Bolle,“Abiometrics-basedsecureauthenticationSystem”,Proc.oftheAutoID99,Oct.1999,pp.70–73
- https://link.springer.com/chapter/10.1007/978-1-84882-254-2_4
- https://ieeexplore.ieee.org/abstract/document/4534494 - fingerrpint matching
# Implementation
https://forum.arduino.cc/t/fingerprint-sensor-with-esp32-not-working-solved/555737/8

# Pre-req

## Fingerprint
### Basics
- ridge in a fingerprint is defined as a single curve segment and a valley is the region between two adjacent ridges
- The collective set of ridge endings and bifurcations form the minutiae. 
- The minutiae can be of different types including dots ,islands, ponds or lake, spurs, bridges and crossovers

## Processing
1. [[Histogram Equilization]] 
	1. [[Generation of biometric key for use in DES]]
2. Helper data


## Look up
### Imp
- How attendance systems work
- how to encrypt fuzzy data like biometrics
- Fuzzy extractors
- Learn how facial unlock works when its almost always near match
- encrypt using python or esp32?
- **There is a difference between fingerprint encryption and fingerprint authentication**

1. [[Cancellable Biometrics]]
2. Symmetric vs public keys
3. self exclusion in facial recognition

## Research
### Papers
1. [[Generation of biometric key for use in DES]] by Rupam Kumar Sharma 
	1. (not that useful)
2. [[Biometric Encryption Tutorial]] 
	1. general stuff
	2. applications
	3. cancellable biometrics
3. [[MyTec's Biometric Encryption]]
	1. History
	2. Methods
	3. Biometric encyption, key generation
4. [[Biometric Encryption system for the self exclusion scenario in face recognition]]
	1. What is BE
5. [[A Novel Fuzzy Encryption Technique Based on Multiple Right Translated AES Gray S-Boxes and Phase Embedding]]
6. [[A Survey on Fingerprint Authentication Using Various Cryptographic Techniques]]
7. [[Touchless BUA]]
	1. Using LSTMs
8. [[Fingerprint Authentication for Banking]]
9. [[TRNG and fingerprint authentication]]
10. [[Encryption of biometric fingerprint templates]]
11. [[Arduino based biometric authentication]]
12. [[Biometric key generation using Deep Learning]]
13. [[Security performance evaluation of biometric encrytion]]
14. [[An Analysis of Minutiae Matching Strength IBM]] - attack points
15. [[Biohashing two factor authentication featuring fingerprint data and tokenised random number]]
16. [[Cancelable Biometrics Review]]: conclusion is imp for our conslusion

17. [[Fingerprint recognition techniques]] 
18. [[Review of fingerprint recognition algorithms]] - super short and useful for matching algorithm selection
19. 

# Paper outline
- [x] 1. Abstract
- [x] 2. Introduction
	- [x] Definitions and terms
	- [x] Attacks
- [x] 3. Lit survey
	- [x] Classification of solutions
	- [x] One line on each paper referenced - make list of lit review papers
- [x] 4. Objective - crisp def + mwema objectives
- [ ] 5. Proposed methodology
	- [ ] Block diagram
	- [ ] Explain each part of block diagram
	- [ ] Code snippet
- [ ] 6. Results
- [ ] 



----------------------

## Abstract
- Need for - authentiction is ubiqutous
- Recent advances in biometrics
- In this paper

> Biometric authentication developed as an answer to the growing need 


 The need for fool proof authentication procedures away from traditional authentication mechanisms like passwords, security PINS has led to the advent of biometric authentication in information systems. Fingerprints are unique and extremely difficult to forge. However, because, more often than not, they are stored as plaintext strings in a device, they are vulnerable to attacks. This is why biometric authentication is used most prominently in smartphones, never in client server applications. This projects attempts to implement a fool proof authentication system that encrypts fingerprint templates in order to prevent adversaries from gaining unauthorised access to confidential data. 

## Introduction
- What is biometric 
- Applications - short case study in banking sector
- The current state of authentication systems (in brief)

Biometrics is simply the automatic identification of a person’s physiological or 
behavioral patterns or traits. Biometric patterns captured from a person are saved as 
biometric templates. Biometric fingerprint templates are physiological patterns 
extracted by a feature extractor in a biometric fingerprint sensor and saved in a 
biometric system’s database, smartcard or archived in a system folder for purpose of 
future use in verification or identification of a person. A biometric system can be 
categorized as either a verification or identification system. El-Sisi (2011) defined a 
verification system as one which conducts one to one comparison of biometric 
templates to confirm if identity claimed by an individual is true and defined an 
identification system as one that searches an entire database for a biometric template 
match. In the process of verification or identification, a user’s fingerprints are extracted 
for purpose of matching them with previously captured biometric fingerprint 
templates

- **Verification system**
- **Identification system**

# Lit review papers and summary
| Paper   | Summary                                                 | Remarks            |
| ------- | ------------------------------------------------------- | ------------------ |
| Jayapal | pg 17, cancellable biometrics                           | Find better source |
| Jayapal | pg 20 , multimodal biometric                            | find better source |
| Jayapal | pg 25, fingerprint based identification - preprocessing |                    |
|         |                                                         |                    |
