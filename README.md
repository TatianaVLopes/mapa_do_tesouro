# FIAP - Faculdade de Informática e Administração Paulista

<p align="center">
    <a href="https://www.fiap.com.br/">
        <img src="assets/logo-fiap.png" alt="FIAP - Faculdade de Informática e Admnistração Paulista" border="0" width=40% height=40%>
    </a>
</p>

<br>

# Nome do projeto
     Um mapa do tesouro

## Nome do grupo
     TerraFusion Tech

## 👨‍🎓 Integrantes: 
- <a href="https://www.linkedin.com/in/ana-kolodji-94ba66324/">Ana Kolodi</a>
- <a href="https://www.linkedin.com/in/fernando-segregio/">Fernando Miranda Segregio</a>
- <a href="https://www.linkedin.com/in/tatiana-vieira-lopes-dos-santos-368396b3">Tatiana Lopes</a>


## 👩‍🏫 Professores:
### Tutor(a) 
- <a href="https://www.linkedin.com/in/lucas-gomes-moreira-15a8452a/">Lucas Gomes Moreira</a>
### Coordenador(a)
- <a href="https://www.linkedin.com/in/profandregodoi/">André Godoi</a>


## 📜 Descrição

Este projeto consiste em uma modelagem de dados para um sistema de monitoramento agrícola. O sistema utiliza sensores para coletar informações sobre o campo, permitindo otimizar a aplicação de água e nutrientes. Abaixo estão as entidades principais e seus relacionamentos.

# **Modelo Entidade-Relacionamento (MER)**

## **Entidade: Propriedade**
- **Atributos:**
  - `id_propriedade` (PK) – INT (Identificador único)
  - `nome` – VARCHAR(100) (Nome da propriedade)
  - `localizacao` – VARCHAR(255) (Endereço ou coordenadas)
- **Relacionamentos:**
  - 1:N com **Campo**
  - 1:N com **Produtor**

---

## **Entidade: Produtor**
- **Atributos:**
  - `produtor_id` (PK) – INT (Identificador único do produtor)
  - `nome` – VARCHAR(100) (Nome do produtor)
  - `email` – VARCHAR(50) (E-mail do produtor)
  - `telefone` – VARCHAR(15) (Telefone do produtor)
- **Relacionamentos:**
  - 1:N com **Propriedade**

---

## **Entidade: Campo**
- **Atributos:**
  - `id_campo` (PK) – INT (Identificador único do campo)
  - `id_propriedade` (FK) – INT (Referência à propriedade)
  - `tipo_cultura` – VARCHAR(100) (Cultura plantada no campo)
  - `data_plantio` – DATE (Data do plantio)
  - `data_prevista_colheita` – DATE (Previsão de colheita)
  - `area_plantada` – DECIMAL(10,2) (Área plantada em hectares)
  - `status_plantio` – VARCHAR(200) (Status do plantio)
- **Relacionamentos:**
  - 1:N com **Sensor**

---

## **Entidade: Sensor**
- **Atributos:**
  - `id_sensor` (PK) – INT (Identificador único do sensor)
  - `id_campo` (FK) – INT (Referência ao campo)
  - `tipo_sensor` – VARCHAR(50) (Exemplo: "Umidade", "pH", "Nutrientes")
  - `localizacao` – VARCHAR(100) (Localização no campo)
  - `data_instalacao` – DATE (Data de instalação)
  - `hora_instalacao` – TIME (Hora de instalação)
- **Relacionamentos:**
  - 1:N com **Leitura**

---

## **Entidade: Leitura**
- **Atributos:**
  - `id_leitura` (PK) – INT (Identificador único da leitura)
  - `id_sensor` (FK) – INT (Referência ao sensor)
  - `data_leitura` – DATE (Data da leitura)
  - `hora_leitura` – TIME (Hora da leitura)
  - `valor_leitura` – DECIMAL(10,2) (Valor registrado)
  - `limite_minimo` – DECIMAL(10,2) (Valor mínimo aceitável)
  - `limite_maximo` – DECIMAL(10,2) (Valor máximo aceitável)
- **Relacionamentos:**
  - 1:N com **Aplicação**

---

## **Entidade: Aplicação**
- **Atributos:**
  - `id_aplicacao` (PK) – INT (Identificador único da aplicação)
  - `id_leitura` (FK) – INT (Referência à leitura)
  - `quantidade_aplicada` – DECIMAL(10,2) (Quantidade aplicada)
  - `descricao` – CLOB (Descrição da aplicação)
  - `data_aplicacao` – DATE (Data da aplicação)
  - `hora_aplicacao` – TIME (Hora da aplicação)
  - `status_aplicacao` – VARCHAR(100) (Status da aplicação)

---

#### **Relacionamentos**
1. **Produtor** possui várias **Propriedades** (1:N).
2. Cada **Propriedade** pode conter vários **Campos** (1:N).
3. Cada **Campo** pode ter vários **Sensores** instalados (1:N).
4. Cada **Sensor** realiza várias **Leituras** ao longo do tempo (1:N).
5. Cada **Leitura** pode resultar em uma ou mais **Aplicações** de insumos (1:N).



## **Diagrama Entidade-Relacionamento (DER)**

![Diagrama Entidade-Relacionamento](Logical.png)
<br />
<br />

![Diagrama Entidade-Relacionamento](Relational.png)


## 📁 Estrutura de pastas

Dentre os arquivos e pastas presentes na raiz do projeto, definem-se:

- <b>.github</b>: Nesta pasta ficarão os arquivos de configuração específicos do GitHub que ajudam a gerenciar e automatizar processos no repositório.

- <b>assets</b>: aqui estão os arquivos relacionados a elementos não-estruturados deste repositório, como imagens.

- <b>config</b>: Posicione aqui arquivos de configuração que são usados para definir parâmetros e ajustes do projeto.

- <b>document</b>: aqui estão todos os documentos do projeto que as atividades poderão pedir. Na subpasta "other", adicione documentos complementares e menos importantes.

- <b>src/scripts</b>: Posicione aqui scripts auxiliares para tarefas específicas do seu projeto. Exemplo: deploy, migrações de banco de dados, backups.

- <b>src</b>: Todo o código fonte criado para o desenvolvimento do projeto ao longo das 7 fases.

- <b>log</b>: Pasta para guardar os logs da aplicação em um arquivo txt.

- <b>README.md</b>: arquivo que serve como guia e explicação geral sobre o projeto (o mesmo que você está lendo agora).


## 🔧 Como executar o código

#### Pré-requisitos
Antes de começar, verifique se você tem os seguintes pré-requisitos instalados em sua máquina:

#### 1. IDEs
Visual Studio Code (ou qualquer outra IDE de sua preferência)
PyCharm (opcional, caso você prefira um ambiente específico para Python)
#### 2. Serviços
Python 3.6 ou superior: O projeto foi desenvolvido e testado com Python 3.8.
Oracle Database: Para conectar-se ao banco de dados, você deve ter acesso a uma instância do Oracle.
#### 3. Bibliotecas
Bibliotecas Python: As bibliotecas necessárias estão listadas no arquivo requirements.txt. Abaixo estão algumas das principais bibliotecas utilizadas:

matplotlib: Para visualização de dados em forma de gráficos
pandas: Para manipulação de dados
SQLAlchemy: conexão com banco de dados
oracledb: Para conexão com o banco de dados Oracle
logging: Para Logs da aplicação

#### 4. Versões
* Python: >= 3.8
* Matplotlib: 3.9.2
* Pandas: 2.4.1
* OracleDB: 2.4.1
* Outras versões bibliotecas e versãoes seguem *requirements.txt*


#### Passos para configurar o ambiente:

1 - Com o código abaixo, crie um arquivo .env na raiz do seu projeto e preencha com os dados das suas variáveis de ambiente para conexão com o banco de dados:

```
echo -e "DB_USER=\nDB_PASSWORD=\nDB_DSN=" > .env
```
</br>

2 - Crie um ambiente virtual, atualize o pip e instale os pacotes necessários:

#### Para macOS/Linux:

```
python -m venv .venv
source .venv/bin/activate
pip install -U pip
pip install -r requirements.txt

```

#### Para Windows:

```
python -m venv .venv
.\.venv\Scripts\activate
pip install -U pip
pip install -r requirements.txt

```

3 - Rode o arquivo app.py

```
python src/app.py
```

Dicas:
- 1 - Variáveis de Ambiente: Lembre-se de preencher o arquivo **.env** com os valores corretos para **DB_USER**, **DB_PASSWORD** e **DB_DSN** antes de rodar o aplicativo.<br />
- 2 - Antes de **ativar o ambiente** verifique qual é seu **sistema operacional** e escolha o comando correto.

## 🗃 Histórico de lançamentos

* 0.1.0 - 14/10/2024
    <!-- * 
* 0.4.0 - XX/XX/2024
    * 
* 0.3.0 - XX/XX/2024
    * 
* 0.2.0 - XX/XX/2024
    * 
* 0.1.0 - XX/XX/2024
    * -->

## 📋 Licença

<img style="height:22px!important;margin-left:3px;vertical-align:text-bottom;" src="https://mirrors.creativecommons.org/presskit/icons/cc.svg?ref=chooser-v1"><img style="height:22px!important;margin-left:3px;vertical-align:text-bottom;" src="https://mirrors.creativecommons.org/presskit/icons/by.svg?ref=chooser-v1"><p xmlns:cc="http://creativecommons.org/ns#" xmlns:dct="http://purl.org/dc/terms/"><a property="dct:title" rel="cc:attributionURL" href="https://github.com/agodoi/template">MODELO GIT FIAP</a> por <a rel="cc:attributionURL dct:creator" property="cc:attributionName" href="https://fiap.com.br">Fiap</a> está licenciado sobre <a href="http://creativecommons.org/licenses/by/4.0/?ref=chooser-v1" rel="license noopener noreferrer" style="display:inline-block;">Attribution 4.0 International</a>.</p>
