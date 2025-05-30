﻿
---

## 📌 1. GET
**Purpose:** Retrieve data from a server.

**Characteristics:**
- ✅ Safe (doesn't alter data)
- ✅ Idempotent (same result on repeated calls)

**Example:**
```
GET /users/123
```

**JavaScript:**
```javascript
fetch('https://api.example.com/users/123')
  .then(res => res.json())
  .then(data => console.log(data));
```

---

## ✍️ 2. POST
**Purpose:** Create a new resource.

**Characteristics:**
- ❌ Not idempotent (may create duplicates)

**Example:**
```
POST /users
Content-Type: application/json

{
  "name": "John",
  "email": "john@example.com"
}
```

**JavaScript:**
```javascript
fetch('https://api.example.com/users', {
  method: 'POST',
  headers: { 'Content-Type': 'application/json' },
  body: JSON.stringify({ name: "John", email: "john@example.com" })
});
```

---

## 🛠️ 3. PUT
**Purpose:** Replace an existing resource completely.

**Characteristics:**
- ✅ Idempotent

**Example:**
```
PUT /users/123
Content-Type: application/json

{
  "name": "John Updated",
  "email": "john.updated@example.com"
}
```

**JavaScript:**
```javascript
fetch('https://api.example.com/users/123', {
  method: 'PUT',
  headers: { 'Content-Type': 'application/json' },
  body: JSON.stringify({ name: "John Updated", email: "john.updated@example.com" })
});
```

---

## 🩹 4. PATCH
**Purpose:** Partially update an existing resource.

**Characteristics:**
- ✅ Idempotent (when applied correctly)

**Example:**
```
PATCH /users/123
Content-Type: application/json

{
  "email": "newemail@example.com"
}
```

**JavaScript:**
```javascript
fetch('https://api.example.com/users/123', {
  method: 'PATCH',
  headers: { 'Content-Type': 'application/json' },
  body: JSON.stringify({ email: "newemail@example.com" })
});
```

---

## ❌ 5. DELETE
**Purpose:** Remove a resource from the server.

**Example:**
```
DELETE /users/123
```

**JavaScript:**
```javascript
fetch('https://api.example.com/users/123', {
  method: 'DELETE'
});
```

---

## ℹ️ 6. HEAD
**Purpose:** Same as GET but returns headers only.

**Example:**
```
HEAD /users/123
```

**JavaScript:**
```javascript
fetch('https://api.example.com/users/123', { method: 'HEAD' });
```

---

## 📚 7. OPTIONS
**Purpose:** Discover allowed HTTP methods on a resource.

**Example:**
```
OPTIONS /users
```

**JavaScript:**
```javascript
fetch('https://api.example.com/users', { method: 'OPTIONS' });
```

---

## 🔍 8. TRACE
**Purpose:** Echo the received request back for testing/debugging.

**Example:**
```
TRACE / HTTP/1.1
```

(Note: Rarely used and often disabled for security.)

---

## 🔐 9. CONNECT
**Purpose:** Establish a tunnel (commonly used for HTTPS through proxies).

**Example:**
```
CONNECT www.example.com:443 HTTP/1.1
```

---

## 🗂 WebDAV Methods (Less Common)

### PROPFIND
- Retrieve properties of a resource.

### PROPPATCH
- Update properties.

### MKCOL
- Create a collection (like a directory).

### COPY
- Copy a resource.

### MOVE
- Move a resource.

### LOCK / UNLOCK
- Lock/unlock a resource for editing.

---

## ✅ Quick Summary Table
| Method | Action         | Safe | Idempotent | Typical Use Case           |
|--------|----------------|------|------------|----------------------------|
| GET    | Read data      | ✅   | ✅         | Get user profile           |
| POST   | Create data    | ❌   | ❌         | Register a new user        |
| PUT    | Replace data   | ❌   | ✅         | Replace a user's profile   |
| PATCH  | Update data    | ❌   | ✅         | Update just the email      |
| DELETE | Remove data    | ❌   | ✅         | Delete a user              |
| HEAD   | Header only    | ✅   | ✅         | Check resource exists      |
| OPTIONS| Capabilities   | ✅   | ✅         | Discover methods allowed   |
| TRACE  | Debug/echo     | ✅   | ✅         | Diagnostic purposes        |
| CONNECT| Tunnel proxy   | ❌   | ❌         | Secure proxy connections   |
| WebDAV | Remote mgmt    | ❌   | ❌         | File system-like ops       |

---

