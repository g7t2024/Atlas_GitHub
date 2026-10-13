# NEON / GitHub Atlas

Página estática em português com os 100 repositórios públicos mais estrelados retornados pela busca do GitHub no momento da coleta. HTML, CSS, JavaScript e dados separados. Não exige instalação de dependências.

## Abrir

1. Extraia o ZIP mantendo a estrutura de pastas.
2. Abra `index.html` em um navegador moderno.
3. Opcionalmente, execute `python -m http.server 8000` dentro da pasta e abra `http://localhost:8000`.

A página e os dados funcionam localmente, sem servidor. Fontes do Google são opcionais: sem internet, há fontes locais de fallback. Os links dos projetos e a documentação externa exigem internet. A cópia para a área de transferência pode exigir HTTPS ou localhost; em arquivo local, a página permite selecionar o texto e copiar com Ctrl+C.

## Recursos

- Ranking com 100 repositórios, estrelas, forks, linguagem, licença e data.
- Busca por nome, descrição, linguagem, categoria, finalidade e tags.
- Filtros por categoria e finalidade; ordenação por estrelas, nome e forks.
- Paginação com 12 itens; favoritos e preferência de tema armazenados no navegador.
- Detalhes com função, finalidade e passos de instalação/início de uso ou consulta.
- 30 projetos incluem um trecho de comandos do README; os demais remetem ao procedimento oficial. Os guias são introdutórios, não substituem documentação específica de versão, plataforma ou hardware.
- Gráfico de categorias, fluxo ilustrado, arte orbital SVG e animação discreta.
- Layout responsivo, foco de teclado, modal com Escape e respeito a movimento reduzido.

## Arquivos

- `index.html`: estrutura e conteúdo visual.
- `styles.css`: temas, layout, animações e responsividade.
- `app.js`: filtros, favoritos, paginação, gráficos e detalhes.
- `data.js`: dados do snapshot e guias editoriais em português.
- `assets/ranking.json`: mesma base em JSON, para reuso.
- `assets/orbit.svg`: ilustração vetorial original.
- `scripts/validate.cjs`: validação dos dados e interações com DOM simulado.

## Critério e fontes

Consulta à API pública: `https://api.github.com/search/repositories?q=stars:%3E1&sort=stars&order=desc&per_page=100`.

O retorno não marcou resultados incompletos. O snapshot inclui repositórios arquivados, listas, cursos e ferramentas; não é o ranking Trending nem uma classificação de qualidade. Repositórios podem mudar de proprietário/nome, perder disponibilidade ou ter contagens diferentes depois da coleta. O timestamp exato está em `data.js` e `assets/ranking.json`.

As instruções editoriais apontam para o README oficial de cada projeto. Foram obtidos 99 READMEs; o do kernel Linux não foi obtido e seu guia remete à documentação oficial. Trechos de shell não são instaladores completos e não são executados pela página. Não existe um comando de instalação único válido para todos os projetos.

Para atualizar, consulte novamente a API, revise os projetos e seus READMEs e atualize ambos os arquivos de dados. O snapshot é fixo; a página não faz atualização automática nem solicita token do GitHub.

## Validação

Execute `node scripts/validate.cjs`. Também foram verificados `node --check app.js` e `node --check data.js`. A validação usa DOM simulado, não um navegador real; a aparência não foi inspecionada em navegador neste ambiente.

## Publicar por conta própria

Envie `index.html`, `styles.css`, `app.js`, `data.js` e `assets/` para qualquer hospedagem estática. Não há backend, build ou credenciais.
