# Ontohate
Projeto que envolve a criação de uma taxonomia e uma ontologia do discurso de ódio online.

## Como visualizar o código na página
A interface web do projeto está em `index.html`.

### Opção 1 (mais simples): abrir direto no navegador
1. No explorador de arquivos, acesse a pasta do projeto.
2. Dê duplo clique em `index.html`.

### Opção 2 (recomendado): subir um servidor local
Na raiz do projeto, rode:

```bash
python3 -m http.server 8000
```

Depois, abra no navegador:
- `http://localhost:8000/index.html`

> Se alguma funcionalidade depender de carregamento de arquivos via navegador, usar servidor local costuma evitar bloqueios de CORS/segurança do modo `file://`.
