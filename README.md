# Bootcamp Linux do Zero DIO - IaC

Está é a primeira atividade do bootcamp de linux da DIO, trabalhando com Infraestrutura Como Código. Um projeto bem simples.

A proposta da atividade era criar um script bash que criasse no ubuntu server:

- 4 repositórios - público, administração, vendas, segurança
- 3 grupos de usuário - grupo adm, grupo vendas, grupo segurança
- 9 usuários e adicioná-los a seus respectivos grupos de usuários
> foi usado o comando openssl passwd para criar o hash da senha do usuário. Dependendo das configurações do servidor, pode ser necessário o uso de parâmetros como -crypt.

Além disso, também foi necessário através do script alterar permissões de acesso aos diretórios, onde apenas membros do grupo poderiam visualizar, alterar e executar seus repositórios, e terceiros não teriam autorização alguma. Na pasta pública, todos os usuários teriam permissões totais.

