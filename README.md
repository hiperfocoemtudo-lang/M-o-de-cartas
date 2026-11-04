# Mão de Cartas

Applet para o **Linux Mint Cinnamon** que mostra aplicativos fixados e janelas abertas como cartas de Inscryption. A mão aparece na parte inferior da tela e pode ser mostrada ou escondida pelo botão no painel.

- Clique em uma carta para abrir o aplicativo ou trazer sua janela para frente.
- Clique com o botão direito para abrir uma nova janela ou fechar a janela representada pela carta.
- Várias janelas do mesmo aplicativo aparecem empilhadas. Ao passar o mouse, as cartas sobem e se separam.
- Ajuste o tamanho, a sobreposição e o formato da mão nas configurações da applet.

## Instalação

Extraia o pacote ou clone o repositório. Abra um terminal na pasta que contém este README e execute:

```bash
bash instalar.sh
```

O instalador solicita a senha de administrador para instalar as dependências pelo APT e instala a applet para o seu usuário. Depois, abra **Applets** pelo menu do painel, procure **Mão de cartas** e adicione ao painel. Se estiver atualizando uma applet já ativa, remova-a do painel e adicione-a novamente para carregar o código atualizado.

A versão 1.1.0 foi desenvolvida e testada no **Linux Mint 22.3 Cinnamon**. O instalador requer Cinnamon 6.0 ou posterior e Python 3.9 ou posterior. O funcionamento em outras versões do Cinnamon depende das bibliotecas disponíveis na distribuição.

## Como as cartas são criadas

Na primeira vez que um aplicativo aparece na dock ou é selecionado no editor, a applet solicita uma carta padrão com o nome e o ícone do aplicativo. Ela prefere a versão monocromática do ícone quando disponível e o centraliza em 50%. O modelo Leshy recebe ataque, vida, custos, habilidades e adornos aleatórios. O resultado fica salvo no computador.

Em **Configurar → Escolher aplicativos e imagens das cartas…**, selecione um aplicativo para escolher uma imagem pronta ou abrir **Gerar imagem**. O editor mostra as alterações na prévia, permite ajustar o tamanho da imagem central e grava a carta com **Salvar carta**. Imagens personalizadas têm prioridade sobre os padrões automáticos.

A geração e a prévia completa usam o servidor do generator.cards. O nome, as imagens usadas e as opções visuais são enviados a esse serviço para renderizar a carta. É necessário acesso à internet para gerar novas imagens. A dock e as cartas já salvas funcionam offline. [Generator.cards](https://generator.cards/)

## Dependências

| Dependência | Função |
| --- | --- |
| `cinnamon` | Painel e integração com as janelas |
| `python3`, `python3-gi` | Execução do editor, do instalador e do gerador em segundo plano |
| `gir1.2-gtk-3.0`, `gir1.2-gdkpixbuf-2.0`, `gir1.2-glib-2.0` | Interface gráfica, imagens e integração com a sessão |
| `gir1.2-webkit2-4.1` | Interface do editor de cartas |
| `gir1.2-clutter-1.0`, `gir1.2-cogl-1.0` | Texturas, animação e interação da dock |
| `ca-certificates` | Conexão HTTPS com o gerador |

O APT instala também as dependências indiretas. O instalador usa Bash e sudo. Os arquivos JavaScript, CSS e fontes usados pelo editor acompanham o código. [Lista detalhada de dependências](DEPENDENCIAS-Mao-de-cartas.md)

## Código e créditos

A pasta `mao-de-cartas@local/` contém o código da applet, os editores em Python, a interface do gerador e as configurações padrão. Preferências, imagens pessoais e cartas geradas nesta máquina ficam fora do pacote.

A integração incorpora arquivos da interface do generator.cards. A arte original de Inscryption é de Daniel Mullins e o gerador foi criado por vladde. A licença de redistribuição do conjunto de recursos incorporados ainda precisa ser confirmada antes de tornar o repositório público. [Créditos do pacote](mao-de-cartas@local/GERADOR-CREDITOS.txt) · [Créditos do gerador](https://generator.cards/credits)
