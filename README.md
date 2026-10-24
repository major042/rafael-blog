# Rafael Maganha — blog pessoal

Site: https://blog.rafaelmaganha.com.br

Blog pessoal feito com **Jekyll** e publicado no **GitHub Pages**. Os textos são escritos em Markdown; os arquivos HTML dos diretórios `_layouts/` e `_includes/` controlam somente a apresentação.

## Publicar um post

1. No GitHub, abra `_posts/` e escolha **Add file → Create new file**.
2. Use o nome `AAAA-MM-DD-titulo-do-post.md` (por exemplo, `2026-10-24-meu-novo-texto.md`).
3. Cole o modelo abaixo e substitua as informações e o texto.
4. Selecione **Commit changes**. O GitHub Pages publicará o post após a geração do site.

```markdown
---
layout: post
title: "Título do artigo"
description: "Uma frase curta para a listagem do blog."
category: Pessoal
---

Comece o texto neste parágrafo.

Escreva o próximo parágrafo depois de uma linha vazia.

## Um subtítulo

Aqui você pode usar **negrito**, *itálico* e [links](https://example.com).

![Descrição da imagem]({{ '/assets/images/nome-da-imagem.jpg' | relative_url }})
```

**Nota sobre imagens:** o exemplo com `{{ ... | relative_url }}` funciona em posts Jekyll, que processam Liquid. Crie `assets/images/` quando precisar e envie a imagem para lá.

## Editar ou excluir

- **Post existente:** abra seu arquivo `.md` em `_posts/`, clique no ícone de edição e confirme o commit.
- **Excluir post:** use a opção **Delete file** no arquivo de `_posts/` e confirme o commit. O artigo deixa de aparecer depois da publicação. Links antigos poderão retornar 404.
- **Páginas fixas:** edite `sobre.md`, `agora.md` e `blogroll.md` na raiz. O texto fica abaixo do segundo `---`; separe parágrafos com uma linha em branco.
- **Rascunho não publicado:** mantenha-o fora de `_posts/` até querer publicar (por exemplo, no computador local).

## Organização

| Caminho | Finalidade |
| --- | --- |
| `_posts/` | Artigos em Markdown |
| `sobre.md`, `agora.md`, `blogroll.md` | Páginas em Markdown |
| `_layouts/` | Estrutura HTML reutilizável |
| `_includes/` | Cabeçalho, rodapé e metadados |
| `assets/css/` | Estilos |
| `assets/js/` | Comportamentos de interface |
| `assets/images/` | Imagens (quando houver) |
| `_config.yml` | Endereço, formato das URLs e configuração Jekyll |
| `CNAME` | Domínio próprio no GitHub Pages |
| `feed.xml`, `sitemap.xml`, `robots.txt` | Feed e indexação |

O blog publicado é gerado a partir desses arquivos. Não misture uma cópia do site HTML gerado com os arquivos-fonte.

## Rodar localmente ou migrar

Com Ruby e Bundler instalados:

```bash
bundle install
bundle exec jekyll serve
```

Acesse `http://127.0.0.1:4000` para conferir o blog localmente.

Para mudar de servidor, preserve o projeto-fonte, instale as dependências e gere os arquivos estáticos com:

```bash
bundle exec jekyll build
```

O resultado fica em `_site/` e pode ser servido por uma hospedagem estática. Ajuste `url` e `baseurl` em `_config.yml` ao novo domínio. O DNS do domínio e o arquivo `CNAME` devem ser revistos conforme a plataforma; `CNAME` é específico do GitHub Pages.

Antes de reorganizar ou excluir arquivos, faça uma cópia do repositório e verifique referências nos layouts, páginas e estilos.
