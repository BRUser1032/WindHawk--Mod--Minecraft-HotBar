[minecraft_hotbar_taskbar_styler_readme.md](https://github.com/user-attachments/files/32878998/minecraft_hotbar_taskbar_styler_readme.md)
[minecraft_hotbar_taskbar_styler_readme.md](https://github.com/user-attachments/files/32878955/minecraft_hotbar_taskbar_styler_readme.md)
# Windhawk Mod — Minecraft Hotbar para Windows 11

Deixa a barra de tarefas do Windows 11 com o visual clássico da **hotbar do Minecraft**: ícones centralizados em slots, bandeja do sistema separada à direita e indicador de aplicativo aberto ajustado dentro do slot.

Configuração apresentada no canal **[@BitRizeBR](https://www.youtube.com/@BitRizeBR)** (YouTube), desenvolvida com o auxílio do **Claude.ai** (Anthropic).# Minecraft Hotbar para Windows 11 (Windhawk)

Tema para o Windhawk que transforma a barra de tarefas do Windows 11 no visual de uma hotbar do Minecraft: ícones centralizados em slots, bandeja do sistema destacada à direita e indicador de aplicativo aberto dentro de cada slot.

Esta configuração foi apresentada no canal [@BitRizeBR](https://youtube.com/@BitRizeBR) e ajustada para corrigir sobreposições de layout e alinhamentos em resoluções menores.

> **Nota:** Este projeto não é um mod executável ou compilável. É um arquivo de configuração em formato YAML (`minecraft-hotbar-taskbar-styler.yaml`) para ser colado nas configurações do mod **Windows 11 Taskbar Styler**.

---

## Demonstração

![Demonstração da Hotbar do Minecraft na barra de tarefas](https://github.com/user-attachments/assets/bf5b3f75-be9a-4bf7-8e41-ed264ca8d556)

---

## Requisitos

| Item | Detalhe |
| :--- | :--- |
| **Sistema** | Windows 11 (testado na versão 25H2, build 26200.9550, em 1360x768 com 2 monitores) |
| **Windhawk** | Gerenciador de mods instalado ([windhawk.net](https://windhawk.net/)) |
| **Mod Base** | [Windows 11 Taskbar Styler](https://windhawk.net/mods/windows-11-taskbar-styler) (v1.10+) |
| **Ocultar Botão Iniciar** | [WindHawk--Mod--HideWindowsButton](https://github.com/BRUser1032/WindHawk--Mod--HideWindowsButton) (recomendado para remover o Iniciar da barra) |
| **Fonte (Opcional)** | *vivo Sans EN VF* (evita alterações imprevistas na largura do texto) |
| **Conexão** | Necessária para carregar as texturas dos slots diretamente do GitHub |

**Aviso:** Não utilize este tema junto com o mod *Taskbar height and icon size*. Eles entram em conflito e quebram a interface.

---

## Instalação

1. No Windhawk, instale o mod **Windows 11 Taskbar Styler**.
2. Abra as configurações do mod e ative o modo de edição de texto (**Textual mode**).
3. Apague o conteúdo padrão e cole o código contido em `minecraft-hotbar-taskbar-styler.yaml`.
4. Salve as alterações.
5. *(Opcional)* Instale e ative o mod **HideWindowsButton** para ocultar o botão Iniciar.

### Restaurar o Padrão

Caso queira desfazer as alterações, abra o **Textual mode** nas configurações do mod, substitua todo o texto pela linha abaixo e salve (ou simplesmente desative o mod):

```yaml
theme: Minecraft_Hotbar
```

---

## O que foi alterado

Este repositório toma como base o tema **Minecraft Hotbar**, criado originalmente por **WasiXGamer**, aplicando correções de espaçamento e alinhamento.

### Alterações da Versão Atual

| Elemento / Ajuste | Antes | Depois | Status |
| :--- | :--- | :--- | :--- |
| **Slot do idioma** (`POR`/`PTB2`) | Margem `-1,0,-13,0` | Margem `-1,0,-5,0` | A confirmar |
| **Slot do relógio** | Largura `auto` | Largura `76` | A confirmar |
| **Texto da data** | Margem `3,9,7,-9` | Centralizado, margem `0,9,0,-9` | A confirmar |
| **Texto da hora** | Margem `6,-4,6,4` | Centralizado, margem `0,-4,0,4` | A confirmar |

*Motivo dos ajustes:* O ícone do Wi-Fi estava se sobrepondo à borda do slot de idioma devido à margem negativa excessiva, e a data passava dos limites do slot do relógio em telas 1360x768.

*Dica de ajuste fino:* Se o idioma ainda sobrepor, tente margem `-4` ou `-3`. Se criar um vão, volte para `-6`. No relógio, ajuste a largura de 4 em 4 pixels.

### Alterações Anteriores

* **Regras do tema:** Declaradas por extenso no próprio YAML (`theme: ''`) em vez de apenas referenciar o tema por nome.
* **Tamanhos de fonte:** Reduzidos para caber adequadamente nos slots (ícones/Wi-Fi de `30` para `24`; hora de `15` para `13`; data de `13` para `11`; idioma de `16` para `13`).
* **Bandeja do sistema:** Movidinha da coluna 2 (colada na hotbar) para a coluna 3, alinhada à direita, com margem `0,0,8,0`.
* **Indicador de app aberto:** Adicionado `VerticalAlignment=Bottom` e margem inferior `9` para fixar o marcador corretamente dentro do slot.

---

## Pontos em Aberto e Limitações

* **Data e hora em slots separados:** Não implementado. O Windows trata data e hora dentro do mesmo controle XAML e o Taskbar Styler apenas estiliza elementos existentes. Uma alternativa é ocultar a data (`Visibility=Collapsed` em `TextBlock#DateInnerTextBlock`) e manter apenas a hora em um slot de 55x55.
* **Ícone de volume:** O YAML herdou uma regra de visibilidade (`Visibility=1`) que oculta alguns ícones da bandeja, mantendo apenas o Wi-Fi visível.
* **Dependência de internet:** As texturas são baixadas de `raw.githubusercontent.com`. Sem conexão, os slots perdem o fundo.
* **Nomes internos do Windows:** Atualizações do Windows 11 podem alterar a estrutura interna de elementos XAML (`SystemTray.*`, `Taskbar.*`), o que pode quebrar o layout até que o YAML seja atualizado.

---

## Como Reportar Problemas

Ao abrir uma *issue*, informe:

1. Versão e build do Windows (`winver`), resolução e escala da tela.
2. Versão do mod *Windows 11 Taskbar Styler*.
3. Print da barra com o erro destacado.
4. Trecho do YAML modificado, se houver.

---

## Créditos e Licença

* **WasiXGamer** — Tema original *Minecraft Hotbar*.
* **m417z** — Desenvolvimento do Windhawk, do mod *Windows 11 Taskbar Styler* e publicação do guia de estilos.
* **BRUser1032 / BitRize** — Ajustes de margens, alinhamentos e organização do repositório.

*Este projeto é uma derivação do tema original e não possui vínculo oficial com os desenvolvedores do Windhawk.*

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
