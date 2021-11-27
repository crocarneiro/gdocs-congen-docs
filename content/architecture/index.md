---
title: "Arquitetura"
date: 2021-11-24T09:52:12-03:00
weight: 30
---

## Introdução

Aqui nessa página explicarei um pouco da arquitetura da solução, as tecnologias que foram usadas para desenvolvê-la e vou fazer um passo a passo de como configurar um ambiente de desenvolvimento.

O primeiro protótipo que eu fiz era extremamente simples. Era composto de apenas 3 arquivos, um arquivo .html com o layout da barra lateral, um arquivo .js com o código em javascript da barra lateral e um arquivo .gs com o código em AppsScript para gerar os arquivos (que é a mesma coisa que javascript bem dizer). Ou seja, não havia mistério algum. Porém, a solução final tem um nível de complexidade muito mais alto. Isso exigiu que se utilizasse mais tecnologias, sem as quais não seria possível fazer o que foi feito. Na solução final foram utilizadas as seguintes tecnologias:

* HTML, javascript e CSS (conforme o esperado)
* [React](https://pt-br.reactjs.org/)
* [Material UI](https://mui.com/)
* [React-Google-Apps-Script](https://github.com/enuchi/React-Google-Apps-Script): Um template para desenvolver AppsScripts com React.

Sem citar com muitos detalhes todos os pacotes utilizados, foram essas as tecnologias usadas no desenvolvimento do gdocs-congen.

Ao todo temos 2 repositórios:

1. gdocs-congen: Repositório principal, armazena o código do AppsScript e mantém 98% da complexidade do negócio.
3. gdocs-congen-docs: Repositório que armazena essa documentação aqui.


## Acesso aos repositórios
Para ter acesso ao código-fonte, o jeito mais fácil é criando uma conta no [Github](https://github.com/) e me passando o nome de usuário. Dessa forma eu consigo liberar acesso ao repositório para você e você consegue fazer uma cópia dele para sua própria conta. Dessa forma você também tem acesso à todas as atualizações que eu for fazendo.

Após criar sua conta no Github, veja o vídeo abaixo para ver quais são os próximos passos:

{{<youtube id="RkevRuTqsNo" >}}

**OBS:** Se você estiver com problemas para visualizar o vídeo aqui pela página, clique nesse link: [https://youtu.be/RkevRuTqsNo](https://youtu.be/RkevRuTqsNo).

## Ambiente de desenvolvimento
Não vou entrar nos detalhes do ambiente de desenvolvimento do servidor em Java, porque provavelmente vocês não vão precisar alterar ele, até porque ele já faz o que deveria fazer. Vou falar do ambiente de desenvolvimento para o AppsScript em si, que é o principal.

### Dependências
Para trabalhar com ele é preciso fazer a instalação de algumas ferramentas:

* [NodeJS](https://nodejs.org/en/): Recomendo a instalação da versão LTS.
* [clasp](https://developers.google.com/apps-script/guides/clasp): Essa é a linha de comando do Google. Depois de ter instalado o node, basta rodar o seguinte comando para instalar o clasp: `npm install @google/clasp -g`
    * É necessário fazer login no clasp com o comando `clasp login`. O login deve ser feito na conta que se quer instalar o script.

E a princípio é só isso.

## Deploy do script
Com deploy queremos dizer "instalar o script em algum documento do Google". Para fazer isso precisamos seguir algumas etapas:

1. Criar um documento do Google. Criar um script atrelado a ele e copiar o ID desse script.

![passo1](/images/2021-11-26-10_54_21-Window.png)
![passo2](/images/2021-11-26-10_57_42-Window.png)
![passo3](/images/2021-11-26-10_58_58-Window.png)

2. Dentro da pasta raiz do repositório "gdocs-congen", devemos criar um arquivo chamado ".clasp.json". Esse arquivo vai ter dentro de si o seguinte conteúdo:
```
{"scriptId":"id_do_script","rootDir":"dist"}
```

No seu arquivo, você vai substituir o texto "id_do_script" pelo ID do seu script recém criado.

3. Depois, basta rodar os comandos `npm install` e `npm run deploy` na pasta raiz do diretório "gdocs-congen" que o script será compilado e o upload do resultado será feito para dentro do script recém criado.

**Após estas etapas o menu "Gerador de Contratos" já deve aparecer no documento criado.**

## Configuração do script
Ao executar o script pela primeira vez é necessário configurá-lo para que ele funcione corretamente. Essa configuração consiste em informar 2 variáveis:

* **app_token:** Da API do Super Lógica
* **access_token:** Da API do Super Lógica

Para configurar o script apenas acesse o menu "Gerador de Contratos -> Configurações" e informe os campos necessários.

{{< warning title="OBS" >}}
O botão "limpar cache" limpa as configurações, mas também limpa as funções de formatação dos campos.
{{< /warning >}}