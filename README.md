# WIF Serialization

WIF is the serialization of a Private Key.

#### Find the WIF Format of the following:

* \\(2^{256}-2^{199}\\), mainnet, compressed
* \\(2^{256}-2^{201}\\), testnet, uncompressed
* 0dba685b4511dbd3d368e5c4358a1277de9486447af7b3604a69b8d9d8b7889d, mainnet, uncompressed
* 1cca23de92fd1862fb5b76e5f4f50eb082165e5191e116c18ed1a6b24be6a53f, testnet, compressed


```python
# WIF Example
from helper import encode_base58_checksum

secret = 2**256 - 2**200
s = secret.to_bytes(32, 'big')
print(encode_base58_checksum(b'\x80'+s))
print(encode_base58_checksum(b'\x80'+s+b'\x01'))
print(encode_base58_checksum(b'\xef'+s))
print(encode_base58_checksum(b'\xef'+s+b'\x01'))
```


```python
# Exercise 3.1
from helper import encode_base58_checksum

components = (
    # (secret, testnet, compressed)
    (2**256-2**199, False, True),
    (2**256-2**201, True, False),
    (0x0dba685b4511dbd3d368e5c4358a1277de9486447af7b3604a69b8d9d8b7889d, False, False),
    (0x1cca23de92fd1862fb5b76e5f4f50eb082165e5191e116c18ed1a6b24be6a53f, True, True),
)

# iterate through components
    # get the private key in 32-byte big-endian: num.to_bytes(32, 'big')
    # prepend b'\x80' for mainnet, b'\xef' for testnet
    # append b'\x01' for compressed
    # base58 the whole thing with checksum
    # print the wif
```
