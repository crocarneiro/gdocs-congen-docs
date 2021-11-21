---
title: "Barra de Ferramentas"
date: 2021-11-19T10:50:05-03:00
weight: 20
---

## Introdução

A barra de ferramentas é a barra que encontramos no topo da barra lateral da nossa extensão. Nela temos as opções necessárias para "formatar" nosso layout. Por enquanto temos duas ferramentas disponíveis:

1. Foreach: Blocos de repetição.
2. Format functions: Funções de formatação de dados.

## Format function
Essa opção serve para criarmos funções de formatação para nossos dados. Todas as funções de formatação são funções em javascript que recebem um único parâmetro (value). Essa parâmetro é o valor do campo no momento da geração do contrato. Dado que temos esse valor podemos usar todos os recursos da linguagem javascript para formatar o campo como desejamos.

Segue abaixo alguns exemplos, os mais comuns e necessários, de funções que podemos usar em nossos templates:

### CPF
Essa função pode ser usada nos campos de CPF. Normalmente as APIs retornam esses campos como uma string de 11 números sem nenhuma pontuação. Essa função recebe esses valores sem pontuação e coloca a pontuação neles:

Ex:

Valor antes -> 05342699070

Valor depois -> 053.426.990-70

#### **Código da função**
```
function (value){
	return new String(value).replace(/(\d{3})(\d{3})(\d{3})(\d{2})/, "$1.$2.$3-$4");
}
```

### CNPJ
Essa função pode ser usada nos campos de CNPJ. Normalmente as APIs retornam esses campos como uma string de 14 números sem nenhuma pontuação. Essa função recebe esses valores sem pontuação e coloca a pontuação neles:

Ex:

Valor antes -> 80707629000105

Valor depois -> 80.707.629/0001-05

#### **Código da função**
```
function (value){
	return new String(value).replace(/(\d{2})(\d{3})(\d{3})(\d{4})(\d{2})/, "$1.$2.$3/$4-$5");
}
```

### CPF ou CNPJ
Em casos onde não sabemos se o campo vai retornar um CPF ou um CNPJ, podemos utilizar a seguinte função:

#### **Código da função**
```
function (value){
	if(new String(value).length > 11)
		return new String(value).replace(/(\d{2})(\d{3})(\d{3})(\d{4})(\d{2})/, "$1.$2.$3/$4-$5");
	else
		return new String(value).replace(/(\d{3})(\d{3})(\d{3})(\d{2})/, "$1.$2.$3-$4");
}
```

### Valor monetário em extenso
Muitas vezes é necessário que os números que retornam da API sejam escritos por extenso. Para isso podemos utilizar a função `extenso()`.

#### **Código da função**
```
function (value){
	return new String(value).extenso('real', 'reais', 'centavo', 'centavos');
}
```

### Adicionar cifrão na frente do número
Os números referentes a valores monetários costumam vir em formato de ponto flutuante das APIs, ou seja, os valores vem como números com casas decimais separadas por ponto sem nenhuma formatação. Porém em documentos, ou na nossa escrita do dia a dia, normalmente se coloca o cifrão na frente dos valores e o separador decimal é a vírgula. Para conseguir esse efeito podemos usar a seguinte função de formatação:


#### **Código da função**
```
function (value){
	return 'R$' + new String(value).replace('.', ',');
}
```

### Função para deixar apenas a primeira letra em maiúsculo
#### **Código da função**
```
function (value){
const initcap = (s) => {
   return s.toLowerCase().replace(/(?:^|\s)[a-z]/g, function (m) {
      return m.toUpperCase();
   });
};

	return initcap(new String(value));
}
```