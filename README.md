<h1>Gerenciador NODE</h1>

Gerenciador de ambiente node simples usando apenas script shell e dependências mínimas.

![Tela principal gerenciador-node](/imagens/tela-principal.png)  

<b>O que esse projeto faz?</b>

Ele padroniza a instalação e a alternância entre multiplas versões do node num sistema Linux.

<b>O que esse projeto não faz?</b>
Ele não executa verificações de segurança no arquivo, portanto cabe ao usuário bom senso na obtenção de pacotes node.
Obtenha arquivos de fontes confiáveis, e verifique regularmente no site NodeJS para a obtenção de atualizações de segurança.
Por exemplo obtenha pacotes seguros em: https://nodejs.org/pt

<b>Cenários de uso:</b>
Ambientes de desenvolvimento e uso pessoal. Não recomendo a atilização no estado atual em ambientes de produção.

<b> Vantagens de utilização:</b>
Simplicidade: A solução utiliza pouquíssimas dependências, muitas vezes já disponibilizadas numa instalação padrão Debian. O script pode
ser aprimorado por qualquer usuário comum pois é de fácil leitura e baixa complexidade. Ele concentra todas as funcionalidades em apenas 
um arquivo.
Controle total: O usuário pode obter a versão mais recente no próprio site e não fica dependente de disponibilização em repositório
centralizado. O gerenciador permite também a instalação de arquivos locais sem a utilização de conexões de internet o que facilita a criação
e reprodução de ambientes em multiplos equipamentos.
Aprendizado: Ao ler o script e tentar modificá-lo o usuário pode desenvolver novas habilidades no uso de shell script e perceber como ele pode automatizar
tarefas repetitivas.

<b> Como ele faz isso?</b>
Utilizando apenas 2 dependências (tar e wget) geralmente já pré instaladas em sistemas Debian e links simbólicos. O gerenciador
extrai o arquivo com o pacote node para pasta do usuário e organiza em pastas de acordo com o número da versão.  O script tenta 
extrair do nome do arquivo o número da versão. Caso ele não consiga solicita ao usuário o fornecimento manual da versão.
Ele pode promover a instalação de arquivos locais ou através de uma url. Utilizando apenas ferramentas nativas o script controla as 
variáveis de ambiente no basrc garantindo que elas apontem para a versão que o usuário deseja utilizar no momento.

<h2>Como instalar?</h2>

<b>No terminal com sua conta de usuário comum execute:</b>

```bash
wget -qO- https://raw.githubusercontent.com/souza-lb/gerenciador-node/main/instalar | bash
```
<b> Requisitos:</b>
* Sistema Debian 12 (ou demais sistemas baseados em Debian...)
* wget
* tar
* Conexão com internet disponível (apenas no momento da instalação)
* Espaço em disco (Pelo menos 30MB para instalação de um pacode node)

<b> Aviso importante!</b>
Não utilize a conta de superusuário para a instalação.

<h2>Como utilizar?</h2>

<b>No terminal com sua conta de usuário comum execute:</b>

```bash
gerenciador-node
```

<b>Como não foi selecionada nenhuma opção será exibida a ajuda</b>

![Tela ajuda](/imagens/tela-ajuda.png)  

<b>Vamos prosseguir com a instalação de 2 versões do node</b>

<b>No terminal execute:</b>

```bash
gerenciador-node instalar https://nodejs.org/dist/v22.15.1/node-v22.15.1-linux-x64.tar.xz
```
<b>Aguarde a finalização do processo de download</b>

![Tela download](/imagens/tela-download.png)

<b>Após a conclusão do download você deverá receber a mensagem abaixo</b>

![Tela sucesso instalação](/imagens/tela-sucesso-download.png)

<b>Prossiga com a instalação de uma nova versão do node</b>

```bash
gerenciador-node instalar https://nodejs.org/dist/v24.0.2/node-v24.0.2-linux-x64.tar.xz
```

<b>Agora vamos listar as versões disponíveis</b>

```bash
gerenciador-node listar
```

<b>Você receberá uma saída como abaixo</b>

![Tela listagem](/imagens/tela-listagem-node.png)

<b>Vamos definir uma versão como padrão</b>

Execute no terminal como usuário comum

```bash
gerenciador-node definir v22.15.1
```

Se você deseja aplicar imediatamente a mudança no terminal corrente sem precisar fechá-lo execute então (inclua um ponto na frente do comando):

```bash
. gerenciador-node definir v22.15.1
```

Em seguida liste novamente com

```bash
gerenciador-node listar
```

Repare que agora é exibido um asterisco (*) indicando qual a versão está definida como padrão.

![Tela versão padrão](/imagens/tela-versao-padrao.png)

Vamos verificar qual versão está definida como corrente. Execute no terminal:

```bash
node --version
```
Observe a saída abaixo

![Tela node atual](/imagens/tela-node-atual.png)

Agora vamos alternar para a versão mais recente. Execute no terminal

```bash
. gerenciador-node definir v24.0.2
```
Experimente listar novamente as versões disponíveis (repare que o asterisco aponta a nova versão como padrão)

```bash
gerenciador-node listar
```

![Tela nova versão](/imagens/tela-nova-versao.png)

Vamos verificar se a versão 24 realmente está em uso. Execute no terminal

```bash
node --version
```

Observe a saída conforme abaixo

![Tela node novo](/imagens/tela-node-novo.png)

<b>Vamos abordar a opção de remoção de versões do node. Tente remover uma versão em uso conforme abaixo</b>

```bash
gerenciador-node remover v24.0.2
```

Você receberá a seguinte saída:

![Tela remoção](/imagens/tela-remocao.png)

Observe a pasta que armazena as versões disponíveis

![Tela pasta versões](/imagens/tela-pasta-versoes.png)

Alterne para a versão 22 e tente novamente a remoção

```bash
. gerenciador-node definir v22.15.1
```

Agora remova com

```bash
gerenciador-node remover v24.0.2
```

Confirme a remoção

![Tela confirmação remoção](/imagens/tela-confirmação-remoção.png)


Observe a mudança na pasta que armazena as versões

![Tela pasta versão removida](/imagens/tela-pasta-versao-removida.png)


<b>Dúvidas sugestões e contribuições?</b>
Leonardo Bruno
souzalb@proton.me

<b>Gostou do projeto e quer realizar um contribuição voluntária para o desenvolvedor? (Pode ser o valor de uma xícara de café ou chá...) ☕ 🍵
Segue minha chave pix: 8dcc7e3c-0c6a-4c6f-a4c0-26a5e62686db

Ou utilize o QR Code abaixo
</b>

<p align="center">
  <img src="/imagens/qrcode-pix.png" alt="código-qr">
</p>

<b>Você também pode utilizar o PayPal para uma doação</b>

[![PayPal](https://img.shields.io/badge/Donate-PayPal-00457C?style=for-the-badge&logo=paypal)](https://www.paypal.com/donate/?hosted_button_id=EQVW5QQ7GBGSY)


<p align="center">
  <img src="/imagens/qrcode-paypal.png" alt="código-qr-paypal">
</p>

<b>A utilização deste projeto é livre para alterações e adaptações feita a devida referência ao repositório original e seu criador.</b>
