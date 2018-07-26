---
layout: post
title:  "Gerando dados de teste com Faker"
date:   2018-07-25 15:05:13 -0300
categories: faker test
---

Faker é uma biblioteca utilizada para gerar dados aleatórios, como nomes, endereços e números de telefone.

Esses dados podem ser usados em várias situações durante o desenvolvimento de um produto, desde a implementação de um teste ou uma carga aleatória na base de dados.

Imagine uma situação onde você queira visualizar o comportamento do seu produto com 1000 clientes cadastrados, com Faker isso fica bem simples.

Você pode acompanhar mais detalhes do projeto na página [https://github.com/stympy/faker](https://github.com/stympy/faker){:target='_blank'}.

### Utilizando o Faker

Instalação

```bash
gem install faker
```

Gerando dados de exemplo

```ruby
require 'faker'

Faker::Name.name      #=> "Christophe Bartell"

Faker::Internet.email #=> "kirsten.greenholt@corkeryfisher.info"
```

### Cadastrando 1000 clientes na base de dados

Agora vamos supor que o Model que representa os seus clientes é a classe `User` com os atributos `name` e `email`.

Caso você queira cadastrar 1000 clientes na base de dados com nomes e emails aleatórios, basta utilizar o Faker.

```ruby
require 'Faker'

1000.times do
  User.create(
      name: Faker::Name.unique.name,
      email: Faker::Internet.unique.email
  )
end
```

Importante adicionar `unique` para garantir que o Fake retorne dados únicos para cada execução.
