This example is using AWS Request and Response Proxy Model, provided by AWS itself.
If you want to test any changes don't forget to run `make` inside the service directory.
 

# API Specs
- Viết 4 api, gọi vào database postgres
  - create user
  - update user
  - delete user by username
  - get user list by username

- Script create table user
```sql
CREATE TABLE "users" (
    "id" bigserial,
    username character varying(50) COLLATE pg_catalog."default",
    name character varying(50) COLLATE pg_catalog."default" NOT NULL,
    phone character varying(50) COLLATE pg_catalog."default",
    PRIMARY KEY ("id")
);
```

### API Insert
- create user với username, name, phone. Phải check username tồn tại duy nhất trong table, không sử dụng unique của database
- input:
```
{
    "requestId": {{uuid}},
    "requestTime": {{timeRPC3339}},
    "data": {
        "username": {{string}},
        "name": {{string}},
        "phone": {{string}}
    }
}
```
- output:
```
{
    "responseId": {{requestId}},
    "responseTime": {{timeRPC3339}},
    "responseCode": {{string}},
    "responseMessage": {{string}}
}
```

### API Update
- update user by username. Thông tin update là name và phone.
- input:
```
{
    "requestId": {{uuid}},
    "requestTime": {{timeRPC3339}},
    "data": {
        "username": {{string}},
        "name": {{string}},
        "phone": {{string}}
    }
}
```

- output:
```
{
    "responseId": {{requestId}},
    "responseTime": {{timeRPC3339}},
    "responseCode": {{string}},
    "responseMessage": {{string}},
}
```

### API Delete
- delete user by username
- input:
```
{
    "requestId": {{uuid}},
    "requestTime": {{timeRPC3339}},
    "data": {
        "username": {{string}}
    }
}
```

- output:
```
{
    "responseId": {{requestId}},
    "responseTime": {{timeRPC3339}},
    "responseCode": {{string}},
    "responseMessage": {{string}},
}
```

### API Get list
- get list by username
- input:
```
{
    "requestId": {{uuid}},
    "requestTime": {{timeRPC3339}},
    "data": {
        "username": {{string}}
    }
}
```

- output:
```
{
    "responseId": {{uuid}},
    "responseTime": {{timeRPC3339}},
    "responseCode": {{string}},
    "responseMessage": {{string}},
    "data": {
        "username": {{string}},
        "name": {{string}},
        "phone": {{string}}
    }
}
```