# Web / URL / API Terminology — Master Notes

## 1. URL Structure Terms

**URL** → Uniform Resource Locator; full address to locate a resource
- Example: `https://api.site.com:443/v1/users?id=42#top`

**URI** → Uniform Resource Identifier; broader umbrella → identifies a resource (URL is a type of URI)
- URL ⊂ URI

**URN** → Uniform Resource Name; identifies *by name*, not location
- Example: `urn:isbn:0451450523`

**Scheme** → protocol to access resource
- Before `://` → `https`, `http`, `ftp`, `ws`, `mailto`

**Host** → server address (domain or IP)
- `api.site.com`, `192.168.1.1`, `localhost`

**Subdomain** → prefix segment of host
- In `api.site.com` → `api` is subdomain

**Domain** → registered name of site
- `site.com`

**TLD** → Top-Level Domain; last segment
- `.com`, `.org`, `.io`

**Port** → numbered channel on host
- After `:` → `443` (optional; defaults: https→443, http→80)

**Path** → resource location/route on server
- Starts `/` → `/v1/users`

**Query string** → all key-value inputs after `?`
- `?id=42&sort=name`

**Query parameter** → one key-value pair in query
- `id=42`

**Parameter key** → name part → `id`

**Parameter value** → data part → `42`

**Fragment / Anchor** → client-side location marker
- After `#` → `top` (NOT sent to server)

---

## 2. HTTP Method Terms

**HTTP method (verb)** → action to perform on resource

| Method | Action | Idempotent | Has body |
|---|---|---|---|
| GET | read/fetch | ✓ | usually no |
| POST | create | ✗ | yes |
| PUT | replace fully | ✓ | yes |
| PATCH | update partially | ✗ | yes |
| DELETE | remove | ✓ | optional |
| HEAD | headers only | ✓ | no |
| OPTIONS | check allowed methods | ✓ | no |

- **Idempotent** → same call repeated = same result

---

## 3. API Terms

**API** → Application Programming Interface; contract for software-to-software communication

**Endpoint** → specific path that performs one function
- `https://api.site.com/users` (host + path, no query)

**REST** → architectural style using HTTP + resources + verbs
- Stateless, resource-based URLs

**RESTful** → API that follows REST principles

**Resource** → the "thing" an endpoint acts on
- `/users`, `/products`

**Request** → message client sends to server

**Response** → message server returns to client

**Payload / Body** → data sent in request/response
- Often JSON

**Header** → metadata key-value pairs in request/response
- `Content-Type: application/json`, `Authorization: Bearer ...`

---

## 4. Parameter Location Types

**Path parameter** → variable inside the path
- `/users/{id}` → `/users/42`

**Query parameter** → after `?`
- `?sort=name`

**Header parameter** → in headers
- `Authorization: ...`

**Body parameter** → inside request body
- `{ "name": "Sam" }`

---

## 5. Status Code Terms

**Status code** → 3-digit response result

| Range | Meaning | Example |
|---|---|---|
| 1xx | informational | 100 Continue |
| 2xx | success | 200 OK, 201 Created |
| 3xx | redirect | 301 Moved, 304 Not Modified |
| 4xx | client error | 400, 401, 403, 404 |
| 5xx | server error | 500, 502, 503 |

- 401 → Unauthorized (not authenticated)
- 403 → Forbidden (authenticated, no permission)
- 404 → Not Found

---

## 6. Data Format Terms

**JSON** → JavaScript Object Notation; key-value text format
- `{ "id": 42, "name": "Sam" }`

**XML** → tag-based markup format
- `<user><id>42</id></user>`

**Content-Type** → header declaring body format
- `application/json`, `text/html`

**MIME type** → standard label for file/data format
- Same values as Content-Type

---

## 7. Auth & Security Terms

**Authentication** → verify *who* you are

**Authorization** → verify *what* you're allowed to do

**API key** → secret token identifying caller
- Often in header or query

**Token** → credential proving identity/access
- e.g. JWT, Bearer token

**Bearer token** → token sent in `Authorization: Bearer <token>`

**OAuth** → delegated authorization framework
- Lets app act on user's behalf without password

**HTTPS** → HTTP + TLS encryption
- Secure transport

---

## 8. Encoding & Misc Terms

**URL encoding (percent-encoding)** → replace unsafe chars with `%XX`
- space → `%20`, `&` → `%26`

**Slug** → human-readable path segment
- `/blog/how-to-bake-bread`

**Route** → server-side mapping of path → handler
- Often interchangeable with "endpoint"

---

## Quick Relationship Map

```
URI
 └── URL (locator)
      ├── scheme :// host : port / path ? query # fragment
      └── targets → endpoint → resource

API request  = method + URL + headers + body
API response = status code + headers + body
```

---

## Visual: URL Anatomy

```
https://api.site.com:443/v1/users?id=42&sort=name#top
└─┬─┘   └────┬─────┘└┬┘└──┬───┘└──────┬──────┘└┬┘
scheme    host    port  path        query    fragment
```

- URL = whole string
- Endpoint ⊂ URL → address minus query
- Param key ⊂ query/body → just the label
