# AR Dungeon Pizza 🍕

Um jogo de RPG com Realidade Aumentada usando mapa hexagonal/octogonal estilo tabuleiro.

## 🎮 Como Usar

1. **Imprima o marcador Hiro** (arquivo `hiro.png`)
2. **Acesse o jogo**: [https://thalestol.github.io/pizzabox](https://thalestol.github.io/pizzabox)
3. **Permita o acesso à câmera** quando solicitado
4. **Aponte a câmera para o marcador impresso**
5. **Toque diretamente nos tiles** para selecioná-los
6. **Use os botões no canto superior direito** para adicionar e mover peças de pizza

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
5. **Dirt** (Marrom): Áreas de terra

## 🔧 Correções Implementadas

### Problema 1: Labels não funcionando ✅ RESOLVIDO
- **Antes**: Labels 2D em HTML que não se alinhavam com o tabuleiro 3D
- **Agora**: Labels 3D renderizados como texto A-Frame que aparecem ao redor do tabuleiro, como no jogo Batalha Naval

### Problema 2: Viewport muito grande no mobile ✅ RESOLVIDO
- **Canvas agora usa `100vw` e `100vh`** com `position: fixed`
- **Força o canvas a ocupar a tela toda** sem espaços ou offsets
- **Previne scroll e zoom indesejados** em dispositivos móveis
- **Esconde elementos de debug do AR.js** que causavam problemas de layout

### Problema 3: Controle por cursor central (não desejado) ✅ RESOLVIDO
- **Antes**: Usava um cursor no centro da tela que se movia com a câmera
- **Agora**: Implementado **raycasting baseado em toque direto**
  - Toque exatamente onde você quer interagir
  - Funciona com touch events nativos do mobile
  - Usa THREE.js Raycaster para detectar o tile tocado
  - Não é mais afetado pelo movimento da câmera

## 🍕 Peças de Pizza (Personagens)

Agora você pode adicionar e mover personagens no tabuleiro!

### Como Funciona:
1. **Toque no botão "🍕 Adicionar Pizza"** no canto superior direito
2. **Toque em um tile** onde deseja colocar a peça
3. **Uma fatia de pizza 3D** aparecerá no tile selecionado
   - Cone laranja (a fatia)
   - Azeitona preta no topo
4. **Toque no botão "↔️ Mover Pizza"** para mover a última peça adicionada
5. **Toque no tile de destino** para mover a peça

### Tipos de Peças:
- **Aliados** (Laranja com azeitona preta): Seus personagens
- **Inimigos** (Ciano com azeitona vermelha): Oponentes *(futuro)*

## 🎯 Interação

- **Toque direto em tile**: Seleciona e mostra informação
- **Tile selecionado**: Fica branco e pulsa
- **Info mostrada**: Coordenada + Tipo de terreno
- **Modo Adicionar Pizza**: Toque para colocar personagem
- **Modo Mover Pizza**: Toque para mover personagem

## 🛠️ Stack Tecnológica

- **AR.js 3.x** - Realidade Aumentada baseada na web
- **A-Frame 1.3.0** - Framework 3D/VR
- **THREE.js** - Engine 3D (incluído no A-Frame)
- **Hiro Marker** - Sistema de rastreamento de marcador
- **Vanilla JavaScript** - Lógica do jogo
- **Raycasting** - Detecção de toque precisa

## 📱 Compatibilidade

- ✅ Chrome/Safari Mobile (iOS/Android) - **TOUCH OTIMIZADO**
- ✅ Chrome/Firefox Desktop - Mouse funciona perfeitamente
- ⚠️ Requer HTTPS ou localhost para acesso à câmera
- ⚠️ Melhor experiência em dispositivos mobile

## 🎨 Personalizações Possíveis

Edite o arquivo `index.html` para:

- Modificar cores dos terrenos (objeto `TERRAIN`)
- Ajustar tamanho do tabuleiro (`scale` attribute)
- Mudar tamanho dos tiles (`TILE_SIZE`)
- Adicionar novos tipos de terreno
- Modificar o layout octogonal
- Criar novos tipos de peças de pizza (`createPizzaPiece()`)
- Adicionar efeitos visuais e animações

## 📖 Conceito do Jogo

Baseado nas anotações do projeto:
- Sistema de habilidades e pontos de vida
- Mapa em tempo real via AR
- Coordenadas para localização de personagens
- Temática de "Dungeon Pizza" com azeitonas
- **Peças móveis tipo tabuleiro de jogo**
- **Sistema de turnos baseado em coordenadas**

## 🚀 Deploy

Hospedado via GitHub Pages. Para atualizar:

```bash
git add .
git commit -m "Update game"
git push origin main
```

As mudanças aparecem automaticamente em alguns minutos.

## 📝 Notas Técnicas

### Sistema de Touch
- Usa `THREE.Vector2` para normalizar coordenadas de toque
- `Raycaster.setFromCamera()` projeta um raio da câmera através do ponto tocado
- `intersectObjects()` detecta qual tile foi tocado
- Funciona tanto com `touch` quanto com `click` (desktop)

### Canvas e Viewport
- Canvas forçado a ocupar 100% da viewport com `!important`
- `touch-action: none` previne gestos nativos do navegador
- `position: fixed` mantém o canvas sempre visível
- Debug UI do AR.js escondido para não interferir

### Peças de Pizza
- Criadas dinamicamente via JavaScript
- Compostas de `a-cone` (fatia) + `a-sphere` (azeitona)
- Posicionadas usando o mesmo sistema de grid dos tiles
- Podem ser movidas alterando atributos de posição

## 🎮 Próximos Passos Sugeridos

- [ ] Sistema de HP e atributos para personagens
- [ ] Múltiplas peças (não só a última)
- [ ] Seleção de qual peça mover
- [ ] Animações de movimento
- [ ] Efeitos visuais (partículas, brilho)
- [ ] Sistema de turnos
- [ ] Indicador de alcance de movimento
- [ ] Diferentes tipos de personagens
- [ ] Obstáculos e linha de visão

---

**Desenvolvido com base nos sketches do caderno de design do projeto** 