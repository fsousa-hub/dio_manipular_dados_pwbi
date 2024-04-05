<h1>
    <a href="https://www.dio.me/">
     <img align="center" width="40px" src="https://hermes.digitalinnovation.one/assets/diome/logo-minimized.png"></a>
    <span> Desafio de Projeto - DIO</span>
</h1>

Neste desafio foi aplicado as etapas de coleta, obtenção e transformação de dados com Power BI e MySQL na Azure. O projeto é referente ao desafio de projeto **Processando e Transformando Dados com Power BI** do módulo **Visualização e Análise de Dados com Power BI** do Curso Python Data Analytics - **Bootcamp Coding The Future Squadio - Python Data Analytics 2024** da [Digital Innovation One](https://www.dio.me/).

---

<br>


**Etapas do Projeto:**

- *Criação de uma instância na Azure para MySQL.*
- *Criar o Banco de dados com base disponível no github.*
- *Integração do Power BI com MySQL no Azure.*
- *Verificar problemas na base a fim de realizar a transformação dos dados.*

<br>

**Durante este processo preciso realizar o próximo passo a passo e encontrei alguns problemas ao longo do caminho:**

- *Ao analisar Employee temos apenas um registro com o Super_ssn null, percebemos que ele possui o Dno de valor 1 que possui o nome de HeadQuarters. Ou seja, provavelmente ele é o dono da companhia e não possui nenhum superior a ele.*
- *Não há departamentos sem gerentes.*
- *Diferentes funcionários de departamentos gastam horas diferentes para o mesmo projeto.*
- *Ao separar a coluna Address de Employee vi que um registro possui um nome composto chamado Fire-Oak, isso estava dando problema na hora de separar pelo limitador -, tratei o dado transformando Fire-Oak em FireOak e depois separando os dados de endereço.*
- *Consulte o SQL que utiliza para juntar colaboradores com seus gerentes:*

```sql
WITH manager AS(
	SELECT e.Fname,e.Lname, e.Ssn FROM employee e
    JOIN departament d ON e.Dno = d.Dnumber
    WHERE e.Ssn = d.Mgr_ssn
) 
SELECT CONCAT(m.Fname," ",m.Lname) AS manager_name, e.* FROM employee e
LEFT JOIN manager m ON e.Super_ssn = m.Ssn OR e.Super_ssn IS NULL
WHERE e.Super_ssn IS NOT NULL OR m.Fname = "James";
```
- *Ao mesclar departamento com localização temos o departamento Research em 3 locais diferentes porém com o mesmo ID o que causou duplicatas nos dados, portanto preferi nesse momento não fazer a mesclagem com localização e apenas deixar o departamento por funcionar.*

<br>

**Pasta: Query SQL**

Arquivo *.sql   | 
--------- | 
script_bd_company.sql |
insercao_de_dados_e_queries_sql.sql | 


<br>

**Pasta: Coleta e Extração de Dados**

Arquivo *.pbix   | 
--------- | 
extract_database_azure_direct_query.pbix |
integration_example_mysql_sakila.pbix | 
report_sample_mysql.pbix | 


<br>

**Pasta: Limpeza e Transformação de Dados**

Arquivo *.pbix   | 
--------- | 
limpeza_dados_primeiro_exemplo.pbix | 
limpeza_dados_segundo_exemplo.pbix | 
limpeza_dados_terceiro_exemplo.pbix | 
limpeza_dados_mescla_tabelas.pbix | 
limpeza_dados_combinação_de_tabelas.pbix | 


<br>

**Pasta: Imagem**

Arquivo *.png   | 
--------- | 
relatorio-mysql-pwbi | 

<br>

## Links Úteis:


### Microsoft Azure

<br>

>Criação de uma instância na Azure para MySQL.
>Acesso ao site **Azure**, _Testar o Azure Gratuitamente_ em <https://azure.microsoft.com/pt-br> por 30 dias.

### Repositório GitHub com Query SQL

<br>

>Criar o Banco de dados com base disponível no github.
>Acesso ao repositório **Azure**, _Testar o Azure Gratuitamente_ em <https://azure.microsoft.com/pt-br> por 30 dias.

### Power BI

<br>

>Integração do Power BI com MySQL no Azure.
>Acesso ao site **Microsoft Power BI**, _Experimente o Power BI como parte de uma conta gratuita do Microsoft Fabric._ em <https://app.powerbi.com/>

<br>
