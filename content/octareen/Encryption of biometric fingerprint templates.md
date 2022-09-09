
![[Pasted image 20220518180715.png]]


![[Pasted image 20220518180831.png]]


# Introduction
- Definition of biometric system

## traditional biometric system blocks
According toMenariya and Ojha (2012)
- Sensor
- Feature extractor
- Templates database server
- Matcher
- Decision

The three major functions of biometrics are Enrollment, Archiving and Biometric Template Matching(Malhotra & Kant, 2013)


# Authentication
## Identification
A biometric systemhas identificationcapabilities if it is able to uniquely retrieve and match an individual’s biometric features from a database of other individuals e.g. match fingerprint patterns of a user from several other fingerprints in a database. Identification is a 1: nsearch where nis all individuals in a biometric database(Venkatesh, Balaji, & Chakravarthy, 2012).ii)

## Verification In
verificationa known distinctive attribute about a user is used to retrieve biometric features of an individual then perform a match comparison against it from biometric feature sets presented at a biometric sensor e.g. using ID NO, VAT NO, NSSF NO, NHIF NO or Employee NO to retrieve biometric fingerprint features saved with the distinguishingattribute against the fingerprint features presented at a biometric sensor


## What we want
![[Pasted image 20220518183220.png]]

## Uni vs multimodal
- https://ieeexplore.ieee.org/document/4579977 multimodal 
- multimodal biometric systemswhich unlike unimodal biometric systemsarevery complex, expensive and only affordable to large corporations and are apreserve for rich governments(Das, 2012)
- UNIMODAL AUTH needs better security
This however has not been the case as biometric templates have been fraudulently accessed to gain unauthorized access to information systems.
- The advent of increased security threats in information systems and need to guarantee unbeatable systems security enticed system designersand developersto incorporate use of passwords, PINs and access codes for system users’ authorization.
- **Tan (2013)**considered use of biometric authentication schemes to bemore efficient over traditional password based access control methods.
- Statistics however show that biometric systems have not been known to be impervious to hacks and that there are several known possible attacks on biometric systems which have rendered use of biometricsinsufficient in providing water tight security as is evidenced by Rathgeb and Busch (2012)



## System specifics
- A biometric system can be categorized aseither a verification or identification system. El-Sisi(2011)defineda verification system as one which conducts one to one comparisonof biometric templatesto confirm if identity claimed by an individual is true and defined an identification system as one that searches an entire database for a biometric template match. In the process of verification or identification, a user’s fingerprints areextracted for purpose of matching them with previously captured biometric fingerprint templates.

## Problems
- Biometric templates stored in a database in their raw format can be illegally retrieved and replayed to the biometric system’s matcher by system hackers to grant unauthorized access to a biometric systemespecially for instanceswhere adversariesdisguise themselvesas the genuine bearersof the presented biometric traits.
- In order to realize optimal and secure use of biometrics as access control features, there is need to guarantee safety of biometric templates stored in authenticationsystems.
- Passwords, PINS and access codes can be replaced with new ones if they get compromised unlike the case of biometric fingerprint templates which havepermanent physical features - PERMANENCE

## Solutions
Ahmadet al.,(2012)particularizedthat ‘security of biometric data in a biometric system’ as one of the key technical issues and challenges regarding use of biometric systems. Schemes used to protect biometric feature sets and biometric templates in biometric systems were reviewed then an encryption techniquefor encrypting biometric fingerprint templates with encryption keys derived from other fingerprint templatesin a unimodal biometric fingerprint systemwas designed and developed.

Although various biometric templateprotection schemes and approaches existincluding encryption of templates with information prevalentto an individual e.g. year of birth, ID number or security codesas seen in(Kauret al, 2010)which can be easily guessed and estimated by attackers, there is need for a biometric fingerprint template protection approach that providessecurity of archived biometric templates in unimodal biometric fingerprint systems

The existing template protection schemes are not fool proof and do not guaranteewater tightsecurityas is evidenced by Jadhav (2014).

In a recent research study,researchers pressedthat cryptographic template protection renders more secure image protection (Maniroja & Sawarkar, 2013). Thisstudy culminatedto a more effective technique for securing biometric fingerprint templates that guaranteedsafety ofnot only biometric fingerprint templates in unimodal biometric fingerprint systems but also provideda replicable approach forsecuringbiometric templates in a non-retrievable manner to hackers in other biometric syste

## Prev methods
pg 37/163
Existing literature identify bio-hashing and cancellable biometrics as invertible and non-invertible transformation respectively(Gaddam & Lal, 2011).

Cancellable biometrics


# Attacks
![[Pasted image 20220518181448.png]]

We are trying to prevent attack 6
![[Pasted image 20220518181546.png]]


- Brindha 2012
- She further cautioned against biometric templates being stored in plaintext form and insisted that fool-proof methodologies are essential in securing storage ofbiometric templates to safeguard both safety of the biometric system and that of the users.


# How are we getting the key
## Then algorithms 
- AES
- RSA
- ECC

## If AES
which mode and why?
pg 57/163

ANSIandISOstandard formats.How fingerprints are saved in a biometric system determines how secure a biometric system is at averting adversarial attacks(Arjunwadkar et al., 2012). This research chose to use ISO 19794-2 format forbiometric fingerprint templates which is anISO standard format accepted widely in the spheres of biometric fingerprints(Alexandruet al. 2012


### Method specifics
pg 57,58
![[Pasted image 20220518183805.png]]

![[Pasted image 20220518183957.png]]



### Survey results from Mwema paper are important

- 99/163 - attack type summary



## Flow chart-
pg 115/168 VERY IMPORTANT
pg 119/168 UML

