# Inception

## Regras Gerais

[ ] Este projeto deve ser realizado em uma Máquina Virtual.

[ ] Todos os arquivos necessários para a configuração do seu projeto devem ser colocados na pasta srcs.

[ ] Um Makefile também é necessário e deve estar localizado na raiz do seu diretório. Ele deve configurar toda a sua aplicação (ou seja, tem que construir as imagens Docker usando o arquivo docker-compose.yml).

[ ] Este assunto requer a aplicação de conceitos que, dependendo do seu histórico, você pode ainda não ter aprendido. Portanto, recomendamos que você leia bastante documentação relacionada ao uso do Docker, além de qualquer outra coisa que achar útil para concluir esta tarefa.

## Parte Obrigatória

Este projeto consiste em configurar uma pequena infraestrutura composta por diferentes serviços sob regras específicas. Todo o projeto deve ser feito em uma máquina virtual. Você deve usar docker-compose.

[ ] Cada imagem Docker deve ter o mesmo nome que o serviço correspondente.

[ ] Cada serviço deve ser executado em um contêiner dedicado.

[ ] Por questões de desempenho, os contêineres devem ser construídos a partir da penúltima versão estável do Alpine ou Debian. A escolha é sua.

[ ] Você também deve escrever seus próprios Dockerfiles, um para cada serviço. Os Dockerfiles devem ser chamados no seu docker-compose.yml pelo Makefile.
* Isso significa que você deve construir as imagens Docker do seu projeto. É proibido puxar imagens Docker prontas ou usar serviços como o DockerHub (com exceção do Alpine/Debian).

### Voce deve configurar:

[ ] Um contêiner Docker que contenha NGINX com apenas TLSv1.2 ou TLSv1.3

[ ] Um contêiner Docker que contenha WordPress + php-fpm (deve ser instalado e configurado), sem nginx.

[ ] Um contêiner Docker que contenha apenas MariaDB, sem nginx.

[ ] Um volume que contenha o banco de dados do WordPress.

[ ] Um segundo volume que contenha os arquivos do seu site WordPress.

[ ] Uma rede Docker que estabeleça a conexão entre seus contêineres.

### Seus contêineres devem reiniciar em caso de falha.

Um contêiner Docker não é uma máquina virtual. Portanto, não é recomendado usar qualquer "gambiarra" baseada em 'tail -f', e assim por diante, para mantê-lo rodando. Leia sobre como os daemons funcionam e se é uma boa ideia usá-los ou não.

[ ] É proibido usar network: host, --link ou links:.

[ ] A linha de rede deve estar presente no arquivo docker-compose.yml

[ ] Seus contêineres não devem ser iniciados com um comando que execute um loop infinito. Isso também se aplica a qualquer comando usado como entrypoint ou em scripts entrypoint. Alguns exemplos de práticas proibidas: tail -f, bash, sleep infinity, while true.

[ ] Leia sobre PID 1 e as melhores práticas para escrever Dockerfiles.

[ ] No banco de dados WordPress, devem haver dois usuários, sendo um deles o administrador. O nome de usuário do administrador não pode conter "admin" ou "administrator" (ex.: admin, administrator, admin-123, etc.).

[ ] Seus volumes estarão disponíveis na pasta /home/login/data da máquina host que usa Docker. Substitua "login" pelo seu login.

[ ] Para simplificar, você deve configurar o nome do domínio para apontar para seu endereço IP local. Este nome de domínio deve ser login.42.fr. Novamente, use seu próprio login. Por exemplo, se seu login for wil, wil.42.fr redirecionará para o IP apontando para o site de wil.

[ ] A tag latest está proibida.

[ ] Nenhuma senha deve estar presente nos seus Dockerfiles.

[ ] É obrigatório usar variáveis de ambiente e fortemente recomendado usar um arquivo .env para armazenar essas variáveis. Também é altamente recomendado usar os Docker secrets para armazenar informações confidenciais.

[ ] O contêiner NGINX deve ser o único ponto de entrada na sua infraestrutura, via porta 443, usando o protocolo TLSv1.2 ou TLSv1.3.