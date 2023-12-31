<h1>OpenSSL Certificate Management Lab</h1>

<h2>Lab Description:</h2>
<p>Welcome to my OpenSSL certificate management lab on Kali Linux. In this lab experience, you'll dive into OpenSSL, a versatile tool for securing data. You'll learn how to create certificates, generate certificate signing requests, and convert certificate formats. OpenSSL is a vital resource for protecting digial confidentiality.</p>

<h2>About OpenSSL:</h2>
<p>OpenSSL is an open-source cryptographic library that plays a crucial role in securing data, encrypting communication, and managing certificates.</p>

<h2>What's Inside:</h2>
<p>Inside this repository, you'll find a comprehensive guide with step-by-step instructions to generate asymmetric key pairs, generate a Certifacte signing request, and convert the certifcate format. We'll use Kali Linux as our virtual environment, incorporating languages like Bash, OpenSSL commands, and relevant libraries. </p>


<h2>Section 1: Generating Public and Private Keys</h2>

In this section, we will generate an asymmetric RSA key pair using OpenSSL.

1. First, navigate to your Documents directory and create a new directory named "keys". This is where we will store our keys.    
   - cd Documents     
   - mkdir keys     
   - cd keys 

2. Now, let's generate an Asymmetric RSA key pair. The following command will create a private key named "threathunter.key" with a key length of 2048 bits.    
   - openssl genrsa -out threathunter.key 2048

3. To view the content of the private key you just generated, you can use the "cat" command:    
   - cat threathunter.key
  
     
![Alt Text](images/1.png)

4. Next, we'll extract the corresponding public key from the private key. This public key will be used when generating a Certificate Signing Request (CSR) in a later section.    
   - openssl rsa -in threathunter.key -pubout -out threathunter_public.key

5. To verify that both the private and public keys have been generated and saved successfully, you can list the files in the current directory:    
   - ls

6. Finally, you can view the content of the public key using the "cat" command:    
   - cat threathunter_public.key  


![Alt Text](images/1.5.png)

You've now successfully generated an RSA key pair, obtained the private key, and extracted the public key. These keys are fundamental to secure communication and certificate management in OpenSSL.




<h2>Section 2: Generating a Certificate Signing Request (CSR)</h2>
In this section, we will create a Certificate Signing Request (CSR) using OpenSSL. A CSR is a request for a digital certificate that includes your public key and essential information about your organization.

1. To generate the CSR, use the following command:
   
   - openssl req -new -key threathunter.key -out threathunter.csr

![Alt Text](images/2.png)


2. You can verify the certificate request with this command:
   - openssl req -text -in threathunter.csr -noout -verify

3. To view the CSR that would be sent to the certificate authority, use the following command:
   
   - cat threathunter.csr  


![Alt Text](images/3.png)


Now you have successfully generated a Certificate Signing Request (CSR) and can review its content. The CSR is a crucial step in obtaining a digital certificate for your server or application.



<h2>Section 3: Converting Certificate Formats</h2>
In this section, we will explore how to convert certificate formats using OpenSSL. Converting between formats is often necessary for compatibility with different systems or applications.

1. To generate a self-signed certificate, run the following command:
   
   - openssl req -newkey rsa:2048 -nodes -keyout threathunter.key -x509 -days 100 -out threathunter.crt

2. To merge the ".key" and ".crt" files into a ".pfx" (PKCS #12) file, use this command:
   
   - openssl pkcs12 -export -name "threathunter.com" -out threathunter.pfx -inkey threathunter.key -in threathunter.crt  


![Alt Text](images/5.png)


You've now learned how to generate a self-signed certificate and convert it into a different format (".pfx"). This flexibility in format conversion is valuable for various deployment scenarios and system compatibility.



