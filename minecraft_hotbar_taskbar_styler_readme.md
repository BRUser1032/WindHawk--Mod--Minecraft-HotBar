# Windhawk Mod — Minecraft Hotbar para Windows 11

Deixa a barra de tarefas do Windows 11 com o visual clássico da **hotbar do Minecraft**: ícones centralizados em slots, bandeja do sistema separada à direita e indicador de aplicativo aberto ajustado dentro do slot.

Configuração apresentada no canal **[@BitRizeBR](https://www.youtube.com/@BitRizeBR)** (YouTube), desenvolvida com o auxílio do **Claude.ai** (Anthropic).

---

## 📸 Demonstração

<img width="1359" height="767" alt="Demonstração do estilo Minecraft Hotbar" src="https://github.com/user-attachments/assets/bf5b3f75-be9a-4bf7-8e41-ed264ca8d556" />

---

## ℹ️ Sobre o Projeto

> **Nota:** Isto **não é um mod compilável**. É um arquivo de configuração (YAML) para colar no mod **Windows 11 Taskbar Styler**, do Windhawk.

Este repositório contém o código modificado a partir do tema *Minecraft Hotbar* (originalmente criado por **WasiXGamer** e publicado no guia de estilos do **Windows 11 Taskbar Styler** por **m417z**). O mod reorganiza, separa os elementos da barra de tarefas e aplica as texturas dos slots do Minecraft.

---

## 📋 Requisitos

| Item | Detalhe |
| :--- | :--- |
| **Windows** | Windows 11 (testado na 25H2, build 26200.9550, em 1360x768, 2 monitores) |
| **Windhawk** | [windhawk.net](https://windhawk.net) |
| **Mod principal** | **Windows 11 Taskbar Styler** (testado na v1.10) |
| **Esconder o botão Iniciar** | **[WindHawk--Mod--HideWindowsButton](https://github.com/BRUser1032/WindHawk--Mod--HideWindowsButton)** |
| **Fonte (opcional)** | `vivo Sans EN VF`. Sem ela, o Windows usará outra fonte padrão e os textos podem ficar com larguras variadas. |
| **Conexão de Internet** | Necessária para baixar as texturas dos slots em tempo real via `raw.githubusercontent.com` (veja em [Limitações](#-limitações)). |

> ⚠️ **Atenção:** **Não use** o mod *"Taskbar height and icon size"* junto com este tema. O README do tema original avisa que há conflito entre eles.

---

## 🚀 Instalação

1. No **Windhawk**, instale e ative o mod **Windows 11 Taskbar Styler**.
2. Abra as configurações do mod e entre no modo de edição de texto (**Textual mode**).
3. Apague todo o conteúdo existente e cole o conteúdo do arquivo `minecraft-hotbar-taskbar-styler.yaml`.
4. Salve as alterações.
5. Para remover o botão Iniciar da hotbar, instale e ative o mod **[WindHawk--Mod--HideWindowsButton](https://github.com/BRUser1032/WindHawk--Mod--HideWindowsButton)**.

---

## 🔄 Como Voltar ao Normal

Caso queira restaurar as configurações padrão ou se algo ficar instável:

1. Abra o **Textual mode** no mod Taskbar Styler.
2. Deixe apenas a linha abaixo e apague o resto:
   ```yaml
   theme: Minecraft_Hotbar
   ```
3. Ou, se preferir, simplesmente desative o mod **Taskbar Styler** no Windhawk.

---

## 🛠️ Alterações Realizadas em Relação ao Tema Original

Este projeto parte do tema original de **WasiXGamer** e aplica ajustes específicos de alinhamento, fonte e posicionamento dos elementos.

### Versão Atual

| Alteração | Antes | Depois | Status |
| :--- | :--- | :--- | :--- |
| **Slot do idioma (POR/PTB2)** | Margem direita `-1,0,-13,0` | `-1,0,-5,0` | A confirmar |
| **Slot do relógio** | Largura `auto` | `76` | A confirmar |
| **Texto da data** | Margem `3,9,7,-9` | Centralizado, margem `0,9,0,-9` | A confirmar |
| **Texto da hora** | Margem `6,-4,6,4` | Centralizado, margem `0,-4,0,4` | A confirmar |

* **Motivo das alterações:** No layout anterior, o slot do Wi-Fi ficava por cima da borda do slot de idioma (devido à margem direita negativa) e a data passava da borda esquerda do slot do relógio.
* **Dica de ajuste:** Se ainda houver sobreposição no idioma na sua resolução, tente `-4` ou `-3`. Se abrir um vão, volte para `-6`. No relógio, ajuste a largura em passos de 4 em 4.

### Versões Anteriores

| Alteração | Antes | Depois | Status |
| :--- | :--- | :--- | :--- |
| **Regras do tema** | Tema referenciado por nome | Regras coladas por extenso (`theme: ''`) | Funciona |
| **Ícones de texto e Wi-Fi/Volume/Bateria** | Fonte 30 | Fonte 24 | Funciona |
| **Chevron (`^`)** | Fonte 32 | Fonte 24 | Funciona |
| **Hora** | Fonte 15 | Fonte 13 | Funciona |
| **Data** | Fonte 13 | Fonte 11 | Funciona |
| **Idioma** | Fonte 16 | Fonte 13 | Funciona |
| **Bandeja do Sistema** | Coluna 2, alinhada à esquerda, colada na hotbar | Coluna 3, à direita, margem `0,0,8,0` | Funciona |
| **Indicador de app aberto (entalhe)** | Sem alinhamento vertical (fora do slot) | `VerticalAlignment=Bottom`, margem inferior `9` | Funciona (confirmado) |

> **Nota:** Os tamanhos de fonte foram definidos por tentativa e erro em uma tela de 1360x768. Em outras resoluções ou escalas de exibição do Windows, ajustes adicionais podem ser necessários.

---

## 📌 Pontos em Aberto

* **Hora e data em slots separados:** Não implementado. Ambos pertencem ao mesmo controle interno do Windows e o Taskbar Styler apenas estiliza elementos existentes, sem criar novos. Uma alternativa não testada é esconder a data (`Visibility=Collapsed` em `TextBlock#DateInnerTextBlock`) e manter apenas a hora em um slot de 55x55.
* **Ícone de Volume:** Apenas o ícone do Wi-Fi aparece no grupo de controle da bandeja. O arquivo YAML possui `Visibility=1` (`Collapsed`) em um dos ícones desse grupo (herdado do tema original). Não foi confirmado se este comportamento é intencional.
* **Formato de data curta:** Mudar o formato no Windows para `dd/MM/yy` reduz o tamanho do texto, mas pode impactar outros programas do sistema.

---

## ⚠️ Limitações

* **Dependência da Internet:** As texturas dos slots são carregadas diretamente de `raw.githubusercontent.com/ramensoftware/windows-11-taskbar-styling-guide`. Se o repositório mudar de local ou faltar conexão, os slots perderão o fundo estilizado.
* **Dependência de seletores internos do Windows:** O arquivo usa nomes de elementos XAML (`SystemTray.*`, `Taskbar.*`). Atualizações do Windows 11 podem alterar ou renomear esses elementos e quebrar partes do tema.
* **Ambiente de Teste:** Validado até o momento em apenas um ambiente específico: Windows 11 25H2 (build 26200.9550), resolução 1360x768 com 2 monitores.
* **Ocultador do Botão Iniciar:** O mod secundário de esconder o botão Iniciar também está sujeito a quebras após atualizações do sistema.

---

## 💬 Como Reportar um Problema

Ao abrir um *issue*, inclua as seguintes informações:

1. Versão e build do Windows (`winver`), resolução da tela e taxa de escala.
2. Versão do **Taskbar Styler** instalada.
3. Captura de tela (print) da barra de tarefas indicando o problema.
4. Trecho do arquivo YAML que você eventualmente alterou.

---

## 📜 Créditos e Licença

* **WasiXGamer:** Criador do tema original *Minecraft Hotbar*.
* **m417z:** Criador do Windhawk, do mod *Windows 11 Taskbar Styler* e mantenedor do guia de estilos.
* **BRUser1032 / BitRizeBR:** Desenvolvimento dos ajustes e customizações deste repositório.
* **Claude (Anthropic):** Assistência na análise e estruturação do código.

> **Aviso de Isenção e Licença:** Este projeto é um derivado do tema *Minecraft Hotbar*. Ajustar valores e regras não altera os direitos dos autores originais. Este projeto não possui afiliação oficial com o Windhawk ou seus autores.  
> Licença pendente de verificação: até que as licenças do tema original e do guia de estilos sejam formalmente declaradas, considere o uso deste repositório como "sem licença declarada".