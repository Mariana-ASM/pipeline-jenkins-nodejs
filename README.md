# Pipeline Jenkins Node.js

Projeto Node.js utilizado para demonstrar um pipeline de CI/CD com Jenkins.

## Requisitos

* Node.js
* npm
* Jenkins
* Git

## Instalação

Clone o repositório:

```bash
git clone <https://github.com/Mariana-ASM/pipeline-jenkins-nodejs/blob/projeto-pipeline-jenkins-nodejs>
cd pipeline-jenkins-nodejs
```

Instale as dependências:

```bash
npm install
```

## Build

Execute o build:

```bash
npm run build
```

O comando apenas simula uma etapa de build e exibe uma mensagem de sucesso.

## Testes

Execute os testes automatizados:

```bash
npm test
```

Os testes utilizam **Jest** e **Supertest**.

## Execução

Inicie a aplicação:

```bash
npm start
```

O servidor será iniciado pelo arquivo `server.js`.

## Comandos disponíveis

```bash
npm install    # Instala as dependências
npm run build  # Executa o build
npm test       # Executa os testes
npm start      # Inicia a aplicação
```

## Pipeline com Jenkins

Para esta atividade foi criado um pipeline CI/CD utilizando Jenkins.

A configuração do pipeline está definida no arquivo `Jenkinsfile`, localizado
na raiz do projeto. O Jenkins foi configurado utilizando a opção
**Pipeline script from SCM**, obtendo o código diretamente deste repositório
no GitHub.

O pipeline executa as seguintes etapas:

```text
Checkout → Instalar Dependências → Build → Teste → Post
```

### 1. Instalação das dependências

O Jenkins instala as dependências do projeto utilizando:

```bash
npm install
```

### 2. Build

Em seguida, executa a etapa de build:

```bash
npm run build
```

Resultado obtido:

```text
Build concluido com sucesso
```

### 3. Testes automatizados

Os testes são executados através do comando:

```bash
npm test
```

Foram executados três testes da API:

* GET `/` deve retornar mensagem da API;
* GET `/status` deve retornar online;
* GET `/usuarios` deve retornar uma lista.

Resultado obtido durante a execução:

```text
Test Suites: 1 passed, 1 total
Tests:       3 passed, 3 total
```

### 4. Ações pós-execução

O `Jenkinsfile` possui um bloco `post` para tratar o resultado final do pipeline.

Em caso de sucesso:

```groovy
success {
    echo 'Pipeline executado com sucesso!'
}
```

Em caso de falha:

```groovy
failure {
    echo 'Pipeline falhou! Verifique os logs.'
}
```

## Resultado da execução

O pipeline foi executado com sucesso no Jenkins, concluindo as etapas de
instalação das dependências, build e testes automatizados.

Resultado final:

```text
Pipeline executado com sucesso!
Finished: SUCCESS
```

## Evidências da execução

### Pipeline executado com sucesso

A primeira execução do pipeline foi finalizada com sucesso no Jenkins.

<img width="1592" height="718" alt="Captura de tela 2026-09-07 213924" src="https://github.com/user-attachments/assets/6ea98c6d-54d1-4a11-a8ef-a5dfe960c1b8" />


### Testes automatizados

Os três testes automatizados foram executados com sucesso.

<img width="1600" height="341" alt="Captura de tela 2026-09-07 214237" src="https://github.com/user-attachments/assets/cf1f29c8-a712-4ada-949c-597f80ba9be7" />

### Resultado final

Ao final da execução, o bloco `post` de sucesso foi acionado e o Jenkins
finalizou o pipeline com o status `SUCCESS`.

<img width="1599" height="715" alt="Captura de tela 2026-09-07 214141" src="https://github.com/user-attachments/assets/08f42ea1-be71-495a-8248-08a0d32a72cf" />

<img width="389" height="183" alt="Captura de tela 2026-09-07 214937" src="https://github.com/user-attachments/assets/5f7053ee-4c01-4a5b-8b46-60a6992edcde" />

Também foi realizado um teste controlado para validar o comportamento do
pipeline em caso de falha.

Foi provocado temporariamente um erro na etapa de Build utilizando um comando
que retorna código de saída `1`. Com isso, o Jenkins interrompeu as etapas
seguintes e executou corretamente a ação `failure` definida no bloco `post`.

Resultado obtido:

```text
Pipeline falhou! Verifique os logs.
ERROR: script returned exit code 1
Finished: FAILURE
```

<img width="1599" height="722" alt="Captura de tela 2026-09-07 221420" src="https://github.com/user-attachments/assets/dba64440-43aa-438e-8001-c0e2f32647b0" />

<img width="740" height="361" alt="Captura de tela 2026-09-07 221429" src="https://github.com/user-attachments/assets/c64cb655-9cec-4e12-bb89-9002ecd3ce4e" />


## Tecnologias utilizadas

* Jenkins
* Node.js
* npm
* Jest
* Supertest
* Git
* GitHub

## Aprendizados

Com esta atividade foi possível compreender na prática a criação de um
pipeline CI/CD com Jenkins.

O Jenkins foi configurado para obter o `Jenkinsfile` diretamente do
repositório no GitHub e executar as etapas definidas no pipeline.

Também foi possível compreender a utilização de `stages` para organizar
as etapas de instalação, build e testes, além do bloco `post` para executar
ações diferentes de acordo com o sucesso ou falha do pipeline.
