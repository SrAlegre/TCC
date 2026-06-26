# Configuração do Ambiente LaTeX no VS Code (Windows) 📄🚀

Este guia prático foi criado para orientar o passo a passo da instalação e configuração de um ambiente de desenvolvimento completo para LaTeX utilizando o **Visual Studio Code** no sistema operacional Windows.

O conteúdo deste repositório foi baseado nas instruções detalhadas do vídeo:  
▶️ **[Como Instalar LaTeX no Windows e Usar no VS Code | Tutorial Completo](https://www.youtube.com/watch?v=OVWmg0hhLFY)** (Canal: *NegronDev*)

---

## 🛠️ Requisitos e Downloads

Para que o ambiente funcione corretamente, permitindo que você escreva o código em LaTeX e veja o PDF atualizado em tempo real na tela, você precisará baixar as seguintes ferramentas:

1. **[Visual Studio Code (VS Code)](https://code.visualstudio.com/)**: O editor base onde o código será escrito.
2. **[Extensão LaTeX Workshop](https://marketplace.visualstudio.com/items?itemName=James-Yu.latex-workshop)**: Extensão do VS Code que traz o suporte nativo ao LaTeX.
3. **[MiKTeX (basic-miktex-25.12-x64.exe)](https://miktex.org/download)**: O sistema compilador responsável por transformar o código em um arquivo PDF.
4. **[Strawberry Perl (strawberry-perl-5.42.2.1-64bit.msi)](https://strawberryperl.com/)**: Ferramenta auxiliar necessária para garantir o funcionamento correto dos scripts de compilação automática no Windows.

---

## 🏁 Passo a Passo de Instalação e Configuração

### Passo 1: Instalação do VS Code e da Extensão
1. Baixe e instale o **Visual Studio Code** se ainda não o tiver. *(Dica: marque as caixas de contexto durante a instalação para facilitar a abertura de pastas no Windows).*
2. Abra o VS Code e acesse a aba de **Extensões** no menu lateral esquerdo (ou use o atalho `Ctrl + Shift + X`).
3. Pesquise por `LaTeX Workshop` (ou clique no link de download acima).
4. Clique no botão **Install** (Instalar) na opção desenvolvida por *James Yu*.

### Passo 2: Instalação e Atualização do MiKTeX
1. Baixe e execute o instalador do **MiKTeX** (`basic-miktex-25.12-x64.exe`).
2. Aceite os termos de licença e avance mantendo as opções e diretórios padrões recomendados.
3. **Configuração pós-instalação (Muito Importante):** * Procure por **MiKTeX Console** no menu iniciar do seu Windows e abra o aplicativo.
   * No menu lateral esquerdo, clique na opção **Updates** (Atualizações).
   * Clique para verificar e instale todas as atualizações de pacotes disponíveis. Aguarde o processo terminar completamente antes de fechar.

### Passo 3: Instalação do Strawberry Perl
1. Baixe e execute o instalador do **Strawberry Perl** (`strawberry-perl-5.42.2.1-64bit.msi`).
2. *Nota:* Se o navegador ou o Windows exibir um aviso de proteção ao baixar, clique nos três pontinhos e selecione "Manter" ou "Executar assim mesmo".
3. Siga o assistente de instalação padrão clicando em avançar até concluir. Libere permissão de administrador quando o Windows solicitar.

### Passo 4: Reinicialização do Sistema
* **Obrigatório:** Salve todos os seus trabalhos e **reinicie o computador**. Isso é essencial para que o Windows e o VS Code reconheçam os novos caminhos (variáveis de ambiente) do MiKTeX e do Perl que acabaram de ser instalados.

---

## 💻 Como Utilizar no Dia a Dia

1. **Compilação Automática:** Toda vez que você editar um arquivo `.tex` e salvá-lo (`Ctrl + S`), a extensão chamará o MiKTeX em segundo plano para compilar o documento.
2. **Download de Pacotes Automático:** Se você usar um comando como `\usepackage{...}` para importar um pacote que ainda não está no seu computador, uma pequena janela do MiKTeX surgirá na tela. Basta clicar em **Install** para baixar e aplicar o pacote automaticamente.
3. **Visualizar o PDF Lado a Lado:** * No canto superior direito do VS Code, procure e clique no ícone que se parece com uma **lupinha em cima de uma folha** (*View LaTeX PDF*).
   * O PDF renderizado abrirá em uma aba dividida ao lado do seu código, sendo atualizado instantaneamente a cada vez que você salvar o arquivo.

---

## 🛠️ Comandos Úteis para Compilação Manual

Embora a extensão LaTeX Workshop já faça todo o processo automaticamente, em alguns casos (como depuração de erros ou compilação em servidores) pode ser útil executar os comandos manualmente no terminal. Abaixo estão os principais:

| Comando | Descrição |
|---------|-----------|
| `pdflatex main.tex` | Compila o arquivo `main.tex` diretamente para um PDF. Gera arquivos auxiliares (`.aux`, `.log`, `.toc`, etc.) que serão usados nas próximas etapas. |
| `biber main` | Processa as referências bibliográficas (quando você usa `\usepackage{biblatex}`). Leia o arquivo `.bcf` gerado pelo `pdflatex` e cria o arquivo `.bbl` com as citações formatadas. |
| `latexmk -CA` | Limpa **todos** os arquivos auxiliares gerados pelas compilações (`.aux`, `.log`, `.bbl`, `.blg`, `.toc`, `.out`, etc.), deixando apenas o `.tex` e o PDF. Útil para forçar uma compilação do zero ou reduzir bagunça na pasta. |

### 📌 Ordem típica para compilar um documento com bibliografia

Se precisar compilar manualmente (sem a extensão), a ordem geral é:

1. `pdflatex main.tex`        *(primeira passagem)*
2. `biber main`               *(processa as referências)*
3. `pdflatex main.tex`        *(segunda passagem para resolver citações)*
4. `pdflatex main.tex`        *(terceira passagem para atualizar sumário e referências cruzadas)*

Após esses passos, o PDF final estará completo e atualizado.

---

*Documento criado para registro das configurações de ambiente LaTeX.*