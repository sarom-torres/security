# Criando certificado auto-assinado usando OpenSSL

## Certificado contendo SubjectAlternativeName

### Gerando chave privada 

O seguinte comando irá gerar uma chave RSA de 1024 bits em um arquivo `.key`.
O comando `-des3` irá solicitar uma senha para a chave privada, caso não queria proteger a chave privada com senha basta remover o comando.


`openssl genrsa -des3 -out lased.key 1024`

### Gerando certificado
O seguinte comando irá gerar um certificado CSR (Certificate Signing Request), contendo a chave privada gerada anteriormente e com os dados de entrada do comando `-subj`.

```
openssl req -new -key lased.key -out lased.csr -subj "/C=BR/ST=Santa Catarina/L=Sao Jose/O=IFSC/CN=ModeloArev1:XXXXXXXXYYYYZZ/" -config config.cnf
```

O parâmetro `-config` receberá um arquivo de configuração com a extensão `.conf` contendo o OID e o valor associado ao identificador.
Conteúdo do arquivo de configuração:

```
[req]
req_extensions = v3_req
distinguished_name = req_distinguished_name

[req_distinguished_name]

[v3_req]
subjectAltName=@subject_alt_section

[subject_alt_section]
otherName=2.16.76.1.3.1;UTF8String:61585866000104
```
O resultado do seguinte comando será um arquivo `.csr`.

### Gerando certificado auto-assinado

O comando abaixo irá gerar um certificado X509 auto-assinado. Neste caso deverá ser passado como parâmetro o arquivo `.csr`, a chave privada `.key` e o arquivo de configuração `.conf`.

```
openssl x509 -req -days 365 -in lased.csr -signkey lased.key -out lased.cert -extfile config.cnf -extensions v3_req
```
O resultado do comando será um arquivo `.cert`.

### Criando arquivo PEM

```
cat lased.key > lased.pem
cat lased.cert >> lased.pem
```

### Exportando certificado para KeyStore
O seguinte comando irá criar uma KeyStore com extensão `.pkcs12` e exportará o certificado PEM.

`openssl pkcs12 -export -in lased.pem -out keystore.pkcs12`

### Conteúdo da KeyStore

O seguinte comando irá mostrar o conteúdo da KeyStore

`keytool -v -list -keystore keystore.pkcs12`

