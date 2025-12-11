# 🏛️ Simulador de Tramitação Legislativa (Interface Visual)

![HTML5](https://img.shields.io/badge/HTML5-E34F26?style=for-the-badge&logo=html5&logoColor=white)
![CSS3](https://img.shields.io/badge/CSS3-1572B6?style=for-the-badge&logo=css3&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black)

> **Projeto Acadêmico | SENAI Roberto Simonsen** > *Disciplina: Linguagem de Marcação*

Este projeto é uma evolução visual de exercícios de lógica de programação. Trata-se de uma **Single Page Application (SPA)** simples que simula o processo de aprovação de uma lei no Brasil, utilizando uma interface gráfica interativa (Dark Mode) em vez de apenas logs no console.

---

## 🚀 Funcionalidades da Interface

Diferente da versão em terminal, este projeto foca na **Experiência do Usuário (UI/UX)**:

* **📺 Painel de Status Dinâmico**: O estado atual da lei (ex: "Em Votação", "Sancionada") muda de cor e texto visualmente.
* **botoes Interativos**: Os botões de decisão ("Aprovar", "Rejeitar", "Vetar") são criados e removidos automaticamente pelo JavaScript dependendo da etapa atual.
* **📜 Log Visual**: Um histórico de tramitação aparece na tela lateral, registrando cada passo com data e hora.
* **🎨 Design Responsivo**: Layout construído com **CSS Grid** e **Flexbox**.

---

## 🧠 Tecnologias e Conceitos Aplicados

O foco deste repositório é demonstrar a **Manipulação do DOM** e a estruturação de código Orientado a Objetos no Front-end.

### 1. JavaScript (Engine)
* **Manipulação do DOM**: Uso de `document.createElement`, `appendChild` e `innerHTML` para desenhar a tela via código.
* **Programação Orientada a Objetos (POO)**: Utilização de `class LegislativeEngine` para encapsular toda a regra de negócio.
* **State Pattern**: Gerenciamento de estados complexos para controlar o fluxo da aplicação.

### 2. CSS3 (Estilização)
* **CSS Variables (`:root`)**: Para gerenciamento fácil de paleta de cores (Tema Dark).
* **CSS Grid**: Utilizado para dividir a tela entre o "Painel Principal" e o "Log de Eventos".
* **Animações**: Feedback visual nos botões e mudanças de estado.

### 3. HTML5 (Estrutura)
* Uso de tags semânticas e estrutura limpa, servindo apenas como "container" para o JavaScript atuar.

---

## 📂 Como testar o projeto

Como é um projeto Front-end estático (apenas HTML/CSS/JS), não requer instalação de nada.

1.  Baixe o arquivo `simuladolegislacao.html`.
2.  Dê um **duplo clique** para abrir no seu navegador padrão (Chrome, Edge, Firefox).
3.  Interaja com os botões para ver a lei tramitar.

---

## 📸 Exemplo de Código

Abaixo, um trecho de como o JavaScript cria os botões dinamicamente na tela:

```javascript
// Método que gera os botões baseado nas opções do estado atual
createButtons(options) {
    this.ui.buttons.innerHTML = ''; // Limpa botões antigos

    options.forEach(opt => {
        const btn = document.createElement('button');
        btn.innerText = opt.label;
        
        // Adiciona evento de clique
        btn.onclick = () => {
            this.transitionTo(opt.next);
        };
        
        this.ui.buttons.appendChild(btn); // Coloca na tela
    });
}
