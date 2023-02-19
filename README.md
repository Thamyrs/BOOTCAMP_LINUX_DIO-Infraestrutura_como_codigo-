# Bootcamp Linux do Zero DIO - IaC

Esta é a primeira atividade do bootcamp de linux da DIO, trabalhando com Infraestrutura Como Código. Um projeto bem simples.

A proposta da atividade era criar um script bash que criasse no ubuntu server:

- 4 repositórios - público, administração, vendas, segurança
- 3 grupos de usuário - grupo adm, grupo vendas, grupo segurança
- 9 usuários e adicioná-los a seus respectivos grupos de usuários

Além disso, também foi necessário através do script alterar permissões de acesso aos diretórios, onde apenas membros do grupo poderiam visualizar, alterar e executar seus repositórios, e terceiros não teriam autorização alguma. Na pasta pública, todos os usuários teriam permissões totais.

## Observações

Embora o comando ``adduser`` seja mais comum de ser usado para criar usuários no linux, em aula foi ensinado a usar o comando ```useradd``` e a definir todos o parâmetros manualmente em um único comando.

Além disso, ao criar os usuários com ```useradd``` usávamos o parâmetro ``-p`` com o ``openssl`` para a criação de senhas. Por padrão do openssl, as senhas são armazenadas com algoritmo de hashing MD5 (ou o parâmetro -1), que é um algoritmo vulnerável a ataques de força bruta e dicionário. Em aula, nos foi instruído a usar o parâmetro ``-crypt`` no comando ``openssl passwd``, por exemplo:
```
useradd joao -m -c "João Silva" -s /bin/bash -p $(openssl passwd -crypt senha123)
```
Esse crypt refere-se a um algoritmo de hashing criado a partir do algortimo criptográfico DES, com algumas modificações. 
Se o MD5 já é ruim, esse aqui é ainda pior. Ele também é um algoritmo fraco e pode ser fácilmente quebrado com ataques de força bruta, e além disso, ele não é eficiente com salt (você pode verificar isso através desse [link](https://asecuritysite.com/openssl/passwds)). 
A maioria das apicações mais modernas, incluindo versões mais recentes do openssl, não funcionam mais com esse algortimo. 

Para "resolver" esse problema, apenas coloquei o parâmetro ``-5`` no comando ``openssl passwd``, referente ao algoritmo de hashing SHA-256, que é considerado seguro por não possuir vulnerabilidades conhecidas. 
Mas aconteceu uma coisa curiosa: inicialmente, ao verificar o arquivo ``/etc/shadow``, as senhas estavam armazenadas com o padrão $ 5 $ do SHA-256. Como eu coloquei o comando ``passwd <nome do usuário> -e``, o usuário era obrigado a atualizar a senha, e quando fazia, a sua senha não era mais armazenada com o SHA-256, e sim com um algoritmo chamado ``Yescrypt``, com padrão $ y $, o mesmo usado por padrão do comando ``adduser``, que teoricamente é seguro. 
