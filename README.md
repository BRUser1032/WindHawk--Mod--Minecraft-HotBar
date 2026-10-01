# Minecraft Hotbar para a barra de tarefas do Windows 11 (Windhawk)

Deixa a barra de tarefas do Windows 11 com visual de **hotbar do Minecraft**: ícones centralizados em slots, bandeja do sistema separada à direita e indicador de app aberto dentro do slot.

Configuração apresentada no canal **@BitRizeBR** (YouTube), feita com ajuda do Claude (IA).

> Isto **não é um mod compilável**. É um arquivo de configuração (YAML) para colar no mod **Windows 11 Taskbar Styler**, do Windhawk.

---

## Requisitos

| Item | Detalhe |
|---|---|
| Windows | Windows 11 (testado na 25H2, build 26200.9550, em 1360x768, 2 monitores) |
| Windhawk | [windhawk.net](https://windhawk.net) |
| Mod principal | **Windows 11 Taskbar Styler** (testado na v1.10) |
| Esconder o botão Iniciar | [WindHawk--Mod--HideWindowsButton](https://github.com/BRUser1032/WindHawk--Mod--HideWindowsButton) |
| Fonte (opcional) | `vivo Sans EN VF`. Sem ela o Windows usa outra fonte e o texto pode ficar com outra largura |
| Internet | As texturas dos slots são baixadas de `raw.githubusercontent.com` (veja "Limitações") |

**Não use** o mod "Taskbar height and icon size" junto com este tema: o README do tema original avisa que conflita.

---

## Instalação

1. No Windhawk, instale o mod **Windows 11 Taskbar Styler**.
2. Abra as configurações do mod e entre no modo de edição de texto (**Textual mode**).
3. Apague o conteúdo e cole o conteúdo de `minecraft-hotbar-taskbar-styler.yaml`.
4. Salve. Se algo ficar instável, veja "Como voltar ao normal".
5. Instale e ative o mod de esconder o botão Iniciar (link na tabela acima), se quiser o Iniciar fora da hotbar.

### Como voltar ao normal

No Textual mode, coloque apenas:

```yaml
theme: Minecraft_Hotbar
```

e deixe o resto vazio (estado original do tema), ou desative o mod Taskbar Styler.

---

## O que foi alterado em relação ao tema original

O tema **Minecraft Hotbar** é de **WasiXGamer**, publicado no guia de estilos do Taskbar Styler. Este repositório parte dele e altera o seguinte:

### Versão atual

| Alteração | Antes | Depois | Status |
|---|---|---|---|
| Botão de controle (Wi-Fi/volume/bateria): margem esquerda (regra nova em `SystemTray.OmniButton#ControlCenterButton`) | sem regra | `Margin=9,0,0,0` | **A confirmar** |
| Slot do relógio: largura | `auto` | `84` | **A confirmar** (a largura 76 foi aplicada, mas deixava a data apertada) |
| Texto da data: alinhamento e margem | margem `3,9,7,-9` | centralizado, margem `0,9,0,-9` | Funciona (confirmado no print) |
| Texto da hora: alinhamento e margem | margem `6,-4,6,4` | centralizado, margem `0,-4,0,4` | Funciona (confirmado no print) |

**Sobreposição do slot do idioma (POR/PTB2).** No print, o slot do Wi-Fi ficava ~9 px por cima da borda do slot do idioma. Mudar a margem do próprio slot do idioma (de `-13` para `-5`) **não resolveu**: comparando os dois prints, o espaçamento entre os slots não mudou, só a posição do desenho dentro do slot (cerca de 2 px). A margem do idioma voltou ao valor original do tema (`-13`). A correção atual atua no botão vizinho (Wi-Fi), por margem, e **ainda precisa ser confirmada**.

Se o espaço ficar maior ou menor que o ideal, ajuste o `9` de 1 em 1. No relógio, ajuste a largura de 4 em 4.

### Versões anteriores

| Alteração | Antes | Depois | Status |
|---|---|---|---|
| Regras do tema | tema referenciado por nome | regras coladas por extenso (`theme: ''`) | Funciona |
| Ícones de texto e Wi-Fi/volume/bateria | fonte 30 | 24 | Funciona |
| Chevron (`^`) | fonte 32 | 24 | Funciona |
| Hora | fonte 15 | 13 | Funciona |
| Data | fonte 13 | 11 | Funciona |
| Idioma | fonte 16 | 13 | Funciona |
| Bandeja | coluna 2, alinhada à esquerda, colada na hotbar | coluna 3, à direita, margem `0,0,8,0` | Funciona |
| Indicador de app aberto (entalhe) | sem alinhamento vertical, ficava fora do slot | `VerticalAlignment=Bottom`, margem inferior `9` | Funciona (confirmado visualmente) |

Os tamanhos de fonte foram escolhidos por tentativa e erro em uma tela 1360x768. **Em outra resolução ou escala, podem precisar de ajuste.**

---

## Pontos em aberto

- **Hora e data em slots separados:** não implementado. Os dois textos pertencem ao mesmo controle do Windows e o Styler só estiliza elementos existentes, não cria novos. Uma alternativa é esconder a data (`Visibility=Collapsed` em `TextBlock#DateInnerTextBlock`) e deixar só a hora num slot de 55x55. Não testado.
- **Volume:** só o ícone do Wi-Fi aparece no grupo de controle da bandeja. O YAML tem `Visibility=1` (Collapsed) em um dos ícones desse grupo, herdado do tema. Não está confirmado se isso é intencional.
- **Data curta:** mudar o formato para `dd/MM/yy` no Windows encurtaria o texto, mas afeta outros programas.

---

## Limitações

- **Depende de internet e de outro repositório:** as texturas dos slots são carregadas de `raw.githubusercontent.com/ramensoftware/windows-11-taskbar-styling-guide`. Se o arquivo mudar de lugar ou a conexão falhar, os slots perdem o fundo.
- **Depende de nomes internos do Windows:** os alvos usam nomes de elementos XAML (`SystemTray.*`, `Taskbar.*`). Uma atualização do Windows pode renomear ou reorganizar elementos e quebrar partes do visual. O Taskbar Styler é atualizado pelo autor, mas o YAML deste repositório só é ajustado quando alguém testa.
- **Testado em uma máquina:** Windows 11 25H2 (26200.9550), 1360x768, 2 monitores.
- **O mod de esconder o Iniciar também pode quebrar** após atualizações (veja o repositório dele).

---

## Como reportar um problema

Abra um issue com:

1. Versão e build do Windows (`winver`), resolução e escala.
2. Versão do Taskbar Styler.
3. Um print da barra, com o que está errado destacado.
4. Se possível, o trecho do YAML que você alterou.

---

## Créditos e licença

- **WasiXGamer** — tema original **Minecraft Hotbar**.
- **m417z** — Windhawk, mod Windows 11 Taskbar Styler e o guia de estilos onde o tema e as texturas estão publicados.
- **BRUser1032 / BitRize** — ajustes deste repositório.
- **Claude (Anthropic)** — assistência na análise e nos ajustes.

Este material é **derivado** do tema Minecraft Hotbar. Ajustar valores e regras não remove os direitos dos autores originais.

**Licença: pendente de verificação.** Este repositório ainda não declara licença, e a licença do tema original e do guia de estilos não foi verificada. Até lá, trate o uso como "sem licença declarada".

Este projeto não é afiliado ao Windhawk nem a seus autores.
