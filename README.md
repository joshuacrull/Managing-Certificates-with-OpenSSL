<h2>OpenSSL Certificate Management Lab</h2>
<ul>
    <li><b>Begin by navigating to your "Documents" directory and creating a new directory named "keys" if it doesn't already exist. This is where we will store our generated keys:</b></li>
    <pre><code>cd Documents
mkdir keys
cd keys</code></pre>

    <li><b>Now, let's generate an RSA key pair. The following command will create a private key named "corp.515support.com.key" with a key length of 2048 bits:</b></li>
    <pre><code>"Generate a Asymmetric encryption RSA key pair" openssl genrsa -out corp.515support.com.key 2048</code></pre>

    <li><b>To view the content of the private key you just generated, you can use the "cat" command:</b></li>
    <pre><code>"Display the private key" cat corp.515support.com.key</code></pre>

    <li><b>Next, we'll extract the corresponding public key from the private key. This public key will be used when generating a Certificate Signing Request (CSR) in a later section:</b></li>
    <pre><code>"Extract the public key file to a file for export with CSR" openssl rsa -in corp.515support.com.key -pubout -out corp.515support.com_public.key</code></pre>

    <li><b>To verify that both the private and public keys have been generated and saved successfully, you can list the files in the current directory:</b></li>
    <pre><code>ls</code></pre>

    <li><b>Finally, you can view the content of the public key using the "cat" command:</b></li>
    <pre><code>"Display the public key" cat corp.515support.com_public.key</code></pre>

    <li><b>You've now successfully generated an RSA key pair, obtained the private key, and extracted the public key. These keys are fundamental to secure communication and certificate management in OpenSSL.</b></li>
</ul>

<ul>
    <li><b>In this section, we will create a Certificate Signing Request (CSR) using OpenSSL. A CSR is a request for a digital certificate that includes your public key and essential information about your organization:</b></li>
    <ol>
        <li><b>To generate the CSR, use the following command:</b></li>
        <pre><code>"Generating signing certificate" openssl req -new -key corp.515support.com.key -out corp.515support.com.csr</code></pre>

        <li><b>You can verify the content of the CSR with this command:</b></li>
        <pre><code>"Verify the certificate request" openssl req -text -in corp.515support.com.csr -noout -verify</code></pre>

        <li><b>To view the CSR that would be sent to the certificate authority, use the following command:</b></li>
        <pre><code>"Display the certificate signing request that would be sent to the certificate authority" cat corp.515support.com.csr</code></pre>

        <li><b>Now you have successfully generated a Certificate Signing Request (CSR) and can review its content. The CSR is a crucial step in obtaining a digital certificate for your server or application.</b></li>
    </ol>
</ul>

<ul>
    <li><b>In this section, we will explore how to convert certificate formats using OpenSSL. Converting between formats is often necessary for compatibility with different systems or applications:</b></li>
    <ol>
        <li><b>To generate a self-signed certificate, run the following command:</b></li>
        <pre><code>"Generating a self-signed certificate" openssl req -newkey rsa:2048 -nodes -keyout corp.515support.com.key -x509 -days 100 -out corp.515support.com.crt</code></pre>

        <li><b>To merge the ".key" and ".crt" files into a ".pfx" (PKCS #12) file, use this command:</b></li>
        <pre><code>"Merging .key and .crt files into a .pfx file" openssl pkcs12 -export -name "corp.515support.com" -out corp.515support.com.pfx -inkey corp.515support.com.key -in corp.515support.com.crt</code></pre>

        <li><b>You've now learned how to generate a self-signed certificate and convert it into a different format (".pfx"). This flexibility in format conversion is valuable for various deployment scenarios and system compatibility.</b></li>
    </ol>
</ul>
