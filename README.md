# Conecta Saúde — landing page

Site estático (HTML único, 13 páginas internas navegáveis por `#`), publicado no **Cloudflare Workers** (arquivos estáticos).

> **Status:** prévia em análise — ainda não aprovada. O site está marcado como `noindex`
> (meta tag, cabeçalho `X-Robots-Tag` e `robots.txt`) para não aparecer no Google até a aprovação.

## Estrutura

```
public/
  index.html   # o site inteiro
  _headers     # cabeçalhos do Cloudflare (noindex enquanto for prévia)
  robots.txt   # bloqueia buscadores enquanto for prévia
wrangler.toml  # configuração do Cloudflare (serve a pasta public/)
```

## Publicar no Cloudflare (Workers, via GitHub)

O projeto `conectasaude-landingpage` no Cloudflare está ligado a este repositório.
Configuração usada:

- **Build command:** *(vazio)*
- **Deploy command:** `npx wrangler deploy`
- **Root directory:** `/`

O `wrangler.toml` manda o Cloudflare servir os arquivos de `public/`. A cada `git push`
na branch de produção o site é publicado de novo automaticamente.

## Quando o site for aprovado

- Remover `<meta name="robots" content="noindex,nofollow">` de `public/index.html`.
- Apagar a linha `X-Robots-Tag` de `public/_headers` e liberar o `public/robots.txt`.
- Remover a faixa "Prévia navegável" (`#aviso-previa`) do topo da página.
- Trocar o telefone/WhatsApp provisório `(85) 90000-0000` pelo número real.
