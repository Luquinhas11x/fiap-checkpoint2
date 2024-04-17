# Checkpoint 2

Aplicação Java com container e Banco de Dados para segunda avaliação do 3ºSIT


## Pré-requisitos

- Java 17+
- Docker
- Apache Maven
- Acesso a internet
- Acesso ao Docker Hub

## Instalação

#### Dependências
- Spring Data JPA (SQL)
- Thymeleaf (TEMPLATE ENGINES)
- Spring Web (WEB)
- Spring Boot DevTools (DEVELOPER TOOLS)
- H2 Database (SQL)
- Oracle Driver (SQL)
- MySQL Driver (SQL)

#### Clone

#### Instalação

```
git clone https://github.com/Luquinhas11x/fiap-checkpoint2.git
```

## Execução

### Maven
* Limpar o diretório de saída do projeto Maven

```
mvn clean
```

* Compilar o projeto Maven

```
mvn package
```

#### Docker
* Criar nova imagem Docker

```
docker build -t fiap-checkpoint2
```

* Executar container

spring.profiles.active=${PROFILE}

```
docker run -d -p 8080:8080 -e PROFILE=<prd|dev|stg> fiap-checkpoint2
```

## Container Registry


#### Docker Hub

* Login

```
docker login
```

* Criar imagem pronta para upload (método 1 - criando nova imagem)

```
docker build -t ludushark/fiap-checkpoint2 .
```

* Upload de imagem para o Docker Hub

```
docker push ludushark/fiap-checkpoint2
```

## Navegação
#### Base

- http://localhost:8080

#### H2 Database

- Endpoint para acessar o banco de dados através do H2 Database: http://localhost:8080/h2-console

- No campo da url incluir
```
jdbc:h2:mem:testdb
```
- No campo do username incluir
```
sa
```
- No campo da password incluir
```
password
```

#### Comandos SQL utilizados como exemplo

- Manipulando a tabela de PACIENTES 
```
INSERT INTO pacientes (nome, endereco, bairro, email, telefone_completo, data_nascimento, created_at, updated_at)
VALUES ('Pedro Silva', 'Rua das Rosas, 456', 'Interior', 'pedro@example.com', '1234-5678', '2003-07-20', CURRENT_TIMESTAMP, CURRENT_TIMESTAMP);
```
```
INSERT INTO pacientes (nome, endereco, bairro, email, telefone_completo, data_nascimento, created_at, updated_at)
VALUES ('Lucas Santana', 'Rua das Flores, 123', 'Centro', 'lucas@example.com', '94175-2012', '2004-10-11', CURRENT_TIMESTAMP, CURRENT_TIMESTAMP);
```
```
select * from pacientes;
```
- Manipulando a tabela de PROFISSIONAIS
```
INSERT INTO profissionais (nome, especialidade, valor_hora, created_at, updated_at)
VALUES ('Dr Henrique', 'Infectologista', 150.00, CURRENT_TIMESTAMP, CURRENT_TIMESTAMP);
```
```
INSERT INTO profissionais (nome, especialidade, valor_hora, created_at, updated_at)
VALUES ('Dr Cesar', 'Ortopedista', 100.00, CURRENT_TIMESTAMP, CURRENT_TIMESTAMP);
```
```
select * from profissionais;
```
- Manipulando a tabela de CONSULTAS
```
INSERT INTO consultas (data_consulta, status_consulta, quantidade_horas, valor_consulta, profissional_id, paciente_id)
VALUES ('2024-04-21 11:00:00', 'AGENDADA', 2, 300.00, 1, 1);
```
```
select * from consultas;
```
```
SELECT
c.data_consulta,
c.status_consulta,
c.quantidade_horas,
c.valor_consulta,
p.nome AS nome_profissional,
pc.nome AS nome_paciente
FROM
consultas c
INNER JOIN
profissionais p ON c.profissional_id = p.id
INNER JOIN
pacientes pc ON c.paciente_id = pc.id;
```

## Features (Funcionalidades)

- Múltiplos profiles
- Banco de dados

## Contatos

- Lucas Santana de Paula - lukinha11x@gmail.com

## Referencias

- [GitHub com as intruções](https://github.com/acnaweb/microservices-2024/blob/main/checkpoints/checkpoint-2-sem1.pdf)
- [Docker Hub com o repositório](https://hub.docker.com/r/ludushark/fiap-checkpoint2/tags)


