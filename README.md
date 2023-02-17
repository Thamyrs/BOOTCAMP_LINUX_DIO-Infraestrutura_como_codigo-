# Bootcamp Linux do Zero DIO - IaC

Esta é a primeira atividade do bootcamp de linux da DIO, trabalhando com Infraestrutura Como Código. Um projeto bem simples.

A proposta da atividade era criar um script bash que criasse no ubuntu server:

- 4 repositórios - público, administração, vendas, segurança
- 3 grupos de usuário - grupo adm, grupo vendas, grupo segurança
- 9 usuários e adicioná-los a seus respectivos grupos de usuários

> Em aula, foi instruído a usar o parâmetro -crypt no comando openssl passwd, referente ao algoritmo de hashing. No entanto, ele é um algoritmo fraco e vulnerável a ataques de dicionário e força bruta, e inclusive foi removido de versões mais recentes da openssl. Por default, ele usa agora o MD5 (padrão $1$), mas que infelizmente também é um algoritmo de hashing com várias vulnerabilidades conhecidas. **Usei o parâmetro -5 para atribuir o SHA-256 como função de hashing da senha, que é considerado seguro.**

Além disso, também foi necessário através do script alterar permissões de acesso aos diretórios, onde apenas membros do grupo poderiam visualizar, alterar e executar seus repositórios, e terceiros não teriam autorização alguma. Na pasta pública, todos os usuários teriam permissões totais.

