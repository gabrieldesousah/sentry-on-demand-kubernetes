# On Docker:
- Crie e preencha a Secret Key SENTRY_SECRET_KEY com uma string random 32 char
  (Obs.: o comando anaixo cria e destrói um container com a finalidade de criar uma senha)
  command: docker run --rm sentry:8.10.0 config generate-secret-key

- Execute o comando para criar os containeres:
  docker-compose up -d
- Execute "docker-compose exec sentry sentry upgrade" para configurar o banco de dados e criar o usuário "admin"
- Execute o comando "docker-compose restart sentry"
  Sentry estará rodando na porta pública 9090

# On Kubernetes:

* Need to install postgres volume:
- In localhost:
```kubectl apply -f local/```

- In AWS:
```kubectl apply -f local/```

* Need to install all services:
```kubectl apply -f kubernetes/```

* exec the sentry pod and execute upgrade to install the database on postgres:
```kubectl exec -it <pod sentry> sentry upgrade```

* Now all is fine and running
