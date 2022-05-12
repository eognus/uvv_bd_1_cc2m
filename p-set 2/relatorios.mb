create table relatorio_1( salario decimal(10, 2), numero_departamento integer);
insert into relatorio_1(numero_departamento, salario) select numero_departamento, AVG(salario) from funcionario group by numero_departamento  ;
select * from relatorio_1;

create table relatorio_2( sexo char(1), salario decimal(10, 2));
insert into relatorio_2(sexo, salario) ((select sexo, AVG(salario) from funcionario where sexo='M') UNION (select sexo, AVG(salario) from funcionario where sexo='F'))  ;
select * from relatorio_2;

create table relatorio_3 (
                                      -> nome_departamento varchar(15),
                                      -> cpf char(11),
                                      -> nome varchar(30),
                                      -> data_nascimento date,
                                      -> idade integer,
                                      -> salario decimal (10, 2)
                                      -> );
insert into relatorio_3 (select all nome_departamento, primeiro_nome + nome_meio + ultimo_nome, data_nascimento,NULL , salario from funcionario,departamento where funcionario.numero_departamento = departamento.numero_departamento group by nome_departamento);
