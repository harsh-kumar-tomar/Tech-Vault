this lib is used to hash given data.

hash algo in hashlib

| Function | Output Length      | Use Case                                    |
| -------- | ------------------ | ------------------------------------------- |
| `md5`    | 128 bits (32 hex)  | Fast but insecure (don't use for passwords) |
| `sha1`   | 160 bits (40 hex)  | Better than MD5 but still broken            |
| `sha256` | 256 bits (64 hex)  | Strong and commonly used                    |
| `sha512` | 512 bits (128 hex) | Very strong, more secure                    |
```python
s = "Harsh"

# return  hashlib.hash object 
temp = hashlib.sha256(s.encode())

#  hashlib.hash -> raw bytes but when used with print() it shows hexadeciamal of 0/1 
temp.digest()

# hashlib.hash -> hexadecimal string 
temp.hexdigest()

```