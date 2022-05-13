/*relatorio_1*/
select numero_departamento, AVG(salario) from funcionario group by numero_departamento  ;

/*relatorio_2*/
(select sexo, AVG(salario) from funcionario where sexo='M') UNION (select sexo, AVG(salario) from funcionario where sexo='F')  ;


/*relatorio 3*/
select nome_departamento, concat(primeiro_nome, nome_meio, ultimo_nome) as nome, data_nascimento, (select date_format(from_days(DATEDIFF(now(), data_nascimento)), '%Y')+0 AS age)as idade, salario from funcionario f, departamento d where f.numero_departamento = d.numero_departamento;


/*relatorio 5*/ 
select nome_departamento, concat (f.primeiro_nome,f.nome_meio, f.ultimo_nome)as nome_funcionario, concat (g.primeiro_nome, g.nome_meio, g.ultimo_nome) as nome_gerente, f.salario from funcionario f, funcionario g,departamento where cpf_gerente = g.cpf and f.numero_departamento = departamento.numero_departamento order by nome_departamento ASC, f.salario DESC ;

/*relatorio 8*/ 
select nome_departamento,nome_projeto,concat(primeiro_nome, nome_meio, ultimo_nome)as nome_funcionario, horas from funcionario f,departamento d,projeto p,trabalha_em t where t.cpf_funcionario=f.cpf and t.numero_projeto=p.numero_projeto and p.numero_departamento=d.numero_departamento;

 /*relatorio 9*/ 
select  nome_projeto, nome_departamento,SUM(horas) from trabalha_em t,projeto p,departamento d where d.numero_departamento=p.numero_departamento and p.numero_projeto=t.numero_projeto group by nome_departamento,nome_projeto;
 
 /*relatorio 10*/
 select nome_departamento, avg(salario) from funcionario f,departamento d where f.numero_departamento=d.numero_departamento group by nome_departamento;
  
 
  /*relatorio 14*/ select nome_departamento, COUNT(cpf) from funcionario f,departamento d where f.numero_departamento=d.numero_departamento group by nome_departamento;
  
  /*relatorio 15*/ select concat(f.primeiro_nome,f.nome_meio,f.ultimo_nome) as nome_funcionario, nome_departamento, nome_projeto from funcionario f,departamento d,projeto p where f.numero_departamento=d.numero_departamento and d.numero_departamento=p.numero_departamento group by nome_funcionario;
