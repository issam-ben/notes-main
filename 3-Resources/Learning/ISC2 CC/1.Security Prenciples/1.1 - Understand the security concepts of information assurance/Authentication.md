Authentication is the process of verifying who someone is.

## Access Control
- Identification: is the process where an Individual makes a claim to be someone ex:user without any proof at the moment.
- Authentication: is the step when the user provides proof of their identity. 
- Authorization: is the process of giving the authenticated user the resources he/she has access to.
- Accounting: is the process of tracking user activities, like who logged in, modified files,...etc
### Password Policies
Are set of rules that put requirements on users regarding their passwords, it aims to enhance the security of systems, some of these rules are:
- Password length: it sets the minimum number of characters in a password, like 8 characters min, the more longer the password the more harder to be guessed or brute forced.
- Password Complexity: it sets the types of characters that must be used in a password, like enforcing lower and upper cases, and other characters like */#%$*.
- Password Expiration: it sets the lifetime of a password, like having the requirement to renew passwords every 3 months. 
- Password History: it sets the rule that and old password can't be reused.
- Password Resets: it sets the ability for users to reset and change their passwords, the organization should make it easy for them to do so.
- Password Reuse: it sets the requirement from users to not use the same password across multiple websites and services.
- Password Managers: it sets the requirement of an organization to its users to use Password managers (such: Lastpass, Bitwarden, Proton, ...etc), to make it easy for them to have different passwords for each website and service they use.
### Authentication Factors
Computer systems have many ways (Techniques) of authentication that allow users to authenticate and protect their resources, these factors are:
- Something you know: the most common authentication factor, like passwords, PINs, Security codes...etc.
- Something you Are: Like Biometric authentication, that measures one of your physical characteristics such as 
	- fingerprint, 
	- eye pattern, 
	- face,
	- voice.
- Something you have: it is the physical possessing of a device that authenticates you such as:
	- Smartphone, 
	- Software token applications,
	- Hardware token key fob,
	- Smart Cards.

### Multi-Factor Authentication
All the factors mentioned can provide some level of security, but can be a risk if used alone, like password, if an attacker get holds of it, it will be a breach, other factors are not perfect neither, but if combined it can make the job of the attacker much more harder, like combining something you know (Password) with something you have (Smartphone). it is recommended to use two or more different types of factors, because combining a password with a PIN is same type, hence it's not Multi-Factor Authentication MFA.