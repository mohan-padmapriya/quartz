# Abstract
Owing to the various advantages offered by biometric authentication systems over knowledge and possession based systems like passwords and pins, the use of the former has increased exponentially in popularity. Fingerprints are unique and tough to forge. However, more often than not, they are stored as plaintext strings in a device, and are hence vulnerable. This is why biometric authentication is used most prominently in smartphones, and rarely in client server applications. This project attempts to implement an authentication system that encrypts fingerprint templates before storing them, in order to prevent adversarial attacks. AES in CBC mode is employed in order to secure the fingerprint templates in the database.


## Introduction
A \textbf{biometric} is a measurement of an individual's unique physical or behavioural characteristics. Facial recognition, retinal scans, and fingerprint mapping are popular examples of biometric security systems.

The system is capable of verification if it is able to perform a comparison between an archived biometric template and a biometric presented at the sensor. 
*a verification system authenticates a person’s identity by comparing the captured fingerprints with her own biometric template(s) pre-stored in the system. It conducts one-to-one comparison to determine whether the identity claimed by the individual is true;*

The identification mode is defined by successful retrival of an individual's biometric features from a database of several biometric templates. 
*an identification system recognizes an individual by searching the entire template database for a match. It conducts one-to-many comparisons to establish the identity of the individual.*

Biometric authentication schemes are more efficient over traditional password or pin based authentication systems (Tan 2013). Recent developments in sensing and computing technologies have made biometric systems more affordable and as a result they are easily embedded in a variety of smart consumer devices such as mobile phones and tablets. 
However, they are not immune to adversarial attacks (Rathgeb and Busch 2012). It is quite easy for biometric templates stored as plaintext to be accessed illegally, and even tampered with and replayed to the authentication system, thereby risking the loss and forgery of confidential data by a malicious adversary. 

Another insurmountable weakness of such a system is the permanence associated with a biometric signature. While passwords and pins can be replaced upon necessity, the same cannot be done to fingerprints or iris scans. 

### Types of attacks

There are several abuses of biometrics and attacks on biometric template databases. The sources of these attacks are varied, as demonstrated in the figure below. 
![[Pasted image 20220520142428.png]]

- Point 1: Spoofing: Fake biometric at the sensor
- Point 2: Replay attack: resubmission of a digitally stored old fingerprint
- Point 3: Trojan horse at the feature extractor 
- Point 4: Tampering with the feature representation
- Point 5: Masquerading: Override matcher
- Point 6: Substitution: Tampering with stored templates
- Point 7: Channel attack between template and matcher
- Point 8: Decision (yes/no) override

In this paper, we focus on developing a system that counters the attacks at points 5, 6, and 7.


## Literature Survey
Through the years, there have been several proposals for authentication schemes that keep biometrics secure. 

## A review of existing methods
![[Pasted image 20220520162354.png]]
## Feature Transformation
## Biohashing

BioHashing is an invertible method which is based on transforming the biometric template using pseudo-random projections that are generated using a user-specified key or token. However, as concluded by Kong et al, biohashing techniques operate under the assumption that the TRN would never be lost, stolen, shared or duplicated, which is not generally the case. If it was possible to guarentee a secure TRN, there would be little use to combine biometrics as it would serve as a perfectly secure password by itself. 

> https://citeseerx.ist.psu.edu/viewdoc/download?doi=10.1.1.106.138&rep=rep1&type=pdf

Another popular idea in feature transformation, which is non-invertible are Cancellable Biometrics, proposed and outlined in Davida et al, Ratha et al, and otehrs. In this method, instead of storing the original biometric, it is transformed using a one way function. The transformation can be applied either in the original domain or in the feature domain. It provides privacy since it is computationally difficult to recover the original biometric from a transformed one. 
The vulnerability of cancellable systems using compressive sampling is not known yet, against blind deconvolution systems is not known yet.
In order for the transform to be repeatable, the biometric signal must be positioned in the same coordinate system each time. This requires that an absolute registration be done for each biometric signal acquired prior to the transformation.

https://engineering.jhu.edu/vpatel36/wp-content/uploads/2018/08/SPM_CB_v6.pdf

## Biometric encryption
Generation of a secure key from a biometric template uses the concepts of fuzzy extractors and secure sketches. how to derive a consistent cryptographic key from noisy data such as biometric templates, with the help of some extra information called a sketch. These ideas are further outlined by Dodis et al and nasir et al. 

Sahai and Waters propose a unique fuzzy identity based encryption scheme we view an identity as set of descriptive attributes. A Fuzzy IBE scheme allows for a private key for an identity, ω, to decrypt a ciphertext encrypted with an identity, ω 0 , if and only if the identities ω and ω 0 are close to each other as measured by the “set overlap” distance metric.


There are also methods that encrypt the fingerprint template. Mwema uses a fingerprint template to generate a key, and then uses that key to encrypt another fingerprint template. 
(**More on mwema**)
and others

In this paper, we attempt to use a similar approach to encrypting the fingerprint template. 

## Objective
![[Pasted image 20220518183220.png]]

- Confidentiality and integrity
**

The objective of this project is to develop a fingerprint authentication system that is -

1.  Confidentiality: Even if an adversary is able to access a template, she must not be able to decrypt it.
    
2.  Integrity: The adversary should not be able to manipulate a fingerprint template in any way.
    
3.  Revocability: It must be possible to identify and revoke a compromised template, and reissue a new one that is representative of the user’s true fingerprint.
    
4.  Unforgeability: The system must ensure ciphertexts cannot be existentially forged using fingerprint spoofs. 
    

Efficiency: The encryption scheme must not bear significantly on the speed of the matching algorithm.**

**READ MWEMA AGAIN**

# Proposed methodology
### Block diagram of system
A fingerprint sensor is used to enrol fingerprints and consequently perform user verification. 


### Circuit diagram
![[ESP32 FINGERPRINT.jpg]]


### System flow design

- Enrolment and encryption
- Decryption and maatching

A conventional fingerprint authentication system has 3 main components - sensing, feature extraction, and matching. Our proposed system has the extra steps of encryption and decryption.


## Extraction of fingerprint on to template
### 1. Sensing
The sensing element is the most important part of the fingerprint module. In general, sensors can be divided into three categories - optical sensors, solid state sensors, and ultrasound sensors. 

![[opticalSensor.png]]

There are several parameters that characterise digital raw fingerprint images, such as[^1] : 
- Resolution
- Area
- Number of pixels
- Depth
- Geometric accuracy
- Image quality

It is essential to ensure the image is satisfactory in all these areas.

The fingerprint module used in this implementation is a live-scan, optical fingerprint sensor with TTL UART interface. It is a 500 dpi sensor with Fake rate (FAR): <0.001%  Refusal rate (FRR): <1.0%[^2]



## 2. Feature Extraction
### Fingerprint terminology
**Ridges and valleys:** 
- Ridges are the dark lines while valleys are the light ones. They may run parallel to each other, bifurcate, or terminate. 
- Ridgelines give rise to **singular regions** like **loops, deltas, and whorls**.
- **Core**: Also known as the registration point, it is situated at the centre of the north most loop singularity. It is not always straightforward to locate it due to the variability of fingerprints. 
- While ridges, valleys, cores, and singularities are analysed as global markers, locally, we analyse **minutiae** which refer  to various ways that the ridges bifurcate or terminate. 

### Feature extraction steps
![[featEx.png]]

## Pre and post processing - (jayapal)
To ensure a greater sucess rate, noise caused by cuts, scars, dryness, and wetness needs to removed, and ridges must simultaneously be enhanced. 

### Preprocessing
- Image enhancement
	- histogram equalization
	- Image filtering
		- Low pass filters for Smoothing, Blurring
		- High pass filters for edge detection and sharpening
	- Noise removal 
- Image binarization/segmentation

### Minutiae extraction
- Ridge thinning and minutiae detection can be done using
	- Minutiae extraction technique
	- Pattern matching or ridge based technique.
	- Correlation method

### Postprocessing
- False minutiae removal


## Encryption scheme
### Why AES-128
- justification

### AES-CBC general description
![[Pasted image 20220522192026.png]]

### AES as used here


## Database management

## Matching algorithm
In order to perform verification or identification, an algorithm that compares the similarity between two fingerprint templates is required. Fingerprint matching algorithms may either return a binary decision (yes or no), or might output a degree of similarity between 0 and 1. 

The process of matching is made difficult by certain factors, like a high degree of displacement or rotation that causes the fingerprint area fingerprint area to fall outside the sensor’s “field of view,” different pressure and skin condition, non-linear distortion, noise from the fingerprint sensor, and errors made during the feature extraction.

There's a selection of fingerprint matching algorithms used, the most popular of which are correlation based, or minutia based. Given the superior performance of minutia based matching, as concluded in the review by ___ we implement it.

### Desc of minutia based
![[minuExa.png]]








# Implementation
- Pictures
- Code




## Results
- More secure, 
- Best 

## Further work/scope
- better matching algorithm
- hardware limitations

----------------------------------


# References
## Biohashing
- B. Topcu, H. Erdogan, C. Karabat and B. Yanikoglu, "Biohashing with fingerprint spectral minutiae," 2013 International Conference of the BIOSIG Special Interest Group (BIOSIG), 2013, pp. 1-12.
- https://citeseerx.ist.psu.edu/viewdoc/download?doi=10.1.1.106.138&rep=rep1&type=pdf

## Cancellable biometrics
V. M. Patel, N. K. Ratha and R. Chellappa, "Cancelable Biometrics: A review," in IEEE Signal Processing Magazine, vol. 32, no. 5, pp. 54-65, Sept. 2015, doi: 10.1109/MSP.2015.2434151.
- G. I. Davida, Y. Frankel, and B. J. Matt, “On enabling secure applications through off-line biometric identification,” IEEE Symposium on Security and Privacy, pp. 148–157, May 1998. [3] N. K. Ratha, J. H. Connel, and R. Bolle, “Enhancing security and privacy in biometrics-based authentication systems,” IBM Systems Journal, vol. 40, no. 3, pp. 614–634, 2001. [4] N. Ratha, S. Chikkerur, J. Connell, and R. Bolle, “Generating cancelable fingerprint templates,” IEEE Transactions on Pattern Analysis and Machine Intelligence, vol. 29, no. 4, pp. 561 –572, April 2007.
## Fuzzy extractors and secure sketches
Dodis, Yevgeniy & Reyzin, Leonid & Smith, Adam. (2004). Fuzzy Extractors: How to Generate Strong Keys from Biometrics and Other Noisy Data. Computing Research Repository - CORR. 38. 523-540. 10.1137/060651380. 

Li, Qiming & Sutcu, Yagiz & Memon, Nasir. (2006). Secure Sketch for Biometric Templates. Adv. Cryptology Asiacrypt. 4284. 99-113. 10.1007/11935230_7. 

LI, N., Guo, F., Mu, Y., Susilo, W. & Nepal, S. (2017). Fuzzy Extractors for Biometric Identification. 37th IEEE Internaitonal Conference on Distributed Computing Systems (ICDCS 2017) (pp. 667-677). United States: IEEE.

Uludag, U., Pankanti, S., Jain, A.K. (2005). Fuzzy Vault for Fingerprints. In: Kanade, T., Jain, A., Ratha, N.K. (eds) Audio- and Video-Based Biometric Person Authentication. AVBPA 2005. Lecture Notes in Computer Science, vol 3546. Springer, Berlin, Heidelberg. https://doi.org/10.1007/11527923_32

A. A. Al-Saggaf, "A Post-Quantum Fuzzy Commitment Scheme for Biometric Template Protection: An Experimental Study," in IEEE Access, vol. 9, pp. 110952-110961, 2021, doi: 10.1109/ACCESS.2021.3100981.

Brent Waters, Sahai
Jayapal
Mwema
