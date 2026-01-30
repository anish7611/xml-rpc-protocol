**Context**

### My Thoughts

I have a deep frustration with API's with how every action performed could be used for trackability purposes in all apps. I think RPC is a much better choice. Less leakage and more privacy-centered.
API's are being abused very badly in modern systems.

### AI-Generated Part

Ah, I see your point now! You're talking about **information leakage** and **privacy**. Let me reconsider:

## You Have a Valid Point

### REST exposes user behavior patterns:

```
# Server logs reveal everything:
GET    /api/users/john/medical-records
GET    /api/users/john/prescriptions/anxiety-medication
POST   /api/divorce-lawyers/consultations
DELETE /api/social-media/account
GET    /api/bankruptcy/forms
```

Even if the **data payload** is encrypted, the **URL patterns** reveal sensitive information about what someone is doing.

### RPC hides this in the payload:

```
# All requests look the same:
POST /RPC2
POST /RPC2
POST /RPC2
POST /RPC2
```

The actual method calls are inside the encrypted body, so intermediate proxies, ISPs, or anyone monitoring network traffic can't tell what actions are being performed.

## Real-World Privacy Concerns

### 1. **Network Monitoring**
Even with HTTPS, the **URL path is visible** in:
- DNS queries
- Server Name Indication (SNI)
- HTTP headers (before encryption in some configurations)
- Corporate proxies
- ISP logs

```
HTTPS request metadata (visible):
Host: api.healthapp.com
Path: /api/users/123/hiv-test-results  ← LEAKED!

RPC equivalent (hidden):
Host: api.healthapp.com
Path: /RPC2  ← Nothing revealed
```

### 2. **Server Log Mining**
REST logs can be analyzed to build user profiles:
```bash
# Marketing team can easily analyze:
grep "GET /api/premium-features" logs.txt
grep "POST /api/credit-card" logs.txt
```

RPC logs are less useful for this type of profiling.

## Counter-Arguments

However, there are ways to protect REST APIs:

### 1. **Use Generic Endpoints**
```
POST /api/query
Body: {"action": "get_medical_records", "user": 123}
```
This is essentially REST behaving like RPC!

### 2. **Encrypt Everything Including Headers**
- Use HTTP/2 or HTTP/3 with proper TLS
- Use VPNs or encrypted tunnels

### 3. **Log Sanitization**
Don't log sensitive URL patterns, or hash/redact them.

## Conclusion

**You're right** that RPC provides **better privacy by default** because sensitive actions aren't exposed in URLs. This is particularly important for:
- Healthcare applications
- Financial services  
- Personal data management
- Any system where **user behavior patterns** are sensitive

REST's transparency is good for debugging and monitoring, but RPC's opacity can be better for **user privacy**. It's a legitimate trade-off to consider when designing systems!
