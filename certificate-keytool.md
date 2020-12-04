# Criando certificado auto-assinado usando Keytool

### Gerando par de chaves

Criando um certificado auto-assinado e o armazenando na KeyStore

```
keytool -genkeypair -alias ALIAS_NAME -keyalg RSA -validity #_OF_DAYS -keysize 1024 -keystore KEYSTORE_NAME.jks
```

* **ALIAS_NAME**: nome do alias do certificado.

* **#_OF_DAYS**: número de dias a qual o certificado será válido.

* **1024**: tamanho da chave. Valor recomendado é 2048.

* **KEYSTORE_NAME**: Caminho/nome do arquivo keystore.

### Formato da Keystore

Caso a Keystore esteja em formato `.jks` pode ser necessário mudar o tipo de armazenamento da keystore para `pkcs12`
```
keytool -importkeystore -srckeystore KEYSTORE_NAME.jks -destkeystore KEYSTORE_NAME.pkcs12 -deststoretype pkcs12
```

* **KEYSTORE_NAME**: Caminho/nome do arquivo keystore.

### Exportando o certificado

Exportando um certificado contido na keystore para um arquivo `.cert`

```
keytool -export -alias ALIAS_NAME -keystore KEYSTORE_NAME.pkcs -rfc -file CERTIFICATE_NAME.cert
```
* **ALIAS_NAME**: nome do alias do certificado.

* **KEYSTORE_NAME**: Caminho/nome do arquivo keystore.

* **CERTIFICATE_NAME**: Caminho/nome do arquivo certificado.

### Mostrando certificado

Para mostrar em tela o certificado

```
keytool -printcert -v -file CERTIFICATE_NAME.crt
```
* **CERTIFICATE_NAME**: Caminho/nome do arquivo certificado.
