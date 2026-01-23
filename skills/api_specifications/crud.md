# CRUD Basics

## Resource: /apx/characters

### Routes

| Action | Method | Path |
|--------|--------|------|
| Read list or filtered | GET | /apx/characters |
| Search | POST | /apx/characters |
| Read by id | GET | /apx/characters/{id} |
| Create | PUT | /apx/characters |
| Update | PUT | /apx/characters/{id} |
| Delete | DELETE | /apx/characters/{id} |

### curl examples

```bash
curl -X GET http://localhost:8080/apx/characters
```

```bash
curl -X POST http://localhost:8080/apx/characters \
  -H "Content-Type: application/json" \
  -d '{"table":"characters","filters":{"name":"ana"}}'
```

```bash
curl -X GET http://localhost:8080/apx/characters/123
```

```bash
curl -X PUT http://localhost:8080/apx/characters \
  -H "Content-Type: application/json" \
  -d '{"table":"characters","data":{"name":"ana"}}'
```

```bash
curl -X PUT http://localhost:8080/apx/characters/123 \
  -H "Content-Type: application/json" \
  -d '{"table":"characters","data":{"id":"123","name":"ana updated"}}'
```

```bash
curl -X DELETE http://localhost:8080/apx/characters/123
```

### http examples

```bash
http GET http://localhost:8080/apx/characters
```

```bash
http POST http://localhost:8080/apx/characters \
  table=characters \
  filters[name]=ana
```

```bash
http GET http://localhost:8080/apx/characters/123
```

```bash
http PUT http://localhost:8080/apx/characters \
  table=characters \
  data[name]=ana
```

```bash
http PUT http://localhost:8080/apx/characters/123 \
  table=characters \
  data[id]=123 \
  data[name]="ana updated"
```

```bash
http DELETE http://localhost:8080/apx/characters/123
```
