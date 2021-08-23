## Signing Templates and Signing Contracts GSoC 2021

- Student: [Sanket Shevkar](https://github.com/sanketshevkar)
- Mentor: [Martin Halford](https://github.com/martinhalford)
- Organisation: [Accord Project](https://github.com/accordproject)

# Template Signing

#### Purpose: 
The developer/author should be able to digitally sign the template that the developer has developed. Dicussion about this can be found [here](https://github.com/accordproject/cicero/issues/262).

- Pull Request [#688](https://github.com/accordproject/cicero/pull/688)
- Status: Merged
- Closes [#671](https://github.com/accordproject/cicero/issues/671)

### Prerequisites

Create a PEM file containing the the private key and the certificate of the developer,
following should be the format of the PEM file:

```
-----BEGIN RSA PRIVATE KEY-----
(Private Key: domain_name.key contents)
-----END RSA PRIVATE KEY-----
-----BEGIN CERTIFICATE-----
(Primary SSL certificate: domain_name.crt contents)
-----END CERTIFICATE-----
```

Create a pkcs#12 file:

`openssl pkcs12 -export -in server.pem -out keystore.pkcs12`

### Usage

```
cicero archive --template [template path] --output [output archive path] --keystore [pkcs#12 keystore path] --passphrase [password of the keystore]

cicero verify --template [template path]
```

# Contract Signing

#### Purpose: 
The parties involved in execution of a certain contract should be able to digitally sign the contract to validate it model, logic, data/text. Dicussion about this can be found [here](https://github.com/accordproject/cicero/issues/558).

- Pull Request [#689](https://github.com/accordproject/cicero/pull/689)
- Status: Open
- This a part of a much larger new feature that is being built i.e. Contract Instances. 
More information can be found [here](https://github.com/accordproject/lab-contract-design). 

### Prerequisites

Create a PEM file containing the the private key and the certificate of the party,
following should be the format of the PEM file:

```
-----BEGIN RSA PRIVATE KEY-----
(Private Key: domain_name.key contents)
-----END RSA PRIVATE KEY-----
-----BEGIN CERTIFICATE-----
(Primary SSL certificate: domain_name.crt contents)
-----END CERTIFICATE-----
```

Create a pkcs#12 file:

`openssl pkcs12 -export -in server.pem -out keystore.pkcs12`

### Usage

```
cicero sign --contract [contract path] --output [output archive path] --keystore [pkcs#12 keystore path] --passphrase [password of the keystore] --signatory [name of the signatory]

cicero verify --contract [contract path]
```
