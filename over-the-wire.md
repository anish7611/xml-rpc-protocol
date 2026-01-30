### XML-RPC Request

```
<?xml version="1.0"?>
<methodCall>
  <methodName>get_customer</methodName>
  <params>
    <param>
      <value><int>101</int></value>
    </param>
  </params>
</methodCall>
```

### XML-RPC Response

```
<?xml version="1.0"?>
<methodResponse>
  <params>
    <param>
      <value>
        <struct>
          <member>
            <name>name</name>
            <value><string>John Doe</string></value>
          </member>
          <member>
            <name>balance</name>
            <value><double>1500.0</double></value>
          </member>
        </struct>
      </value>
    </param>
  </params>
</methodResponse>
```

### HTTP Request

```
POST /RPC2 HTTP/1.1
Host: localhost:8000
User-Agent: xmlrpclib.py/1.0.1 (by www.pythonware.com)
Content-Type: text/xml
Content-Length: 192

<?xml version="1.0"?>
<methodCall>
  <methodName>get_customer</methodName>
  <params>
    <param>
      <value><int>101</int></value>
    </param>
  </params>
</methodCall>
```

### HTTP Response

```
HTTP/1.1 200 OK
Server: BaseHTTP/0.6 Python/3.9.0
Date: Tue, 30 Jan 2024 10:15:30 GMT
Content-Type: text/xml
Content-Length: 425

<?xml version="1.0"?>
<methodResponse>
  <params>
    <param>
      <value>
        <struct>
          <member>
            <name>name</name>
            <value><string>John Doe</string></value>
          </member>
          <member>
            <name>email</name>
            <value><string>john@example.com</string></value>
          </member>
          <member>
            <name>balance</name>
            <value><double>1500.0</double></value>
          </member>
        </struct>
      </value>
    </param>
  </params>
</methodResponse>
```

### Compare to Modern REST API

### For comparison, here's the same data exchange using a modern REST API:
Request http

```
GET /api/customers/101 HTTP/1.1
Host: localhost:8000
Accept: application/json
Response
httpHTTP/1.1 200 OK
Content-Type: application/json
Content-Length: 95

{
  "name": "John Doe",
  "email": "john@example.com",
  "balance": 1500.0
}
```

### Key differences:

```
XML-RPC: 617 bytes total, verbose XML encoding
REST API: ~190 bytes total, clean JSON
XML-RPC always uses POST (calling a method)
REST uses HTTP verbs semantically (GET, POST, PUT, DELETE)
```
