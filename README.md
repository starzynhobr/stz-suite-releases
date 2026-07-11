# STZ Suite — Releases

Repositório **público** de distribuição do [STZ Suite](https://github.com/starzynhobr/stz-suite).

Este repo **não** contém o código-fonte do app. Aqui ficam apenas artefatos de release e o catálogo oficial de plugins.

## O que entra aqui

| Conteúdo | Onde |
|----------|------|
| Catálogo oficial de plugins | `catalog/official-plugins.json` |
| Pacotes de plugin (`.stz-plugin`) | [GitHub Releases](https://github.com/starzynhobr/stz-suite-releases/releases) |
| (Opcional) instalador / Base | Releases |

## Como o app usa este repositório

1. O app baixa o catálogo em `catalog/official-plugins.json`.
2. Cada plugin no catálogo declara `version`, `package_url` e `sha256`.
3. **Instalar / Atualizar** usa a URL do catálogo (não depende de `latest` do GitHub).
4. Atualização disponível = versão instalada menor que a versão listada no catálogo.

## Formato de release (plugins)

Sugestão de tags (um plugin por versão):

```text
fetchora-v0.1.0
lumio-v0.1.0
```

Ou um release agrupado:

```text
plugins-v0.1.0
```

Assets com o nome de marca do pacote, por exemplo:

```text
Fetchora-0.1.0.stz-plugin
Lumio-0.1.0.stz-plugin
```

URL típica de asset:

```text
https://github.com/starzynhobr/stz-suite-releases/releases/download/<tag>/<arquivo>.stz-plugin
```

## Segurança

- Prefira sempre URLs HTTPS deste repositório.
- O app valida o pacote com o `sha256` declarado no catálogo (quando preenchido).
- Não publique código-fonte nem segredos neste repositório.

## Manutenção

1. Gerar o `.stz-plugin` no repositório privado de desenvolvimento.
2. Criar/atualizar um Release e anexar o asset.
3. Atualizar `catalog/official-plugins.json` (`version`, `package_url`, `sha256`, `size_bytes`).
4. Commit + push do catálogo na branch `main`.

## Licença / uso

Distribuição oficial de binários e catálogo do STZ Suite.  
O código-fonte e termos de uso do aplicativo permanecem no repositório de desenvolvimento.
