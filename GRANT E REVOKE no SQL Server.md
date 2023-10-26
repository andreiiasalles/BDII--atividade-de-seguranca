# Criando o login

```sql
USE master;
CREATE LOGIN Andreia
WITH PASSWORD = '123';
```

No explorador de objetos, expanda segurança → Atualizar e expanda os logins → O login Andreia foi criado com sucesso.

![image](https://github.com/andreiiasalles/BDII--atividade-de-seguranca/assets/57154658/b5304db9-9b6e-43d3-b860-57528bf284a0)

# Criando o usuário do banco de dados associado ao login

```sql
USE MinhaEmpresa;
CREATE USER Andreia FOR LOGIN Andreia;
```

Vá para o banco de dados MinhaEmpresa → Expanda a segurança → Expanda usuários → O usuário Andreia é criado.

![image](https://github.com/andreiiasalles/BDII--atividade-de-seguranca/assets/57154658/844c2f06-34ee-479c-8a7f-da75ed7c9bcf)

# Conectando ao SQL SERVER

![image](https://github.com/andreiiasalles/BDII--atividade-de-seguranca/assets/57154658/42b01db2-9153-4353-8a77-10b8eca32b88)

