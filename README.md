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

## 1 - **Modelo Entidade-Relacionamento (MER)**

### **Entidade: Propriedade**
- **Atributos:**
  - `id_propriedade` (PK) – INT (Identificador único)
  - `id_produtor` (FK) – INT (Referência ao produtor)
  - `nome` – VARCHAR(100) (Nome da propriedade)
  - `localizacao` – VARCHAR(255) (Endereço ou coordenadas)
- **Relacionamentos:**
  - 1:N com **Campo**
  - 1:N com **Produtor**

---

### **Entidade: Produtor**
- **Atributos:**
  - `produtor_id` (PK) – INT (Identificador único do produtor)
  - `nome` – VARCHAR(100) (Nome do produtor)
  - `email` – VARCHAR(50) (E-mail do produtor)
  - `telefone` – VARCHAR(15) (Telefone do produtor)
- **Relacionamentos:**
  - 1:N com **Propriedade**

---

### **Entidade: Campo**
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

### **Entidade: Sensor_Umidade**
- **Atributos:**
  - `id_sensor_umidade` (PK) – INT (Identificador único do sensor)
  - `id_campo` (FK) – INT (Referência ao campo)
  - `localizacao` – DECIMAL(100) (Localização no campo)
  - `data_instalacao` – DATE (Data de instalação)
  - `hora_instalacao` – TIME (Hora de instalação)
- **Relacionamentos:**
  - 1:N com **Leitura_sensor_Umidade**

---

### **Entidade: Leitura_sensor_Umidade**
- **Atributos:**
  - `id_leitura_umidade` (PK) – INT (Identificador único da leitura)
  - `id_sensor_umidade` (FK) – INT (Referência ao sensor)
  - `data_leitura` – DATE (Data da leitura)
  - `hora_leitura` – TIME (Hora da leitura)
  - `valor_umidade_leitura` – DECIMAL(10,2) (Valor registrado)
  - `limite_minimo_umidade` – DECIMAL(10,2) (Valor mínimo aceitável)
  - `limite_maximo_umidade` – DECIMAL(10,2) (Valor máximo aceitável)
- **Relacionamentos:**
  - 1:N com **Aplicação_umidade**

---

### **Entidade: Aplicação_umidade**
- **Atributos:**
  - `id_aplicacao_umidade` (PK) – INT (Identificador único da aplicação)
  - `id_leitura_sensor_umidade` (FK) – INT (Referência à leitura)
  - `quantidade_aplicada` – DECIMAL(10,2) (Quantidade aplicada)
  - `descricao` – CLOB (Descrição da aplicação)
  - `data_aplicacao` – DATE (Data da aplicação)
  - `hora_aplicacao` – TIME (Hora da aplicação)
  - `status_aplicacao` – VARCHAR(100) (Status da aplicação)

---

### **Entidade: Sensor_PH**
- **Atributos:**
  - `id_sensor_ph` (PK) – INT (Identificador único do sensor)
  - `id_campo` (FK) – INT (Referência ao campo)
  - `localizacao` – DECIMAL(100) (Localização no campo)
  - `data_instalacao` – DATE (Data de instalação)
  - `hora_instalacao` – TIME (Hora de instalação)
- **Relacionamentos:**
  - 1:N com **Leitura_sensor_ph**

---

### **Entidade: Leitura_sensor_PH**
- **Atributos:**
  - `id_leitura_ph` (PK) – INT (Identificador único da leitura)
  - `id_sensor_ph` (FK) – INT (Referência ao sensor)
  - `data_leitura` – DATE (Data da leitura)
  - `hora_leitura` – TIME (Hora da leitura)
  - `valor_ph_leitura` – DECIMAL(10,2) (Valor registrado)
  - `limite_minimo_ph` – DECIMAL(10,2) (Valor mínimo aceitável)
  - `limite_maximo_ph` – DECIMAL(10,2) (Valor máximo aceitável)
- **Relacionamentos:**
  - 1:N com **Aplicação_PH**

---

### **Entidade: Aplicação_PH**
- **Atributos:**
  - `id_aplicacao_ph` (PK) – INT (Identificador único da aplicação)
  - `id_leitura_sensor_ph` (FK) – INT (Referência à leitura)
  - `quantidade_aplicada` – DECIMAL(10,2) (Quantidade aplicada)
  - `descricao` – CLOB (Descrição da aplicação)
  - `data_aplicacao` – DATE (Data da aplicação)
  - `hora_aplicacao` – TIME (Hora da aplicação)
  - `status_aplicacao` – VARCHAR(100) (Status da aplicação)

---

### **Entidade: Sensor_Nutrientes**
- **Atributos:**
  - `id_sensor_nutrientes` (PK) – INT (Identificador único do sensor)
  - `id_campo` (FK) – INT (Referência ao campo)
  - `localizacao` – DECIMAL(100) (Localização no campo)
  - `data_instalacao` – DATE (Data de instalação)
  - `hora_instalacao` – TIME (Hora de instalação)
- **Relacionamentos:**
  - 1:N com **Leitura_sensor_nutrientes**

---

### **Entidade: Leitura_sensor_nutrientes**
- **Atributos:**
  - `id_leitura_nutrientes` (PK) – INT (Identificador único da leitura)
  - `id_sensor_nutrientes` (FK) – INT (Referência ao sensor)
  - `data_leitura` – DATE (Data da leitura)
  - `hora_leitura` – TIME (Hora da leitura)
  - `valor_ nutrientes _leitura` – DECIMAL(10,2) (Valor registrado)
  - `limite_minimo_ nutrientes ` – DECIMAL(10,2) (Valor mínimo aceitável)
  - `limite_maximo_ nutrientes ` – DECIMAL(10,2) (Valor máximo aceitável)
- **Relacionamentos:**
  - 1:N com **Aplicação_ nutrientes **

---

### **Entidade: Aplicação_ nutrientes**
- **Atributos:**
  - `id_aplicacao_ nutrientes ` (PK) – INT (Identificador único da aplicação)
  - `id_leitura_sensor_ nutrientes ` (FK) – INT (Referência à leitura)
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



## 2 - **Diagrama Entidade-Relacionamento (DER)**

![Diagrama Entidade-Relacionamento](Logical.png)
<br />
<br />

![Diagrama Entidade-Relacionamento](Relational.png)


## 📁 Estrutura de pastas

- <b>assets</b>: aqui estão os arquivos relacionados a elementos não-estruturados deste repositório, como imagens.

- <b>Logical.png</b>: Arquivo com a imagem da estrutura lógica da modelagem de dados.

- <b>Relational.png</b>: Arquivo com a imagem da estrutura relacional da modelagem de dados.

- <b>Monitoramento_plantio.xml<b>: Arquivo com o XML estraido da modelagem de dados.

- <b>README.md</b>: arquivo que serve como guia e explicação geral sobre o projeto (o mesmo que você está lendo agora).


## 3 - Ferramentas utilizadas
* DataModeler: Versão 23.1.0.087

## 🗃 Histórico de lançamentos

* 0.1.0 - 16/10/2024 - 21h39
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
