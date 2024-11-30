# Dashboard No Metabase: Análise Da Aquisição De Clientes 📊🔍
![Alt ou título da imagem](https://github.com/Philippeizidorio/Analiseclientes_Edtech/assets/145637595/f7210ed3-a01e-4221-900a-4dc36a6b22d9)

### ◾Contexto: 

Uma Edtech está focada em acelerar seu crescimento aumentando o número de usuários cadastrados. Para isso, foi solicitado a criação de um dashboard que permitirá a equipe de
negócios desenvolver um plano de ação que será utilizado para auxiliar no estabelecimento das estratégias da empresa para o próximo ano.

### ◾Análise Exploratória De Dados(AED): 

Dentro da própria plataforma de BI, neste caso o Metabase, foi feita uma análise exploratória entre 5 bases de um banco ***Mysql*** a fim de entendermos os dados e extrairmos insights levando em consideração os vários aspectos da aquisição de novos clientes no momento atual da empresa.
- **a.Base 1** = leads_basic_details → _[Informações Básicas Dos Clientes]_
- **b.Base 2** = sales_managers_assigned_leads_details → _[Info. De Possíveis Leads atribuídos aos Ger. De Vendas]_
- **c.Base 3** = leads_interaction_details → _[Informações sobre a interação do cliente com o negócio]_
- **d.Base 4** = leads_demo_watched_details → _[Informações sobre clientes que aceitaram a demonstração]_
- **e.Base 5** = leads_reasons_for_no_interest → _[Motivos de não interesse por parte do Lead]_

### ◾Extract,Transform, And Load(ETL): 

Não foram necessárias correções de erros nos dados, apenas realizamos manipulações para filtrarmos e organizarmos os dados da forma que precisamos com o objetivo de construir os gráficos que serão imputados no Dashboard de acordo com o requisito de negócio e  de dados logo explícitos neste projeto. 

### ◾Requisitos de dados: 

- **Quantidade de pessoas pelo gênero;**  
- **Média de idade dos leads;**
- **Quantidade de pessoas por tipo de graduação;**
- **Média do percentual das aulas de demonstração assistidas por idioma;_[Acima de 0.5]_**
- **Quantidade de usuários atendidos por plataforma ao longo do tempo.**

### ◾Criação Do Dashboard:

Para criação desse dashboard, apliquei as seguintes manipulações e tipos de gráficos no Metabase ↓
 
***1.Gráfico tipo Pizza;***_(Distribuição de gênero)_

- **CÓDIGO →** _Select COUNT(*) as quantidade, gender as genero
              From leads_basic_details
              Group by genero_

***2.Gráfico tipo Cartão;***_(Média de idade)_

- **CÓDIGO →** _Select CAST(AVG(age) as unsigned)
              From leads_basic_details_

***3. Gráfico tipo Barras;***_(Clientes Por G.D.E.)_

- **CÓDIGO →** _Select COUNT(*) as quantidade, current_education as Grau_de_escolaridade
                From leads_basic_details
                Group By Grau_de_escolaridade
                Order By quantidade ASC_

***4. Gráfico tipo Tabela;***_(Médias Watched)_

- **CÓDIGO →** _Select AVG(watched_percentage) as media, language as lingua
               From leads_demo_watched_details
               Where watched_percentage > 0.5
               Group By lingua
               Order by media DESC_

***5. Gráfico tipo Linhas.***_(Quant.Chd.P.P)_

- **CÓDIGO →** _Select COUNT(*), call_done_date as data, lead_gen_source as fonte, call_status as situacao
                From leads_interaction_details
                Left join leads_basic_details on leads_basic_details.lead_id =  leads_interaction_details.lead_id
                Where call_status = 'successful'
                Group by data,fonte_

Você pode visualizar o resultado do Dashboard [**CLICANDO AQUI!**](https://github.com/Philippeizidorio/Analiseclientes_Edtech/blob/main/Dashboard%20-%20Edtech.pdf) [Arquivo em .pdf deste repositório] 

### ◾ Através desse Dashboard, podemos extrair os seguintes insights:
1. Os clientes desta Edtech tendem em sua maior quantidade ser do gênero feminino;
2. A grande parte dos leads está interessada em recolocar-se no mercado de trabalho _[Looking for a job]_ ou apresentam graduação tecnológica _[B.Tech]_;
3. As top plataformas em que ocorre a maior parte dos atendimentos são: 1-Social media, 2-SEO, 3- Email Marketing;
4. Os leads que apresentam maior interesse e média de tempo assistido nas aulas de demonstração são aqueles que tem como idioma de preferência o Inglês ou Telegu;
5. A média de idade do público-alvo é de 22 anos;
6. **[PLUS+]** Através da análise exploratória inicial dos dados, foi identificado como principal motivo de desistência no fechamento de matrículas o preço atual da formação - _'Can't Afford Reason'_.

### ◾ Tecnologias Utilizadas: 
<div <br> 
<img src="https://img.shields.io/badge/Microsoft_Excel-217346?style=for-the-badge&logo=microsoft-excel&logoColor=white">
<img src="https://img.shields.io/badge/MySQL-005C84?style=for-the-badge&logo=mysql&logoColor=white">
<img src="https://img.shields.io/badge/Metabase-509EE3?style=for-the-badge&logo=metabase&logoColor=fff">
</div> 

## Autor:

<img  src="https://github.com/Philippeizidorio/AnaliseTRIM_AgenciaMKTDIGITAL/assets/145637595/9800ac43-2070-48d4-9002-dbf82f756f2c" width="80" alt="cognitiveclass.ai logo" align="left" /> 

### &nbsp;&nbsp;Philippe Izidório

<p>
&nbsp;&nbsp;Estudante De Ciência De Dados / Business Intelligence / Analista De Dados<br/>
&nbsp;&nbsp;LinkedIn: https://www.linkedin.com/in/philippeizidorio/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;E-mail: euphilippeizidorio@gmail.com<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Portifólio de projetos em Data Science: https://github.com/Philippeizidorio
</p>
