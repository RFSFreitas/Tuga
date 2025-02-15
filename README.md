# Turtl server

_Opening an issue? See the [Turtl project tracker](https://github.com/turtl/project-tracker/issues)_

This is the new Turtl server. It handles a number of things for Turtl clients:

- Account management (join/login/delete)
- Data storage
- Syncing
- Permissions and sharing

It implements a plugin architecture so things like analytics and payment
processing can be used without forcing a particular method/service.

## Running the server

The Turtl server requires [Node](https://nodejs.org/) >= 8 and a [Postgres](https://www.postgresql.org/)
instance (>= 9.6) with a dedicated user/db set up for it.

Once you have Node and Postgres set up, do the following:

```sh
mkdir turtl
cd turtl
git clone https://github.com/turtl/server
cd server/
npm install
cp config/config.yaml.default config/config.yaml
```

Now edit `config/config.yaml` as needed.
You'll want to main get your `db` settings correct, and `uploads`/`s3` sections
configured. Also, be sure to change `app.secure_hash_salt` _(unless you're going
to be running the integration tests against this server)_.

Now do:

```sh
# create the plugin directory from config.yaml#plugins.plugin_location
mkdir /path/to/plugin/dir    # (usually just plugins/ in turtl/server/)
./scripts/init-db.sh
node server.js
```

Great, done.

## Running the server (via docker-compose)

You only have to run the following docker-compose command:

```sh
docker-compose up
```

It will spawn a postgres database and the turtl server itself. Now you have a running turtl 
which is available under 'http://localhost:8181'. 

Be aware: after you cancel the docker-compose the data will be lost. For productive usage you may want
to store the postgres-data inside a docker volume.

### Configuration via ENV-Variables
In docker you may want to set each configuration value (for example the database) via environment
variables. You can override **each** default value via environment variable! Just create a variable named
with the prefix **TURTLE_** followed by the "yaml-path" written in UPPERCASE. For example: If you want
to change the **app.api_url** value you have to define the variable name like **TURTL_APP_API_URL**.

Some configuration values are explained in `config/config.yaml.default`.

## Integration tests

If you want to run the [integration tests](https://github.com/turtl/core-rs/tree/master/integration-tests)
against this instance of the server you need to do two things:

1. Leave the `app.secure_hash_salt` value as it appears in `config.yaml.default`
2. Run `node tools/populate-test.data.js`


Eu quero que voce atue como um Doutorando em Desenvolvimento de Software e me ajude a clonar o repositorio localmente e prosseguir com o desenvolvimento.
Voce deve elaborar um plano para iniciarmos o desenvolvimento, a cada etapa elaboraremos o codigo a ser feito commit pelo git e eu atualizarei no repositorio no github
Minha estação de trabalho local é um Aspire VX 15 com i7 16g de ram e 1050ti usando ubuntu mate. Eu priorizo que voce utilize o terminal ubuntu mate e bash.

 
Projeto Tuga
Github https://github.com/RFSFreitas/Tuga


Plano de Projeto para desenvolvimento do Tuga:
Objetivos do projeto:
a. Adaptar funcionalidades em uma versão personalizada do Turtl chamada Tuga.
Escopo do projeto:
a. Funcionalidades a serem implementadas:
i. Templates pré-construídos para facilitar a criação de páginas e organização de informações.
ii. Criação e gerenciamento de bases de dados personalizadas, como tabelas, quadros Kanban, galerias e calendários.
iii. Integração com uma variedade de aplicativos e serviços de terceiros, como Google Drive, Slack.
iv. Pesquisa e navegação avançadas, com opções de filtros e opções de classificação.
v. Recursos de segurança e controle de acesso, permitindo que os usuários controlem quem pode ver e editar informações.
vi. Versões para dispositivos móveis e desktop, incluindo aplicativos para dispositivos móveis (Android) e desktop (Windows e Linux).
b. Requisitos do sistema:
i. Hardware: Notebook Consumidor compatível com o Turtl.
ii. Software: Fork Turtl Server , Node JS, NPM, MongoDb.
iii. Rede: conexão à internet para integração com aplicativos e serviços de terceiros.
Orçamento:
a. O orçamento máximo é de 3 dólares.
b. Será necessária uma avaliação cuidadosa do custo da API devido à sua relação direta com o número de chamadas feitas pelo ChatGPT.
Equipe:
a. ChatGPT desenvolveu o projeto e a documentação, Rogerio Freitas é o COO e DevGPT é responsável pela análise e desenvolvimento do projeto.
b. Todos os membros devem trabalhar mantendo a arquitetura Turtl, princípios de software livre, usabilidade, minimalismo, adaptabilidade e eficiência.
Riscos:
a. Custos elevados podem representar riscos, especialmente durante o estágio de desenvolvimento.
b. Etapas que se tornarem repetitivas ou sem saída serão avaliadas criticamente.
Testes:
a. Os testes serão definidos por DevGPT.
b. Os critérios de aceitação serão definidos por DevGPT.
Implantação:
a. Após o desenvolvimento, DevGPT fará o relatorio.
b. As etapas restantes da implantação serão realizadas por Rogerio Freitas, usando o relatorio.

Diretrizes de Design
Layout limpo e organizado: seguir uma grade de layout consistente, alinhada aos princípios de design do Turtl, mas com um toque minimalista que torna mais fácil para os usuários identificar rapidamente a informação que estão buscando.
Cores neutras e tipografia simples: Usar uma paleta de cores neutras e uma tipografia simples que facilitem a leitura e evitem distrações desnecessárias.
Design modular: Criar um design modular, que permita que os usuários adicionem e removam módulos de acordo com suas necessidades, seguindo a lógica de construção de páginas e blocos do Turtl.
Ícones simples e intuitivos: Usar ícones simples e intuitivos que correspondam às funcionalidades dos módulos, permitindo que os usuários entendam rapidamente o que cada elemento significa.
Elementos de navegação intuitivos: Criar elementos de navegação intuitivos, como botões de ação claros e diretos, para ajudar os usuários a navegar com facilidade entre as páginas e blocos.
Foco na usabilidade: A usabilidade é fundamental em um design minimalista, portanto é importante garantir que as funcionalidades do Tuga sejam fáceis de usar e entender, mesmo para usuários iniciantes.
Simplificação da interface: remova elementos desnecessários da interface do usuário para criar um layout mais limpo e organizado.
Uso consistente de fontes e cores: use fontes e cores consistentes em toda a interface do usuário para criar uma aparência coesa e profissional.
Ênfase na tipografia: use tipografia clara e legível para ajudar os usuários a encontrar e compreender as informações com facilidade.
Design de ícones simplificado: utilize ícones simples e minimalistas para tornar a interface do usuário mais intuitiva e fácil de usar.
Layouts de página limpos e organizados: crie layouts de página limpos e organizados com seções bem definidas para ajudar os usuários a navegar facilmente pelas informações.
Uso adequado de espaçamento: use espaçamento adequado entre elementos para ajudar a criar uma interface do usuário bem organizada e fácil de navegar.
Foco na funcionalidade: mantenha o foco na funcionalidade e usabilidade do sistema, garantindo que as funcionalidades adicionadas atendam às necessidades do usuário e agreguem valor ao produto final.
Diretrizes de Arquitetura
Interface do usuário: O Tuga terá uma interface minimalista e intuitiva. A interface será projetada com foco na usabilidade e na experiência do usuário, permitindo que as funcionalidades sejam facilmente acessadas e utilizadas.
Banco de Dados: O Tuga utilizará um banco de dados relacional para armazenar as informações dos usuários. O banco de dados será projetado para suportar as funcionalidades de criação e gerenciamento de bases de dados personalizadas, como tabelas, quadros Kanban, galerias e calendários.
API: O Tuga terá uma API para integrar com aplicativos e serviços de terceiros, como Google Drive, Slack, Trello, entre outros. A API será projetada para garantir a segurança e a privacidade das informações dos usuários durante a integração.
Segurança: O Tuga terá recursos de segurança e controle de acesso, permitindo que os usuários controlem quem pode ver e editar suas informações. Será implementado um sistema de autenticação seguro, com diferentes níveis de permissão para os usuários.
Arquitetura de Microsserviços: A arquitetura do Tuga será baseada em microsserviços, permitindo que as funcionalidades sejam desenvolvidas e implantadas independentemente. Isso também permitirá uma maior escalabilidade e manutenção do sistema.
Aplicativos móveis e desktop: O Tuga terá aplicativos móveis para Android e iOS, bem como aplicativos desktop para Windows e Linux. Isso permitirá que os usuários acessem e gerenciem suas informações em qualquer lugar e em qualquer dispositivo.
Testes automatizados: O Tuga será testado usando testes automatizados, garantindo a qualidade e a consistência do sistema. Os testes serão definidos por DevGPT, e os critérios de aceitação serão definidos em conjunto com a equipe.
Controle de versionamento: O Tuga será gerenciado usando o Git como sistema de controle de versionamento. Todos os entregáveis serão armazenados em um repositório privado no GitHub, facilitando a colaboração entre a equipe e garantindo a integridade do código-fonte.

Etapa Atual Para Desenvolvimento
i. Templates pré-construídos para facilitar a criação de páginas e organização de informações.







