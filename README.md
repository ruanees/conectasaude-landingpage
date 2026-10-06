# Conecta Saúde — landing page

Site estático (HTML único, 13 páginas internas navegáveis por `#`), publicado no **Cloudflare Pages**.

> **Status:** prévia em análise — ainda não aprovada. O site está marcado como `noindex`
> (meta tag, cabeçalho `X-Robots-Tag` e `robots.txt`) para não aparecer no Google até a aprovação.

## Estrutura

```
public/
  index.html   # o site inteiro
  _headers     # cabeçalhos do Cloudflare (noindex enquanto for prévia)
  robots.txt   # bloqueia buscadores enquanto for prévia
wrangler.toml  # configuração do Cloudflare Pages
```

## Publicar no Cloudflare Pages (via GitHub)

1. Cloudflare → **Workers & Pages** → **Create** → **Pages** → **Connect to Git**.
2. Escolha o repositório `ruanees/conectasaude-landingpage`.
3. Configuração de build:
   - **Framework preset:** None
   - **Build command:** *(vazio)*
   - **Build output directory:** `public`
4. **Save and Deploy**. A cada `git push` o Cloudflare publica de novo automaticamente.

## Publicar pela linha de comando (alternativa)

```sh
npx wrangler pages deploy public --project-name conectasaude-landingpage
```

## Quando o site for aprovado

- Remover `<meta name="robots" content="noindex,nofollow">` de `public/index.html`.
- Apagar a linha `X-Robots-Tag` de `public/_headers` e liberar o `public/robots.txt`.
- Remover a faixa "Prévia navegável" (`#aviso-previa`) do topo da página.
- Trocar o telefone/WhatsApp provisório `(85) 90000-0000` pelo número real.
