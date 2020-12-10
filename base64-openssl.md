# Encode and Decode base64 using openssl

## Encode

```
 openssl base64 -e <<< 'Hello World'
```

## Decode

Para um linha menor que 64 caracteres
```
openssl base64 -d <<< "SGVsbG8gV29ybGQK"
```
Para um linha maior que 64 caracteres.
```
openssl base64 -d -A <<<
'SGVsbG8gZXZlcnlib2R5LiBJJ20gdHJ5aW5nIHRvIHVuZGVyc3RhbmQgaG93IHRoaXMgdG9vbCB3b3JrcyB0aGUgSSBuZWVkIHRvIHdyaXRlIGEgbGluZSB2ZXJ5IHZlcnkgbG9uZyB0byB1c2UgdGhpcyBjb21tYW5kIAo="'

```
