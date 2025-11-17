# Projeto: Sistemas de Recomendação Explicáveis (XRS) com User-KNN

Este repositório contém o material didático (Jupyter Notebook) desenvolvido para a Fase 2 do projeto da disciplina **SCC0284/SCC5966 - Sistemas de Recomendação** (ICMC-USP, 2º Sem/2025).

**Alunos:**
* Victor Silva Botelho (N° USP: 15645421)
* João Pedro Barbosa Madeira (N° USP: 13683038)

**Professor:** Marcelo G. Manzato

---

## 🎯 O Problema: A "Caixa-Preta" dos Sistemas de Recomendação

A maioria dos sistemas de recomendação (SR) funciona como uma "caixa-preta": eles sugerem um item (um filme, uma música, um produto), mas não explicam *por que* o usuário deveria gostar dele. Essa falta de transparência gera desconfiança e reduz a adoção das sugestões.

O objetivo deste projeto é criar um material didático em português que demonstre como construir um **Sistema de Recomendação Explicável (XRS)**.

## 💡 A Solução: Explicação por "Vizinhos Similares"

Este notebook (`entrega2.ipynb`) implementa uma recomendação explicável usando a técnica de **Filtragem Colaborativa Baseada em Usuário (User-Based KNN)**.

Em vez de apenas mostrar o filme recomendado, nós "abrimos a caixa-preta" e geramos uma explicação baseada na própria lógica do algoritmo:

> "Recomendamos este filme para você porque **usuários com gostos parecidos com o seu** (seus 'vizinhos') também gostaram dele."



[Image of User-Based Collaborative Filtering]


## 🛠️ Como Funciona

O notebook é dividido em duas partes principais:

1.  **Geração da Recomendação:**
    * Utilizamos a biblioteca `CaseRecommender` para treinar um modelo `UserKNN` com o dataset **MovieLens 100k**.
    * O modelo gera um ranking de filmes recomendados para um usuário-alvo (ex: Usuário 1).

2.  **Geração da Explicação:**
    * Para explicar a recomendação principal, usamos `Pandas` e `Scikit-learn` para "recriar" a lógica do algoritmo.
    * Calculamos a matriz completa de **similaridade de cosseno** entre todos os usuários.
    * Identificamos os 5 "vizinhos" (usuários) mais similares ao nosso usuário-alvo.
    * Verificamos quais desses vizinhos avaliaram bem (nota 4 ou 5) o filme recomendado.
    * A explicação é gerada em linguagem natural usando essa "prova".

## 🚀 Como Executar

Este notebook foi projetado para rodar perfeitamente no **Google Colab**.

1.  Faça o upload do arquivo `entrega2.ipynb` para o Google Colab.
2.  Execute as células em ordem, de cima para baixo.

* **Célula 1 (Setup):** Instala as bibliotecas (`CaseRecommender`) e baixa o dataset MovieLens 100k.
* **Células 2-9:** Carregam os dados, treinam o modelo, geram a recomendação e, por fim, constroem e exibem a explicação.

## 📦 Requisitos

O notebook instala automaticamente suas próprias dependências via `pip`:
* `CaseRecommender`
* `numpy` (travado na versão `<2.0` para ser compatível com o CaseRecommender)
* `pandas` (dependência do CaseRecommender)
* `scikit-learn` (dependência do CaseRecommender)

## 📈 Exemplo de Saída

Ao final da execução do notebook, você verá a recomendação e sua explicação:
