# Task3
 public key encryption scenario that would cover security and digital signature
# Automated File Generation and Digital Signature 
#!/bin/bash

# Generate a file with the current date
echo "This file was generated on $(date)" > generated_file.txt

# Encrypt the file using Bob's public key
openssl rsautl -encrypt -inkey bob_public.pem -pubin -in generated_file.txt -out encrypted_file.enc

# Sign the file using Alice's private key
openssl dgst -sha256 -sign alice_private.pem -out generated_file.sig generated_file.txt

# Send the encrypted file and signature to Bob's system (replace 'bob@ip_address')
scp encrypted_file.enc generated_file.sig bob@ip_address:~/Bob/
