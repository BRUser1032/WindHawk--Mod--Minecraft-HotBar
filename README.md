
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
