---
title: "Arquitetura"
date: 2021-11-24T09:52:12-03:00
weight: 30
---

Aqui nessa página explicarei um pouco da arquitetura da solução, as tecnologias que foram usadas para desenvolvê-la e vou fazer um passo a passo de como configurar um ambiente de desenvolvimento.

O primeiro protótipo que eu fiz era extremamente simples. Era composto de apenas 3 arquivos, um arquivo .html com o layout da barra lateral, um arquivo .js com o código em javascript da barra lateral e um arquivo .gs com o código em AppsScript para gerar os arquivos (que é a mesma coisa que javascript bem dizer). Ou seja, não havia mistério algum. Porém, a solução final tem um nível de complexidade muito mais alto. Isso exigiu que se utilizasse mais tecnologias, sem as quais não seria possível fazer o que foi feito. Na solução final foram utilizadas as seguintes tecnologias:

* HTML, javascript e CSS (conforme o esperado)
* [React](https://pt-br.reactjs.org/)
* [Material UI](https://mui.com/)
* [React-Google-Apps-Script](https://github.com/enuchi/React-Google-Apps-Script): Um template para desenvolver AppsScripts com React.
* Java e SpringBoot para o servidor.

Sem citar com muitos detalhes todos os pacotes utilizados, foram essas as tecnologias usadas no desenvolvimento do gdocs-congen.

Agora que eu citei as "ferramentas" usadas no projeto, vou falar das partes que compõe o projeto. Como assim "partes" se a única parte que deveria ter é um script para Google Docs? Em tese sim, mas na prática existem alguns detalhes técnicos que adicionam uma certa complexidade. Por exemplo, percebeu que citamos um "servidor"? Por que precisamos de um servidor? Bom, toda nossa solução se sustenta no fato de que podemos utilizar a [API do Super Lógica Imobiliárias](https://superlogicaimobiliarias.docs.apiary.io/#) né? Pois então, existe uma medida de segurança que os navegadores (Chrome, Firefox, Safari, etc) implementam que é conhecida como [CORS](https://developer.mozilla.org/en-US/docs/Web/HTTP/CORS) que meio que não nos permite fazer chamadas diretamente para a API de "dentro" do navegador, porque o domínio da nossa extensão e o domínio da API do Super Lógica são diferentes e a API deles não tem nenhuma exeção para CORS. Para resolver esse problema foi desenvolvido um webservice, uma API, que serve simplesmente para fazer requisições para o Super Lógica e mandar de volta para o nosso AppsScript. O diagrama abaixo ilustra bem essa situação:

![estrutura de comunicação do gdocs-congen](/images/extension_communication_structure.png)

O código da API fica em um repositório separado do código do script, e essa documentação aqui também é um repositório separado. Então ao todo temos 3 repositórios:
1. gdocs-congen: Repositório principal, armazena o código do AppsScript e mantém 98% da complexidade do negócio.
2. gdocs-congen-ws: Repositório referente ao webservice criado para fazer a ponte entre o gdocs-congen e a API do Super Lógica.
3. gdocs-congen-docs: Repositório que armazena essa documentação aqui.