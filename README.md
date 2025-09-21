# Projeto de Engenharia de Software: Portfólio Dinâmico Pessoal

Este repositório documenta o desenvolvimento de um portfólio web dinâmico, criado como projeto para a disciplina de Engenharia de Software. O objetivo é construir uma plataforma centralizada para a apresentação de competências, projetos e informações profissionais.

## Objetivo do Projeto

O objetivo principal deste trabalho é projetar e desenvolver uma aplicação web moderna e responsiva que sirva como um portfólio profissional. A plataforma deverá carregar dinamicamente os projetos de um arquivo de dados, permitindo que o conteúdo seja atualizado de forma simples e eficiente, sem a necessidade de alterar o código-fonte da aplicação.

## O Problema a ser Resolvido

A gestão de uma identidade profissional digital é um processo fragmentado. Profissionais e estudantes mantêm informações em diversas plataformas (LinkedIn, GitHub, currículos em PDF), o que torna a tarefa de atualizar e apresentar projetos de forma consistente uma atividade manual, repetitiva e propensa a erros. A falta de uma plataforma central e de fácil manutenção é o problema central que esta solução visa resolver.

## Tipo de Solução

A solução será uma **Aplicação Web Dinâmica** com uma arquitetura cliente-servidor bem definida:

* **Frontend (Cliente):** Desenvolvido com **HTML5, CSS3 e JavaScript**, será responsável pela apresentação visual da interface. O foco será em um design limpo, moderno, responsivo e que proporcione uma excelente experiência de usuário em qualquer dispositivo (desktop ou mobile).
* **Backend (Servidor):** Um servidor leve construído em **Python** utilizando o microframework **Flask**. Será responsável pela lógica da aplicação, como carregar os dados dos projetos, processar o formulário de contato e servir as páginas web.
* **Fonte de Dados:** Um arquivo estruturado em formato **JSON (`projetos.json`)** armazenará todas as informações dos projetos (título, descrição, tecnologias, links). Esta abordagem separa os dados da apresentação, o que é uma prática fundamental da engenharia de software.

## Requisitos da Aplicação

### Requisitos Funcionais (RF)

| ID   | Descrição                                                                          |
| :--- | :----------------------------------------------------------------------------------- |
| RF01 | O sistema deve exibir as informações pessoais do proprietário (biografia, foto, links para redes sociais). |
| RF02 | O sistema deve carregar e exibir dinamicamente a lista de projetos a partir de um arquivo de dados JSON. |
| RF03 | O sistema deve exibir cada projeto com seu título, descrição, imagem de capa e tecnologias associadas. |
| RF04 | O sistema deve permitir que um visitante filtre os projetos exibidos com base nas tecnologias (tags). |
| RF05 | O sistema deve apresentar um formulário de contato com os campos "Nome", "Email" e "Mensagem". |
| RF06 | O sistema deve validar os campos do formulário no lado do cliente (ex: verificar se o email tem formato válido). |
| RF07 | O sistema deve processar o envio do formulário no backend, salvando a mensagem em um arquivo local ou enviando uma notificação. |

### Requisitos Não Funcionais (RNF)

| ID   | Categoria       | Descrição                                                                      |
| :--- | :-------------- | :----------------------------------------------------------------------------- |
| RNF01| Usabilidade     | A navegação do site deve ser clara, intuitiva e acessível.                     |
| RNF02| Desempenho      | A página principal, incluindo os projetos, deve ter um tempo de carregamento inferior a 3 segundos. |
| RNF03| Responsividade  | O layout do site deve se adaptar de forma fluida a diferentes tamanhos de tela, como desktops, tablets e smartphones. |
| RNF04| Manutenibilidade| A adição de um novo projeto ao portfólio deve ser possível apenas editando o arquivo de dados JSON, sem alterar o código do backend ou frontend. |
| RNF05| Compatibilidade | O site deve ser renderizado corretamente nas versões mais recentes dos navegadores Chrome, Firefox, Safari e Edge. |

## (v) Diagrama de Caso de Uso

O diagrama abaixo ilustra as principais interações de um visitante com o sistema de portfólio.

```mermaid
graph TD
    A(Visitante) --> |1. Acessa o site| B{Visualizar Portfólio}
    B --> C{Exibir Informações Pessoais}
    B --> D{Carregar Projetos do JSON}
    
    A --> |2. Clica em um filtro de tecnologia| E{Filtrar Projetos}
    E --> D
    
    A --> |3. Preenche e envia| F{Enviar Mensagem de Contato}
    F --> G{Validar Formulário}
    G -- Válido --> H{Processar no Backend}
    
    subgraph "Sistema de Portfólio Dinâmico"
        B
        C
        D
        E
        F
        G
        H
    end

    style A fill:#f9f,stroke:#333,stroke-width:2px
