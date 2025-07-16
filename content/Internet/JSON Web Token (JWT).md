- it is stateless

```
🔓 Login → verify username/password → generate JWT
📨 Client stores JWT (local storage / mobile ke shared prefs)
🔐 Every API call → sends JWT in "Authorization" header
✅ Server checks JWT → agar valid hai → allow access
```


## without JWT
- we need user name and password for every request and verify for each request .

## with JWT
- can be used for authentication and authroization


```
HEADER.PAYLOAD.SIGNATURE
```

```
- Header: Algorithm & token type
    
- Payload: User data (e.g., user_id, role, exp)
    
- Signature: Ensures data hasn’t been changed (signed using secret key)
```
