# rails-api
[![Actions Status](https://github.com/kajirikajiri/rails-api/workflows/Ruby/badge.svg)](https://github.com/kajirikajiri/rails-api/actions)


* github actionsでrspecを実行
* docker-composeで起動
* containerをherokuにpush済み
* https://rocky-plateau-44026.herokuapp.com/

# 動作確認

#### Missing token
```bash
curl -X POST \
     -H "Content-Type: application/json" rocky-plateau-44026.herokuapp.com/todos
# -> {"message":"Missing token"}
```

#### signup
```bash
curl -X POST \
     -H "Content-Type: application/json" \
     -d '{"name":"NAME", "email":"email@mail.com", "password":"foobar", "password_confirmation":"foobar"}' \
     rocky-plateau-44026.herokuapp.com/signup
# -> {"message":"Account created successfully","auth_token":"eyJhbGciOiJIUzI1NiJ9.eyJ1c2VyX2lkIjoyLCJleHAiOjE1NzgzMDYyNDV9.wS5Q2OdCHyVkUtOAvh-VNdXfE83aptOHTxhhKZhxlmo"}
```

#### get todos witt valid token
```bash
curl -X GET \
     -H "Authorization: OAuth eyJhbGciOiJIUzI1NiJ9.eyJ1c2VyX2lkIjoyLCJleHAiOjE1NzgzMDYyNDV9.wS5Q2OdCHyVkUtOAvh-VNdXfE83aptOHTxhhKZhxlmo" \
     rocky-plateau-44026.herokuapp.com/todos
# -> []
```

#### create todos with valid token
```bash
curl -X POST\
     -H "Authorization: OAuth eyJhbGciOiJIUzI1NiJ9.eyJ1c2VyX2lkIjoyLCJleHAiOjE1NzgzMDYyNDV9.wS5Q2OdCHyVkUtOAvh-VNdXfE83aptOHTxhhKZhxlmo" \
     -H "Content-type: application/json" \
     -d '{"title":"TITLE"}' rocky-plateau-44026.herokuapp.com/todos
# -> {"id":3,"title":"TITLE","created_by":"2","created_at":"2020-01-05T10:37:42.751Z","updated_at":"2020-01-05T10:37:42.751Z"}
```

#### get todos with valid token
```bash
curl -X GET -H "Authorization: OAuth eyJhbGciOiJIUzI1NiJ9.eyJ1c2VyX2lkIjoyLCJleHAiOjE1NzgzMDYyNDV9.wS5Q2OdCHyVkUtOAvh-VNdXfE83aptOHTxhhKZhxlmo" rocky-plateau-44026.herokuapp.com/todos
# -> [{"id":3,"title":"TITLE","created_by":"2","created_at":"2020-01-05T10:37:42.751Z","updated_at":"2020-01-05T10:37:42.751Z"}]
```
