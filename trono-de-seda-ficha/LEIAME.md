# Ficha - O Trono de Seda (extensão Owlbear Rodeo 2.0)

Arquivos: `manifest.json`, `index.html`, `icon.svg`, `_headers` (CORS para Netlify) e a pasta `cartas/` (78 cartas em WebP).
Mantenha tudo junto, na raiz do site.

## Testar localmente
1. Dentro desta pasta: `npx http-server . -p 5173 --cors -c-1`
2. No Owlbear Rodeo: Perfil, Extensions, Add Extension, cole `http://localhost:5173/manifest.json`
3. Ative a extensão na sala (Edit Room, ou o botão Extensions dentro da sala) e clique no ícone de portão (torii) no canto superior esquerdo.

## Publicar para os jogadores
Suba a pasta inteira na raiz de um site estático (Netlify, GitHub Pages, Vercel) e instale usando a URL do `manifest.json` publicado.
No Netlify, o arquivo `_headers` já libera o CORS que o Owlbear precisa para ler o manifest.

## Onde ficam os dados
- Sala: uma chave por jogador em `OBR.room.setMetadata` (`com.trono-de-seda.ficha/<id do jogador>`). O limite do metadata da sala é 16 kB no total.
- Navegador: cópia de segurança em localStorage.
- Menu (…) da ficha: copiar e importar JSON, medidor de espaço e, para o mestre, seletor das fichas dos jogadores.

## Ajustes rápidos
- Versão do SDK: constante `SDK_URL` no topo do script do `index.html`.
- Tamanho do painel: `width` e `height` no `manifest.json`.
- Rituais do suplemento: objeto `PRESETS`. Cartas: lista `CARTAS` e a pasta `cartas/`.
