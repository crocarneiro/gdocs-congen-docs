---
title: "Demonstrações"
date: 2021-11-19T16:09:32-03:00
weight: 40
---

## Demo 001 | 06/11/2021
Essa é a primeira demonstração do script. É uma demonstração de usabilidade apenas, não contempla nenhum aspecto técnico. Os principais tópicos dessa demonstração são:

* Como iniciar o script
* Cadastrando os modelos: Inserindo campos simples.
* Cadastrando os modelos: Inserindo campos compostos.
* Cadastrando os modelos: Inserindo campos compostos dentro de um bloco de repetição (foreach).
* Inconsistências, tratamento de dados e formatação de campos.

### Vídeo
{{<youtube id="7b4Vj0ZL9JY" >}}

**OBS:** Se você estiver com problemas para visualizar o vídeo aqui pela página, clique nesse link: [https://youtu.be/7b4Vj0ZL9JY](https://youtu.be/7b4Vj0ZL9JY).

Vou colocar aqui embaixo o feedback recebido nessa primeira demonstração, pois ele é importante para entender alguns tópicos da segunda demonstração:

#### bigdu — 09/11/2021
> **Considerações:**

> Primeiramente está ficando muito bom e estou muito impressionado, parabéns mesmo! A solução for each foi pica, caiu uma lágrima aqui!

> Segue minhas considerações:

> Na tela de gerar contrato, inserir um elemento visual “loading”, rodando após o usuário apertar gerar contrato, para que ele saiba que o script esta rodando. Ou algo do tipo.

> Na barra lateral onde escolhemos os campos, seria incrível se pudéssemos exibir, de alguma forma, o valor do campo, um exemplo, do que viria da api. Tenho várias ideias de execução. Poderia ter um icone de “?” para cada campo que ao clicar aparecesse o exemplo.Ou deixar o mouse parado em cima do campo e surgisse um balao com o valor daquele campo. Esses valores viriam deste contrato id 65. Eu popularia todo ele com dados para que aparecesse aí nesses exemplos. Nao sei se pesaria muito

> Inserir um indicador se o script carregou ok ou se deu erro, na primeira vez que a gente abrir. Por exemplo, o token pode dar erro, ou expirar um dia. Podia dar um aviso caso isso acontecesse. Esse teste poderia ocorrer toda vez que desse o start.
Inconsistência Dados e Tratamento de dados e Nomes por extenso

> **Você comentou no vídeo sobre estes assuntos vou dar um feedback.**

> **Inconsistência Dados:** Este tópico não é tão problemático. O pessoal daqui pode padronizar a forma de como escrever na API com acentos e tudo mais.

> **Tratamento de dados:** Este tópico é crucial… Realmente a gente não pensou nisso. É preciso verificar como os dados são escritos no Sistema. Penso que não será preciso tratar os dados para tudo, apenas alguns específicos. Eu precisava testar a ferramenta e enumerar quais seriam fundamentais. Por exemplo, apareceu o número 2 no campo de estado civil ao invés de aparecer “casado” ou “solteiro”. De repente 2 é como o ingaia salva o estado civil pois é um campo com valor fixo, imutavel, não é uma string, daí os programadores deles devem ter decidido fazer assim. Nesses casos precisamos tratar isso para jogar o texto que deveria ser, caso venha 2 como valor. No gerador de contratos dele vem o nome ao invés do número. Outro caso é os dados de CPF e CNPJ. A ferramenta precisava ler os numeros e escrever com pontos. Eu tenho um script no google que eu resolvi essas questoes de tratamento usando REGEX. Eu posso ajudar nisso.

> **Números por extenso:** Uma vez eu queria fazer isso do nada. Eu fiz uma mega pesquisa e voce acredita que eu encontrei um script no proprio App Script que fazia exatamente isso no google Sheets. Será que voce consegue implementar? Ele escreve não só o número, mas também a ordem dele, “centena”, “mil”, “centavos”. Poderia ter uma opção na tag, para dizer ao script que aquele valor precisa ser retornado por extenso, passando o valor para esta funcionalidade.

## Demo 002 | 22/11/2021

Essa demo contempla as melhorias que foram feitas em resposta ao feedback da primeira demo:

* Alterações visuais:
    * Remoção do título
    * Criação da [toolbar](/toolbar)
    * Moção do botão foreach para dentro da [toolbar](/toolbar).
* Possibilidade de visualizar o valor dos campos que constam no contrato de ID 65.
* Possibilidade de criar [funções de formatação](/toolbar/#format-function).

Para mais detalhes sobre a toolbar [clique aqui](/toolbar).

### Vídeo
{{<youtube id="CFosIwk36Ag" >}}

**OBS:** Se você estiver com problemas para visualizar o vídeo aqui pela página, clique nesse link: [https://youtu.be/CFosIwk36Ag](https://youtu.be/CFosIwk36Ag).


Para ver as considerações referentes a segunda demonstração baixe o PDF clicando [aqui](/files/Consideracoes_Demo_02_.pdf).