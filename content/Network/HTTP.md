an **HTTP request** is just plain text sent from a client (like a browser or app) to a server, following a specific format.
http request format = request line + request header + reuqest body

if server reponed back its called http response with status line + reponse header + reponse body

http format 

1. request line = method (get or post) + path + http version
```python
METHOD PATH HTTP/VERSION
GET /index.html HTTP/1.1
```

2. request headers (meta data) = who sending + 
headers are case insensitive
have key val pair pattern

these key val can change depending upon server and client 
some key val are mandatory , some are optional 

```python
Host: example.com
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) Chrome/112.0
Accept: application/json
Content-Type: application/json
Content-Length: 47
Authorization: Bearer abcdef1234567890
```


3. blank line (end of header)
4. body (optional) = post or put data




does client send http request randomly to server ?
first it forms connection -> http request 

connection phase
client send 