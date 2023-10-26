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

Então nos conectamos ao novo usuário que é Andreia

![image](https://github.com/andreiiasalles/BDII--atividade-de-seguranca/assets/57154658/129183f4-26ea-4568-8b7e-e1378a7f6c2b)

O usuário Andreia não pode acessar a tabela de endereços porque não atribuímos permissão GRANT.

![image](https://github.com/andreiiasalles/BDII--atividade-de-seguranca/assets/57154658/e9451d48-ced9-44b7-8a89-675c2d94ad09)

# Dando permissões com GRANT

Logamos com o perfil Adm e utilizamos o seguinte comando para que o usuário Andreia tenha acesso a tabela pedidos:

```sql
USE MinhaEmpresa
GO 
GRANT SELECT ON [dbo].[Pedidos] TO Andreia;
```

![image](https://github.com/andreiiasalles/BDII--atividade-de-seguranca/assets/57154658/3f41c2e9-e0e2-49e4-90e1-46f6aee21e87)

![image](https://github.com/andreiiasalles/BDII--atividade-de-seguranca/assets/57154658/4eff6606-cd85-46fc-a2ac-15ba34a1be9b)


# Removendo permissão com o REVOKE

Vamos remover a permissão de acessar a tabela Clientes do usuário Andreia:

![image](https://github.com/andreiiasalles/BDII--atividade-de-seguranca/assets/57154658/1d2b8db4-f97b-458a-91b8-bbb37bea5b62)

```sql
USE MinhaEmpresa
GO 
REVOKE SELECT ON [dbo].[Clientes] TO Andreia;
```

![image](https://github.com/andreiiasalles/BDII--atividade-de-seguranca/assets/57154658/ef85e1f5-f9f4-498f-9457-1d1a2700c43b)

# Removendo o login do servidor

```sql
DROP LOGIN [Andreia]
```

Mas pode ocorrer o seguinte erro:

![image](https://github.com/andreiiasalles/BDII--atividade-de-seguranca/assets/57154658/29cfd5c2-9b07-4d38-8c8e-6e97d75925ad)

Caso ocorra, podemos seguir da seguinte forma:

```sql
USE MinhaEmpresa;

SELECT session_id
FROM sys.dm_exec_sessions
WHERE login_name = 'Andreia'
```

![image](https://github.com/andreiiasalles/BDII--atividade-de-seguranca/assets/57154658/fd148fdf-e222-4255-889c-cc19536bfe12)

Depois de obtermos um ID de sessão, mate esse ID de sessão com a ajuda do comando KILL.

```sql
KILL 51
KILL 59
```
 E então você poderá usar o comando DROP LOGIN

 ![image](https://github.com/andreiiasalles/BDII--atividade-de-seguranca/assets/57154658/9f6b0a59-16df-4aaf-8d18-7eee9d5ab737)





Material de referencia: https://vaishaligoilkar3322.medium.com/grant-and-revoke-in-sql-server-62ef393e743




