As of version [[1.2.0]], Mumble supports strong encryption and authentication based on certificates instead of passwords.

## Certificates 

A certificate is essentially a digital signature which is used by Mumble to identify and authenticate users, and can be used either alongside or instead of passwords to register user accounts.

For more information about certificates, see the Wikipedia entries on  [Certificates](http://en.wikipedia.org/wiki/Public_key_certificate Public key).

## Authentication Methods 
There are three scenarios to authentication of a registered user in Mumble now:

### No Password Set, Certificate in Client  

If a client is registered to a user name by another user (or themselves, if privileges allow) from inside the Mumble client (by right clicking on the user, or themselves, and clicking "Register"), the account is created with no password but the certificate is connected to that account and only a user with that certificate will be able to connect as that user.  '''This is probably the most common case''', especially if no [external user management](3rd Party Applications .md) is being used.

If no password is set, and the user connects from a Mumble installation that does not have their matching certificate, they will not be able to use that account. See [below](#Replacing Lost or Expired Certificates.md).

### Password Set, Certificate in Client 

If your client has a certificate in it, and you log into an account that has a password on it for the first time, then you will be prompted for a password. Once the correct password is entered, the certificate is attached to that account on the server - any user connecting from that same client certificate will not need a password from that point on.

### Password Set, No Certificate in Client 

If a user's account is created using an external administration program, a password set, and they have not created a certificate in their client, then Mumble will pretty much just authenticate as with 1.1.x and earlier. The password is not saved, and must be entered every time you connect.

As of 1.2.1, Mumble will always automatically generate a certificate, even if you terminate the certificate wizard - so this scenario is increasingly unlikely.

There's still no way to set a password for an account other than SuperUser from Mumble or Murmur itself - you'll need an [administration package](3rd Party Applications .md) to do that. If you don't have one, the next scenario is much more likely.

## Replacing Lost or Expired Certificates 

As stated in the last scenario, if you replace your certificate for some reason then the certificates will not match. If you have a strong certificate (signed by a trusted certificate provider, such as StartSSL) and the email address matches the old one, then the certificate will be updated without a password being required.

If you have another certificate generated by Mumble, then you'll need the password to the account to update your certificate on the server. For this reason, if you're not using account passwords (say, you have no [administration package](3rd Party Applications .md) installed), you'll want to make sure you backup your certificate and key and keep them in a safe place.

## Getting a Strong Certificate 

You can use a strong certificate with Mumble if you have one; you can use commercial certificates as long as they are usable as both client and server certificate. See our article on [[obtaining a Comodo Certificate]] for an example of a certification authority offering free certificates.


