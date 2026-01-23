# CRUDSL and RSL Patterns

## CRUDSL

CRUDSL includes Create, Read, Update, Delete, Search, and List.

| Action | Method | Path |
|--------|--------|------|
| List | get | /api |
| Read | GET | /api/{table} |
| Search | POST | /api/{table} |
| Read by id | get | /api/{table}/{id} |
| Create | put | /api/{table} |
| Update | put | /api/{table}/{id} |
| Delete | delete | /api/{table}/{id} |

### curl examples

```bash
curl -X GET http://localhost:8080/api
```

```bash
curl -X POST http://localhost:8080/api/characters \
  -H "Content-Type: application/json" \
  -d '{"table":"characters","filters":{"name":"ana"}}'
```

```bash
curl -X PUT http://localhost:8080/api/characters \
  -H "Content-Type: application/json" \
  -d '{"table":"characters","data":{"name":"ana"}}'
```

```bash
curl -X DELETE http://localhost:8080/api/characters/123
```

## RSL

RSL includes Read, Search, and List.

| Action | Method | Path |
|--------|--------|------|
| List | get | /source |
| Search | post | /source/{table} |
| Read | get | /source/{table} |
| Read by id | get | /source/{table}/{id} |

### http examples

```bash
http GET http://localhost:8080/source
```

```bash
http POST http://localhost:8080/source/characters \
  table=characters \
  filters[name]=ana
```

```bash
http GET http://localhost:8080/source/characters
```

```bash
http GET http://localhost:8080/source/characters/123
```
