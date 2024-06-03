
# DIO - Python Data Analytics

## Desafio de Projeto II
### Criando um Dashboard corporativo com integração com MySQL e Azure

- Coleta e processamento de dados com Power bi

### Screenshots
![Relatório](https://github.com/FrancaTM/PLACEHOLDER.png)

### Etapas

1. Criado e configurado BD MySQL na Azure
1. Criada estrutura do BD (utilizando **Workbench**) com base no seguinte script:
    https://github.com/julianazanelatto/power_bi_analyst/blob/main/M%C3%B3dulo%203/Desafio%20de%20Projeto/script_bd_company.sql
1. Populado BD (utilizando **Workbench**) com base no seguinte script:
    https://github.com/julianazanelatto/power_bi_analyst/blob/main/M%C3%B3dulo%203/Desafio%20de%20Projeto/insercao_de_dados_e_queries_sql.sql
    **Obs**: Foi necessária a ordenação dos elementos de inserção em "employee" por causa de restrições na tabela
1. Conectado **Power BI** à instância do BD na Azure
1. Transformações de dados realizadas (utilizando **Power Query**):

    5.1. Alterado o nome da tabela departament para **department**

    5.2. Removidas colunas de "table" e "value" em **department** (4 ao todo)
    
    5.3. Alterado tipo de Mgr_ssn em **department** de texto para inteiro

    5.4. Removida coluna de "value" em **dependent** (1 ao todo)

    5.5. Alterado tipo de Essn em **dependent** de texto para inteiro

    5.6. Removida coluna de "value" em **dept_locations** (1 ao todo)

    5.7. Removidas colunas de "table" e "value" em **employee** (6 ao todo)

    5.8. Alterado tipo de Ssn e Super_ssn em **employee** de texto para inteiro

    5.9. Alterado tipo de Salary em **employee** de decimal para decimal fixo

    5.10. Removidas colunas de "table" e "value" em **project** (2 ao todo)

    5.11. Removidas colunas de "value" em **works_on** (2 ao todo)

    5.12. Alterado tipo de Essn em **works_on** de texto para inteiro

    5.13. Dividida coluna complexa "Address" (tabela **employee**) em "AddressNo", "AddressDistrict" e "AddressCity"

1. Verificada a existência de um único **nulo** (em Super_ssn) em **employee**, ou seja, apenas um employee não possui gerente

1. Verificado que não existe departamento sem gerente

1. Verificado que o total de horas de projetos é igual a 275 horas

1. Verificado que existe apenas 1 projeto com uma quantidade de horas igual a 0

1. Criada uma nova consulta (**employee_department**) através da mesclagem de **employee** e **department**
    
    **Obs**: Foi aplicada uma operação de mesclagem para garantir que apenas seriam criadas entradas na nova consulta com base na correspondência (operação de junção) de valores da segunda tabela em relação à primeira

1. Removida coluna "Dnumber" (coluna redundante com Dno) após a mesclagem

1. Criada uma nova consulta (**employee_manager**) através da mesclagem de **employee** com **employee** para identificação dos seus respectivos gerentes
    
    **Obs**: Foi utilizada a operação de mesclagem no Power BI

1. Removidas colunas desnecessárias do resultado (8 ao todo) após a mesclagem (**employee_manager**)

1. Mescladas colunas (3 ao todo) para formar "EmployeeName" em **employee_manager**

1. Mescladas colunas (3 ao todo) para formar "MgrName" em **employee_manager**

1. Criada uma nova consulta (**deptname_location**) através da mesclagem de **department** e **dept_locations**
    
    **Obs**: Foi aplicada uma operação de mesclagem para garantir que apenas seriam criadas entradas na nova consulta com base na correspondência (operação de junção) de valores da segunda tabela em relação à primeira

1. Removidas colunas desnecessárias do resultado (4 ao todo) após a mesclagem (**deptname_location**)

1. Adicionada nova coluna "DnameLocation" pela duplicação e mesclagem das colunas "Dname" e "Dlocation" em **deptname_location**

1. Criada uma nova consulta (**manager_employee**) através da mesclagem de **employee** com **employee** para identificação dos gerentes e seus respectivos colaboradores

1. Removidas colunas desnecessárias do resultado (6 ao todo) após a mesclagem (**manager_employee**)

1. Agrupados dados por "Fname", "Minit" e "Lname" em **manager_employee** para contagem de quantidade de colaboradores por gerente