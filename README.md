# AR Dungeon Pizza 🍕

Um jogo de RPG com Realidade Aumentada usando mapa hexagonal/octogonal estilo tabuleiro.

## 🎮 Como Usar

1. **Imprima o marcador Hiro** (arquivo `hiro.png`)
2. **Acesse o jogo**: [https://thalestol.github.io/pizzabox](https://thalestol.github.io/pizzabox)
3. **Permita o acesso à câmera** quando solicitado
4. **Aponte a câmera para o marcador impresso**
5. **Toque nos hexágonos** para selecioná-los

## 🗺️ Características do Mapa

### Layout Octogonal "Dungeon Pizza"
- **8x8 tiles** em formato octogonal
- **Coordenadas estilo Batalha Naval**: Linhas A-H, Colunas 1-8
- **Labels 3D** que aparecem ao redor do tabuleiro (como no jogo Batalha Naval)

### Tipos de Terreno (Azeitonas)
Baseado no conceito das "4 Azeitonas":

1. **Queimada** (Grass) - Verde: Áreas básicas
2. **Calabresa Duvidosa** (Stone) - Cinza: Áreas de pedra
3. **Só a Gema do Ovo Quebrado** (Water) - Azul: Áreas de água
4. **Alcaparra** (Mountain) - Cinza escuro: Montanhas

Também inclui:
- **Dirt** (Marrom): Áreas de terra

## 🔧 Correções Implementadas

### Problema 1: Labels não funcionando ✅ RESOLVIDO
- **Antes**: Labels 2D em HTML que não se alinhavam com o tabuleiro 3D
- **Agora**: Labels 3D renderizados como texto A-Frame que aparecem ao redor do tabuleiro, como no jogo Batalha Naval

### Problema 2: Viewport muito grande no mobile ✅ RESOLVIDO
- Ajustado viewport meta tag com `maximum-scale=1.0` e `user-scalable=no`
- Adicionado `position: fixed` no body para evitar scroll
- Canvas AR configurado para ocupar 100% da tela corretamente
- Melhoradas configurações do AR.js para mobile
- Adicionado bloqueio de zoom por pinch

## 🎯 Interação

- **Hover** sobre tile: Ilumina o tile
- **Click/Toque** em tile: Seleciona e mostra informação
- **Tile selecionado**: Fica branco e pulsa
- **Info mostrada**: Coordenada + Tipo de terreno

## 🛠️ Stack Tecnológica

- **AR.js 3.x** - Realidade Aumentada baseada na web
- **A-Frame 1.3.0** - Framework 3D/VR
- **Hiro Marker** - Sistema de rastreamento de marcador
- **Vanilla JavaScript** - Lógica do jogo

## 📱 Compatibilidade

- ✅ Chrome/Safari Mobile (iOS/Android)
- ✅ Chrome/Firefox Desktop
- ⚠️ Requer HTTPS ou localhost para acesso à câmera
- ⚠️ Melhor experiência em dispositivos mobile

## 🎨 Personalizações Possíveis

Edite o arquivo `index.html` para:

- Modificar cores dos terrenos (objeto `TERRAIN`)
- Ajustar tamanho do tabuleiro (`scale` attribute)
- Mudar tamanho dos tiles (`TILE_SIZE`)
- Adicionar novos tipos de terreno
- Modificar o layout octogonal

## 📖 Conceito do Jogo

Baseado nas anotações do projeto:
- Sistema de habilidades e pontos de vida
- Mapa em tempo real via AR
- Coordenadas para localização de personagens
- Temática de "Dungeon Pizza" com azeitonas

## 🚀 Deploy

Hospedado via GitHub Pages. Para atualizar:

```bash
git add .
git commit -m "Update game"
git push origin main
```

As mudanças aparecem automaticamente em alguns minutos.

## 📝 Notas de Desenvolvimento

- Os labels são criados dinamicamente via JavaScript
- O mapa octogonal é gerado removendo os cantos de um grid 8x8
- Cada tile tem propriedades de terreno, coordenadas e cor
- Sistema de seleção com feedback visual (pulsação)

---

**Desenvolvido com base nos sketches do caderno de design do projeto** 