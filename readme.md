# Orientações para execução de testes de Back-end
Os testes de back-end sempre serão desenvolvidos sobre a plataforma do Postman.
Abaixo estarão descritas as orientações para download, instalação e preparação do ambiente.

## Preparação do ambiente
Será necessário a instalação das ferramentas abaixo:
* **[Postman]**(https://www.getpostman.com/postman) para desktop para criação dos testes.
* **[Nodejs]**(https://nodejs.org/en/download/) para gestão de pacotes para diversos recursos de javascript.

Após a instalação do Nodejs, deve ser instalado o pacote abaixo, para simular a execução dos testes via linha de comando:

```
 npm install newman --global
```

## Enviroments
As configurações de ambiente como chaves de acesso, parâmetros de diretórios e path de urls, são definidas em arquivos de ambiente. Eles estão definidos no diretório:

```
 env/
```

Em toda a execução, deverá ser informado junto do cenário de teste, o json de ambiente.

## Execução dos cenários de testes
Para execução dos cenários de testes, inicialmente devem ser obtidos os ambientes e cenários de testes diretamente do repositório.

```
 git clone https://github.com/Phelps18/simulador-investimento-backend.git
```

Após a cópia dos cenários de testes, deve ser definido a execução através do **Postman** ou **Newman**, descritos na seção posterior.

### Execução através do Postman
Inicialmente deve ser carregado o arquivo de **ambiente**.

1. Abrir o **Postman**;
1. Localizar a **engrenagem** no alto a direita, ao lado da caixa de seleção de ambiente e clicar em **Manage Enviroments**;
1. Clicar no botão **Import**;
1. Selecionar o arquivo **json** de ambiente no diretório **env** obtido através do repositório de testes;

Após a carga do arquivo de ambiente, deve ser carregada a **collection** através dos passos abaixo:

1. Com o **Postman** aberto;
1. Acessar a opção **File / Import**;
1. Escolher o **json** da collection a ser testada.
```
 /tests/mock-server-investment.json
```

Com o **ambiente** e a **coleção** carregadas, para executar, basta seguir os passos abaixo:

1. Acessar menu **Collection / Runner**;
1. Selecionar a **collection** na caixa de seleção;
1. Definir o ambiente em **Enviroment**;
2. Carregado um arquivo csv na opção **Data** 
1. Clicar no botão **Run**;

### Execução através do Newman
A execução através do Newman é mais simples, bastando apenas indicar os arquivos de ambiente e collection como parâmetros. Abaixo um exemplo de execução.
 
```
newman run tests\mock-server-investment.json --environment env\mock-server-investment-env.json -d datapool\SimularInvestimento.csv --reporters cli,html --reporter-html-template templates\newman-report-customized.hbs  --reporter-html-export reports\collection-name-report.html
```

**Nota**: atentar para a orientação das barras para execução em ambiente linux.
