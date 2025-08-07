# Apache Web Server com Docker Compose no Ubuntu Server (Azure)

Este projeto configura um servidor **Apache** usando **Docker** e **Docker Compose** para hospedar um site estático.  
O exemplo utiliza um template padrão do [StartBootstrap](https://startbootstrap.com/).

## Funcionalidades
- Servidor Apache pronto para rodar no **Ubuntu Server**.
- Montagem automática do conteúdo HTML/CSS/JS na pasta `website`.
- Mapeamento da porta **80** do container para a porta **80** da VM.
- Adaptado para rodar em **máquinas virtuais Azure**.

## Tecnologias Utilizadas
- [Docker](https://www.docker.com/)
- [Docker Compose](https://docs.docker.com/compose/)
- [Apache HTTP Server](https://httpd.apache.org/)
- [Ubuntu Server](https://ubuntu.com/server)

## Estrutura de Pastas
    .
    ├── docker-compose.yml
    └── website/
    ├── index.html
    ├── css/
    ├── js/
    └── assets/

> [Notas]
> - A pasta `website` contém os arquivos do seu site.  
> - Substitua pelo conteúdo do template do StartBootstrap.

## Como Usar:
### Pré-requisitos no Ubuntu Server (Azure)
1. **Atualizar pacotes:**
    ```
    sudo apt update && sudo apt upgrade -y
    ```

2. **Instalar Docker**
    ```
    curl -fsSL https://get.docker.com -o get-docker.sh
    sudo sh get-docker.sh
    ```

3. **Instalar Docker Compose:**
    ```
    sudo apt install docker-compose-plugin -y
    ```

4. **Liberar porta 80 no Security Group da Azure:**
    
    No portal Azure, vá em `Rede` → `Regras de segurança de entrada` e permita porta `80 (HTTP)`.

### Passos finais:
5. **Clonar o repositório na VM**:
    ```
    git clone https://github.com/AzumaNoDoragon/dockerCompose
    cd dockerCompose
    ```

6. **Adicionar os arquivos do site na pasta website/**.

7. **Subir o container**:
    ```
    docker compose up -d
    ```

8. **Acessar no navegador usando o IP público da sua VM**:

    http://SEU_IP_PUBLICO

9. **Como Parar:**
    ```
    docker compose down
    ```

## Observações
- O template do StartBootstrap deve estar dentro de website/.
- Para mudar a porta de acesso, altere o trecho ports no docker-compose.yml.
Exemplo:
    ```
    ports:
    - '8080:80'
    ```

## Licença

Este projeto está sob a licença MIT - veja o arquivo [LICENSE](LICENSE) para mais detalhes.