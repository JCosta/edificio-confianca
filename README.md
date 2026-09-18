# Edifício Confiança — landing page

Página estática de apresentação do empreendimento, pronta para alojar no GitHub Pages.

## Estrutura

```
edificio-confianca/
├── index.html              ← a página toda (HTML + CSS + JS num único ficheiro)
├── images/                 ← renders/mockups (ver nomes abaixo)
└── documentos/
    └── ficha-tecnica-pip.pdf   ← o PDF real do PIP (substituir)
```

## O que tem de substituir

### 1. Imagens (pasta `images/`)
Enquanto uma imagem não existir, a página mostra automaticamente um placeholder
com o nome do ficheiro esperado — não fica nada partido. Basta colocar os
ficheiros com estes nomes exatos na pasta `images/`:

**Fachada:** `fachada-principal.jpg`, `fachada-lateral.jpg`, `fachada-noite.jpg`
**Interiores:** `interior-t0-sala.jpg`, `interior-t1-quarto.jpg`, `interior-wc.jpg`
**Áreas comuns:** `atrio-entrada.jpg`, `terraco-comum.jpg`, `estacionamento.jpg`

Para adicionar, remover ou reordenar imagens, edite o array `GALLERY` no
`<script>` no fundo do `index.html` (à procura de `const GALLERY =`).

### 2. Ficha técnica / PIP
- Os campos da secção "Ficha técnica e PIP de construção" estão no HTML,
  dentro de `<section id="ficha-tecnica">` — procure `pip-row` e substitua
  os valores de exemplo pelos dados reais do processo camarário.
- Coloque o PDF oficial em `documentos/ficha-tecnica-pip.pdf` (o botão
  "Descarregar ficha técnica" já aponta para esse caminho).

### 3. Tabela de fogos (disponibilidade, preços, estado)
Edite o array `UNITS` no `<script>` do `index.html` (à procura de
`const UNITS =`). Cada fogo é uma linha:

```js
{id:'0.1', piso:0, tipologia:'T0', area:38, preco:129000, estado:'disponivel', exp:'Nascente'},
```

- `estado` aceita apenas: `'disponivel'`, `'reservado'` ou `'vendido'`
- A tabela no site filtra, pesquisa e ordena automaticamente — não precisa
  de mexer em mais nada.

### 4. Textos, morada e contactos
- Título, descrição e "Sobre o projeto": editar diretamente no HTML.
- Morada: secção "Localização" (`<section id="sobre">`) — atualize também
  o mapa (o link do Google Maps embed usa uma pesquisa por texto; pode
  trocar por um endereço exato).
- Contactos da agência: secção `<section id="contacto">`.

## Publicar no GitHub Pages

1. Crie um repositório novo no GitHub (ex: `edificio-confianca`).
2. Faça upload/push do conteúdo desta pasta (`index.html`, `images/`,
   `documentos/`) para a raiz do repositório.
3. No repositório: **Settings → Pages → Source**, escolha a branch
   `main` e a pasta `/ (root)`.
4. Ao fim de 1-2 minutos, a página fica disponível em:
   `https://<o-seu-utilizador>.github.io/edificio-confianca/`
5. Esse é o URL que pode enviar a qualquer interessado.

### Via linha de comandos (alternativa ao upload manual)
```bash
cd edificio-confianca
git init
git add .
git commit -m "Landing page Edifício Confiança"
git branch -M main
git remote add origin https://github.com/<o-seu-utilizador>/edificio-confianca.git
git push -u origin main
```
Depois ativar o GitHub Pages como no passo 3 acima.

## Notas
- Não há dependências nem build — é um único ficheiro HTML autocontido.
- Funciona em telemóvel (menu colapsa num hambúrguer abaixo dos 860px).
- Todos os dados de exemplo (preços, áreas, PIP, contactos) são fictícios
  e têm de ser substituídos antes de enviar o link a interessados.
