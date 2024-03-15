# Foliant + MkDocs Help Example

Tools: 

- [Folinat with MkDocs backend](https://foliant-docs.github.io/docs/backends/mkdocs/)
- [MkDocs Material Theme](https://squidfunk.github.io/mkdocs-material/getting-started/)
- [Swagger UI](https://github.com/swagger-api/swagger-ui)

Build html:

```
docker compose run --rm foliant make site --config ./configs/foliant-mkdocs.yml
```

To check the result start simple *http.server*:

For Unix:

```
docker run -it --rm -p 127.0.0.1:8000:8000 \
  -w /app --mount "type=bind,src=$pwd/public/foliant-help-demo.mkdocs,target=/app" \
  python:alpine3.19 python3 -m http.server
```

For Windows:

```
docker run -it --rm -p 127.0.0.1:8000:8000 `
  -w /app --mount "type=bind,src=$pwd/public/foliant-help-demo.mkdocs,target=/app" `
  python:alpine3.19 python3 -m http.server
```

## Customizations 

File/Folder | Purpose
:---: | :---:
`assets/logo` | Logo for the site header and site thumbnail.
`assests/swagger-ui-5-7-2` | Files for swagger-ui, prepared with in-house npm-based Docker image.
`overrides/main.html` | MkDocs Material general templates upadte.
`overrides/swagger-ui.html` | Special page for rendering swagger-ui. Includes the link to the specification `.json` file.

## Buid swagger-ui package

https://github.com/swagger-api/swagger-ui

https://docs.docker.com/guides/walkthroughs/multi-container-apps/

## Change deployment path

If you want to rename the resulting folder with static files do the following:

1. Change `slug` value in the `foliant-mkdocs.yml`.
2. Update `steps - with - path` value.
