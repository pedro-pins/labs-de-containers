# labs-de-containers
<<<<<<< HEAD
## Criando o Lab, instalando o Docker e Portainer
=======
>>>>>>> 1d9402e (adicionando para novo repositorio)
> ### *Docker e Portainer: Uma Dupla Dinâmica para Containers*
>
> ***==Docker==*** *==e **Portainer** são ferramentas poderosas e complementares no universo dos containers. Para entender melhor como elas funcionam e se relacionam, vamos explorar cada uma delas individualmente:==*
>
> ### *==Docker: A Base para a Contenização==*
>
> *==O **Docker** é uma plataforma de desenvolvimento que permite criar e gerenciar **containers**. Um container é como um pacote isolado que contém tudo o necessário para executar um aplicativo: código, runtime, bibliotecas, configurações, etc.==*
>
> ***==Em resumo:==*** *==O Docker é a base para a criação e gerenciamento de containers, proporcionando um ambiente consistente e portátil para suas aplicações.==*
>
> ### *==Portainer: A Interface Gráfica para o Docker==*
>
> *==O **Portainer** é uma interface gráfica que facilita a interação com o Docker. Em vez de utilizar comandos complexos na linha de comando, você pode usar o Portainer para:==*
>
> ***==Em resumo:==*** *==O Portainer é uma ferramenta que torna o Docker mais acessível e fácil de usar, especialmente para usuários que não estão familiarizados com a linha de comando.==*

> ***Documentações oficiais de Docker & Portainer***
>
> Docker: [https://docs.docker.com/](/doc/httpsdocsdockercom-CwsIRMkSvR) 
>
> Portainer: <https://docs.portainer.io/>

\
### Este arquivo de instalação e configuração do Docker e Portainer: 

### Passo 1: Instalar o Docker

Primeiro, vamos instalar o Docker no sistema.


1. **Atualize os pacotes do sistema:**

   ```javascript
   sudo apt update
   sudo apt upgrade 
   ```
2. **Instale os pré-requisitos para o Docker:**

   ```javascript
   sudo apt install apt-transport-https ca-certificates curl software-properties-common -y
   ```
3. **Adicione o repositório do Docker:**

   ```javascript
   curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg
   echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
   ```
4. **Instale o Docker:**

   ```javascript
   sudo apt update
   sudo apt install docker-ce docker-ce-cli containerd.io -y
   ```
5. **Verifique se o Docker está instalado e rodando corretamente:**

   ```javascript
   sudo systemctl status docker
   ```

   Você pode verificar a versão do Docker também:

   ```javascript
   docker --version
   ```
6. **Adicione o seu usuário ao grupo docker (opcional, para evitar usar sudo):**

   ```javascript
   sudo usermod -aG docker $USER
   ```

   Após isso, saia e entre novamente no terminal para que a alteração tenha efeito.

### Passo 2: Instalar o Portainer

Portainer é uma interface de gerenciamento do Docker que roda como um contêiner Docker.


1. **Crie um volume para o Portainer (para armazenar dados):**

   ```javascript
   sudo docker volume create portainer_data
   ```
2. **Baixe e execute o contêiner do Portainer:**

   \
   ```javascript
   sudo docker run -d -p 8000:8000 -p 9443:9443 -p 9000:9000 --name=portainer --restart=always -v /var/run/docker.sock:/var/run/docker.sock -v portainer_data:/data portainer/portainer-ce:latest
   ```

   Este comando irá:
   * Baixar e iniciar o Portainer, expondo as portas 8000, 9443 (HTTPS) e 9000 (interface web).
   * Usar o volume `portainer_data` para persistir dados do Portainer.
   * Montar o Docker socket (`/var/run/docker.sock`) para que o Portainer se comunique com o Docker.

### Passo 3: Acessar o Portainer


1. Abra o navegador e vá para o endereço:

   ```javascript
   http://localhost:9000
   ```
2. **Configurar o usuário administrador:** Na primeira vez que acessar o Portainer, será solicitado que você crie um usuário administrador.
3. **Conectar ao ambiente Docker local:** Depois de logar, selecione "Local" como o ambiente Docker para gerenciar o Docker diretamente pelo Portainer.

<<<<<<< HEAD
Agora, o Docker e o Portainer estão configurados e comunicando entre si! Você pode gerenciar os contêineres do Docker através da interface web do Portainer.
=======
Agora, o Docker e o Portainer estão configurados e comunicando entre si! Você pode gerenciar os contêineres do Docker através da interface web do Portainer.
>>>>>>> 1d9402e (adicionando para novo repositorio)
