## README

## Projeto de software Klassic da empresa 2ST.




### Guideline

Este passo a passo referece a integração do novo colaborador afim do mesmo conseguir instalar o ambiente de desenvolvimento que a empresa adota e posteriormente conseguir colocar em prática este documento de Gerenciamento de Configuração de Software, que trás todos requisitos e passos necessários para compreensão e fluidez do processo de desenvolvimento.

##### Ambiente de desenvolvimento

•	Dependências
Ubuntu 16.04 LTS

##### Instalação do Git

•	Atualize seu OS:
```sh
sudo apt update
```

•	Comando para instalar o Git
```sh
sudo apt-get install git
```

##### Clonar repositório do software Klassic
Git Clone:
```sh
git clone 
```

##### Acesse o diretório clonado:
```sh
cd klassic
```
##### Acesse a branch de desenvolvimento desejada, ex:
```sh
git checkout 1.0.0
```

##### Instalando Java
Insira os repositórios do Java.
•	Atualize o OS.
```sh
sudo apt-get update
sudo apt-get install python-software-properties
sudo add-apt-repository ppa:webupd8t
```
•	Insira os comandos no terminal para instalar a máquina Java
```sh
sudo apt-get install oracle-java8-installer
```
##### Instalando Maven
Instale o Maven:
```sh
sudo apt-get install maven
```
•	Instale as dependências do projeto através do Maven:
```sh
mvn dependency:go-offline
mvn install
```

##### Instalando SGBD e configurando Banco de Dados

Instale o SGBD PostgreSql:
```sh
sudo apt-get install postgresql postgresql-contrib
```

##### Cria a database:
```sh
sudo psql -U postgres -c ’CREATE DATABASE klassic;
```

##### Inicialize o banco:
```sh
sudo psql -U postgres -d aula -a -f Scripts/Database.txt
```

Obs: Certifique-se que dentro do arquivo src/main/resources/META-INF/persistence.xml as propriedades jdbc.user e jdbc.password estejam corretas de acordo com o seu banco de dados.


### Baseline

Como mencionado anteriormente a branch principal de cada produto de software terá como rótulo ”master”, esta é a baseline padrão onde manterão controle de versões seguindo as nomenclaturas adotadas.
Em caso de branch gerada ao cliente, esta apresentará a nomenclatura padrão acrescida de uma quarta casa decimal para controle de customização, assim, esta branch continua sendo monitorada pela versão ”master”podendo receber suas atualizações, e é possível controlar as versão de customização do cliente especifico.

### Nomenclatura de versões

Será utilizado da seguinte forma:
* [Version]: Utilizado para informar qual versão encontra se o produto.
* [Function]: Alterado apenas quando novas funcionalidades são incorporadas no produto.
* [Bugs]: Alterado quando uma corração faz necessário
* [Customize]: Alterado sempre que uma customização especifica de uma cliente é feita. Utilizada apenas em branch de clientes e não na ”master”. Exemplo: master 1.1.1 ou cliente A 1.4.10.3


### Padrão de Commit

Os ”commit”devem seguir um padrão afim de tornar mais fácil a compreensão e integração por parte de novos colaboradores, deixando claro e resumido a alteração aplicada.

* [Nova Distribuição]: Deve ser iniciado com a palavra ”Nova Distribuição ”seguindo de um espaço e depois ""-”, mais um espaço e o resumo objetivo da ação executada, neste caso o nome da nova distribuição e o cliente. Exemplo: ”Nova Distribuição - sistema de carros cliente Volvo”.
* [Correções | Bugs]: Deve ser iniciado com a palavra "Correção" seguindo de um espaço e depois "-", mais um espaço e o resumo objetivo da ação executada, neste caso o que foi corrigido. Exemplo: "Correção - Mascara do campo CEP "
* [Nova Funcionalidade]: Deve ser iniciado com a palavra "Nova Funcionalidade" seguindo de um espaço e depois "-", mais um espaço e o resumo objetivo da ação executada, neste caso o que seria a nova funcionalidade. Exemplo: "Nova Funcionalidade - Valida CPF"
* [Nova Versão]: Deve ser iniciado com a palavra "Nova Versão" seguindo de um espaço e depois "-", mais um espaço e o número da nova versão respeitando a nomenclatura. Exemplo: "Nova Versão - 2.0.0"
