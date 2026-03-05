# Revisão da base e tarefas sugeridas

## 1) Tarefa para corrigir erro de digitação/ortografia
**Problema encontrado:** Há rótulos e comentários em português sem acentuação em textos exibíveis ao usuário (ex.: `Adversario politico`, `discurso de odio`), enquanto outras partes já usam acentuação correta para o mesmo domínio.

**Tarefa sugerida:**
- Revisar `rdfs:label` e `rdfs:comment` em `Ontohate_V.owl` e `Ontohate_relacional_cruzamentos.ttl` para padronizar ortografia em português (ex.: `Adversário político`, `ódio`, `moderação`).
- Manter os IRIs (nomes técnicos com underscore) inalterados para evitar quebra de compatibilidade.

**Critério de aceite:**
- 100% dos `rdfs:label`/`rdfs:comment` em PT-BR com acentuação correta quando aplicável.
- Nenhum IRI alterado.

## 2) Tarefa para corrigir bug
**Problema encontrado:** No cabeçalho da ontologia TTL, `owl:versionInfo` possui dois valores ao mesmo tempo (`v1.0.0 + ...` e `v1.0.2`). Isso pode causar comportamento inconsistente em ferramentas que assumem versão única vigente.

**Tarefa sugerida:**
- Definir uma única versão canônica em `owl:versionInfo` (por exemplo `v1.0.2`).
- Se o histórico precisar ser preservado, mover versão antiga para `rdfs:comment` de changelog ou arquivo `CHANGELOG.md`.

**Critério de aceite:**
- Exatamente um valor de `owl:versionInfo` no documento principal.
- `owl:versionIRI` e `owl:versionInfo` coerentes entre arquivos OWL/Turtle.

## 3) Tarefa para ajustar comentário de código ou discrepância de documentação
**Problema encontrado:** O `README.md` está minimalista e não documenta os artefatos versionados existentes (OWL funcional, RDF/XML, Turtle relacional, planilhas), nem o estado de versão atual.

**Tarefa sugerida:**
- Expandir o `README.md` com:
  - Descrição dos arquivos do repositório e finalidade de cada um.
  - Formatos suportados e como validar cada formato.
  - Política de versionamento (ex.: onde versionIRI/versionInfo são atualizados).

**Critério de aceite:**
- Novo README com seção “Estrutura do repositório”, “Validação” e “Versionamento”.
- Leitor novo consegue entender qual arquivo usar em cada cenário.

## 4) Tarefa para melhorar um teste
**Problema encontrado:** Não há verificação automatizada de consistência semântica/sintática dos artefatos ontológicos no repositório.

**Tarefa sugerida:**
- Criar suíte de validação automática (ex.: script Python + `rdflib` ou ferramentas RDF) para:
  - Parse de `ontohate_oficial.owl`, `Ontohate_V.owl` e `Ontohate_relacional_cruzamentos.ttl`.
  - Checagem de metadados obrigatórios (ontology IRI, version IRI, version info único).
  - (Opcional) checagem de cobertura mínima de labels/comments por classe.
- Integrar em CI para bloquear merge quando a validação falhar.

**Critério de aceite:**
- Pipeline executa validação em PR.
- Falha reproduzível quando arquivo RDF estiver inválido ou metadado obrigatório ausente.
