![logo_sql_docker.png](img/logo_sql_docker.png)

# Executando o SQL Server em um Container Docker
Este tutorial tem por objetivo demonstrar a instalação e uso do SQL Server a partir de containers Docker, uma prática que pode ser bastante útil na montagem de ambientes para desenvolvimento em .NET (ou até mesmo outras plataformas). 

### Para implementar o ambiente apresentado neste tutorial foram utilizados como recursos:  
#### [Docker for Windows](https://www.docker.com/docker-windows/)
#### Windows PowerShell.  

### Documentações consultadas:  

#### [Executar imagens de contêiner do SQL Server Linux com o Docker](https://hub.docker.com/_/microsoft-mssql-server)
#### [Microsoft SQL Server](https://hub.docker.com/_/microsoft-mssql-server)

## Passo 1: Baixando Docker  Windows.

O [Docker for Windows](https://www.docker.com/docker-windows/), que permitirá a criação de imagens e containers para testes em máquinas de desenvolvimento baseadas no Windows

![docker_for_windows.png](img/docker_for_windows.png)

Exemplo de arquivo de instalação: “Docker_Desktop_Installer.exe”

## Passo 2: Criação de um container baseado na imagem do SQL Server.

Abra um terminal de comandos e digite os comandos abaixo:

|docker run --name sqlserver2022 -e 'ACCEPT_EULA=Y' -e 'SA_PASSWORD=8F*J@9'  -e 'TZ=America/Sao_Paulo' -p 1433:1433 -v C:\bkp_sqlserver\:/var/bkp_sqlserver/ -d mcr.microsoft.com/mssql/server:2022-latest| 
| :--- | 

![docker_run.png](img/docker_run.png)

 
| Variáveis                  |                                                                                                         |
| :---                       | :---                                                                                                    |
| docker run                 | Cria e executa o container Docker.                                                                      |
| --name=sqlserver2022           | Especifica o nome do container a ser gerado.                                                            |
| -e 'ACCEPT_EULA=Y'         | Aceita os termos de licença da Microsoft.                                                               |
| -e 'SA_PASSWORD=qj8F*J@9'  | Foi indicada a senha do administrador usuário SA.                                                       |
| -e 'TZ=America/Sao_Paulo'  | TimeZone (Fuso Horário Brasil) da imagem docker.                                                        |
| -p 1433:1433               | Mapeia a porta 1433 do contêiner para porta 1433 do host.                                               |
| -d                         | Mapeia a porta 1433 do contêiner para porta 1433 do host.                                               |
| -v                         | Mapeamento de volume.                                                                                   |
| mcr.microsoft.com/mssql/server:2019-latest  mcr.microsoft.com/mssql/server:2022-latest | Nome da imagem usada para criar o contêiner.|

## Passo 3: Conexão via SQL Server Management Studio.

Para a conexão via SQL Server Management Studio informar em Server name o servidor (neste caso localhost), além das credenciais de acesso nos campos Login e Password:

![conexao_sql_server.png](img/conexao_sql_server.png)
