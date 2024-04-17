INSERT INTO pacientes (nome, endereco, bairro, email, telefone_completo, data_nascimento, created_at, updated_at)
VALUES ('Pedro Silva', 'Rua das Rosas, 456', 'Interior', 'pedro@example.com', '1234-5678', '2003-07-20', CURRENT_TIMESTAMP, CURRENT_TIMESTAMP);

INSERT INTO pacientes (nome, endereco, bairro, email, telefone_completo, data_nascimento, created_at, updated_at)
VALUES ('Lucas Santana', 'Rua das Flores, 123', 'Centro', 'lucas@example.com', '94175-2012', '2004-10-11', CURRENT_TIMESTAMP, CURRENT_TIMESTAMP);

select * from pacientes;

INSERT INTO profissionais (nome, especialidade, valor_hora, created_at, updated_at)
VALUES ('Dr Henrique', 'Infectologista', 150.00, CURRENT_TIMESTAMP, CURRENT_TIMESTAMP);

INSERT INTO profissionais (nome, especialidade, valor_hora, created_at, updated_at)
VALUES ('Dr Cesar', 'Ortopedista', 100.00, CURRENT_TIMESTAMP, CURRENT_TIMESTAMP);

select * from profissionais;

INSERT INTO consultas (data_consulta, status_consulta, quantidade_horas, valor_consulta, profissional_id, paciente_id)
VALUES ('2024-04-21 11:00:00', 'AGENDADA', 2, 300.00, 1, 1);

select * from consultas;

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