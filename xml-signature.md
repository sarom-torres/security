# XML Signature 

## Conceitos

Uma assinatura digital é um valor calculado por meio de um algoritmo criptográfico e anexado a um determinado conteúdo digital que pode ser usado para verificar a autenticidade e a integridade de um dado específico. ([Oracle,2007](https://www.oracle.com/technical-resources/articles/java/dig-signature-api.html)). 

A assinatura digital baseia-se numa infraestrutura de chave pública (PKI - *Public Key Infrastructure*), ou seja, utiliza-se de certificados digitais e criptografia de chave pública.

Uma *XML Signature* ou *XMLDsign* é a representação XML de uma assinatura digital aplicada em um determinado documento a qual possui diversas regras de criação e validação. Uma XML Sinature não é restrita apenas a documentos XML, sendo que é possível assinar diferentes tipos de dados, tais como binários ou ou textos([Microsoft,2016](https://docs.microsoft.com/en-us/previous-versions/windows/desktop/ms762296(v=vs.85)))

Existem três tipos de assinatura digital:
- Detached
- Enveloping
- Enveloped

