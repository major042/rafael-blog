# Blog pessoal — Rafael Maganha

Primeira versão, com **Jekyll nativo** e publicação no **GitHub Pages**, sem hospedagem paga e sem banco de dados. Estética autoral minimalista inspirada no TechDemo (não é cópia do código nem do design).

## Estrutura

- `index.html`: apresentação e posts recentes;
- `blog.html`: arquivo de publicações;
- `agora.md` e `sobre.md`: páginas pessoais;
- `_posts/`: publicações em Markdown (os dois posts incluídos são **exemplos**, não relatos reais);
- `_layouts/` e `_includes/`: estrutura reutilizável;
- `assets/css/style.css`: cores, espaçamento e layout;
- `assets/js/main.js`: alternância claro/escuro (com preferência salva no navegador);
- `feed.xml` e `sitemap.xml`: RSS e sitemap;
- `CNAME`: domínio do blog;
- `_config.yml`: parâmetros do site.

## Publicar no GitHub Pages — sem terminal

1. Faça login em https://github.com/ e crie um repositório **público** chamado `rafael-blog` (ou outro nome). Mantenha o projeto profissional em outro repositório no futuro.
2. Extraia o ZIP e **envie o conteúdo da pasta** (não a pasta externa nem o ZIP) ao repositório. No GitHub, **Add file → Upload files**. Arquivos e pastas iniciados por `_` devem permanecer com os nomes originais. Para assegurar o envio de arquivos ocultos (`.gitignore`), prefira Git ou GitHub Desktop; não é necessário enviá-lo para publicar.
3. Acesse **Settings → Pages**. Em **Build and deployment**, escolha **Deploy from a branch**, branch `main`, pasta `/(root)`. Salve.
4. Na mesma página, em **Custom domain**, informe `blog.rafaelmaganha.com.br` e salve.
5. No painel DNS onde `rafaelmaganha.com.br` é administrado, crie:

   | Tipo | Nome/Host | Destino/Valor |
   | ---- | --------- | ------------- |
   | CNAME | blog | `SEU_USUARIO.github.io` |

   **Troque `SEU_USUARIO` pelo seu usuário real no GitHub.** Não inclua `https://`, barra, nem o nome do repositório no destino. Se já houver registro para o host `blog`, revise conflito antes de criar outro. O domínio raiz `rafaelmaganha.com.br` fica livre para seu site profissional; não altere os registros dele nesta etapa.
6. Aguarde o DNS e a emissão do certificado. No GitHub, confira se **Enforce HTTPS** está habilitado quando disponível. A propagação pode levar até 24h.
7. Acesse https://blog.rafaelmaganha.com.br/ para conferir.

**Importante:** como o projeto está configurado para o domínio próprio (`url` e `baseurl` em `_config.yml`), alguns links e recursos podem não funcionar corretamente no endereço provisório `SEU_USUARIO.github.io/rafael-blog/` antes de configurar o domínio. Para testar antes, use Jekyll localmente ou altere temporariamente `baseurl` para `/rafael-blog` e `url` para `https://SEU_USUARIO.github.io` (depois reverta para o domínio).

## Criar uma publicação

Em `_posts/`, crie um arquivo como `2026-10-23-meu-primeiro-texto.md`, com o conteúdo:

```md
---
layout: post
title: "Meu primeiro texto"
description: "Uma frase breve sobre o artigo."
category: Pessoal
---

Seu texto começa aqui.

## Um subtítulo

Outro parágrafo.
```

A data do nome do arquivo determina a data da publicação. **Não use uma data futura** para publicações que devam aparecer imediatamente. A cada commit no `main`, o GitHub Pages reconstrói automaticamente o site.

## Personalizar

- **Introdução:** `index.html`
- **Apresentação:** `sobre.md`
- **Página Agora:** `agora.md`
- **Título, descrição, endereço:** `_config.yml`
- **Links da navegação:** `_includes/header.html`
- **Rodapé:** `_includes/footer.html`
- **Cores:** variáveis CSS no início de `assets/css/style.css`
- **Posts demonstrativos:** substitua ou remova os arquivos em `_posts/` antes de divulgar.
- **Site profissional:** o link no rodapé aponta para o domínio principal, mesmo antes de haver um site; ajuste ou remova se preferir.

## Testar no computador (opcional)

Se tiver Ruby e Bundler instalados:

```bash
bundle install
bundle exec jekyll serve
```

Abra http://127.0.0.1:4000. Em ambiente Linux, normalmente é mais simples instalar Ruby pelo gerenciador de pacotes; para Windows, publicar direto pelo GitHub evita configurar Ruby.

## Observações

- Hospedagem do GitHub Pages é gratuita para repositórios públicos em planos compatíveis, mas **a renovação do domínio segue sendo cobrada pelo seu registrador**.
- O site não coleta informações por formulário e não usa serviços de análise nem scripts de terceiros.
- O tema escuro usa somente um pequeno JavaScript local.
- O nome do repositório não precisa coincidir com o domínio.

Documentação oficial: https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site/managing-a-custom-domain-for-your-github-pages-site
