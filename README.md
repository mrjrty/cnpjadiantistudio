
## Requistos
* PHP 7.2 ou superior. Configura o PHP conforme orientações do [Adianti FrameWork 7.3.0](https://www.adianti.com.br/framework-quickstart)
* Python 3.6 ou superior
* Aproximadamente 200 GB de espaço livre em disco para a instalação:
    * 6 GB arquivos zip da Receita Federal. Pode ser liberado depois
    * 85 GB para arquivos texto descompactados. Pode ser liberado depois.
    * 85 GB para banco de dados SqLite.

## Intalação separada

### Parte 1 - PHP
1. Ter um servidor PHP 7.2 ou superior. Configura o PHP conforme orientações do [Adianti FrameWork 7.3.0](https://www.adianti.com.br/framework-quickstart)
1. Copie o conteudo da pasta `www` do projeto para o seu servidor PHP.
1. Verifique se tudo dentro de `<caminho servidor>/cnjrfb/app/CNPJ-full` tem permissão de execução do servidor web. Se for Linux (Debian/Ubuntu) com Apache pode executar `sudo chown -R www-data:www-data`
1. Abra o sistema em um navegador e verifique se os 3 menus dentro HOME está funcionando: Empresa, Sócios e CNEA. 

**ATENÇÃO!! a função de gerar grafo depende da parte 2 em Python para funcionar**. Nesse momento você está usando um mini banco de dados de exemplo com apenas 56 KB para mostrar que tudo está funcionando. A versão final do banco de dados tem mais de 6GB e depende da parte 3 para funcionar.

### Parte 2 - Python 
Na primeira parte foi a instalação dos elementos básicos sem banco de dados completo.

1. Requisito: PHP, Python e Disco
1. Copie o projeto [CNPJ-FULL](https://github.com/fabioserpa/CNPJ-full) e coloque na pasta `<caminho servidor>/cnjrfb/app/CNPJ-full`
    1. [Instale o PIP conforme orientação](https://github.com/fabioserpa/CNPJ-full#gerenciador-de-pacotes-do-python-pip)
    1. Instale os requisitos `pip install -r requirements.txt` USE o arquivo [requirements.txt aqui no projeto](https://github.com/bjverde/cnpjrfb/blob/master/requirements.txt)
1. Abra o sistema em um navegador. Menu > Facilitadores >  Gera Grafo , sugestão é o CNPJ 00.000.000/0001-91

### Parte 3 - O banco completo !
É algo demorado mesmo! Pois irá baixar 6 GB de dados da Receita Federal e depois criar o banco de dados completo.

Baixar todos dados [Dados públicos CNPJ](https://receita.economia.gov.br/orientacao/tributaria/cadastros/cadastro-nacional-de-pessoas-juridicas-cnpj/dados-publicos-cnpj) na pasta `<caminho servidor>/cnjrfb/app/CNPJ-full/downloads`


## Intalação via Docker-compose
Existem alguns arquivos em Docker-compose para criar todo o ambiente necessários para rodar tudo que é necessário. A ideia é com um comando o usuário consiga ter tudo funcionando sem muito esforço.

1. Instale o Docker e Docker-compose 
1. clone o projeto
1. Abriu um terminal na raiz do projeto
1. Execute o comando `docker-compose build` para gerar todo o ambiente.
1. Execute o comando `docker-compose -f docker-compose.yml up -d` para rodar o ambiente já configurado. O Docker pretender resolver apenas [Parte 1 - PHP](#parte-1---php) e a [Parte 2 - Python](#parte-2---python).
1. Verificando se a instalação está correta: Abra o sistema em um navegador e verifique se os 3 menus dentre home está funcionando: Empresa, Sócios e CNEA.
1. Verificando se a instalação está correta: Abra o sistema em um navegador. Menu > Facilitadores >  Gera Grafo , sugestão é o CNPJ 00.000.000/0001-91
1. Executar o procedimento da [Parte 3 - O banco completo](#parte-3---o-banco-completo-) por ser algo muito demorado deve ser feito manualmente.
# cnpjadiantistudio
