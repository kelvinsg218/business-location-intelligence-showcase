# API (visão geral)

API REST versionada em `/api/v1`, com JSON e autenticação por sessão (cookie). Ela é documentada com OpenAPI na aplicação; este resumo mostra apenas as categorias e os endpoints principais. Não é uma API pública nem um contrato estável para terceiros.

## Convenções

- Respostas de sucesso: `{ "success": true, "data": { ... } }`.
- Respostas de erro: `{ "success": false, "error": { "code", "message", "details", "requestId" } }`, com códigos estáveis como `VALIDATION_ERROR` e `UNAUTHENTICATED`.
- Todos os endpoints, exceto os de cadastro, login e verificação de saúde, exigem sessão.
- Recursos de outro usuário respondem `404`, como se não existissem.

## Categorias

### Autenticação

| Método | Endpoint | Descrição |
|---|---|---|
| `POST` | `/api/v1/auth/register` | Cria a conta e inicia a sessão |
| `POST` | `/api/v1/auth/login` | Inicia a sessão |
| `POST` | `/api/v1/auth/logout` | Encerra a sessão |
| `GET` | `/api/v1/auth/me` | Usuário da sessão atual |

### Localização e análise

| Método | Endpoint | Descrição |
|---|---|---|
| `POST` | `/api/v1/locations/analyze` | Analisa um ponto (endereço **ou** coordenadas, nunca os dois) para um tipo de negócio e raio; desde a v0.7 inclui a seção de demografia estimada |
| `POST` | `/api/v1/locations/geocode` | Converte um endereço em ponto no mapa |
| `POST` | `/api/v1/locations/reverse` | Obtém um rótulo de endereço para um ponto |
| `GET` | `/api/v1/locations/capabilities` | Recursos disponíveis no ambiente: provedores, mapa e cobertura demográfica (quadrantes importados, caráter experimental) |

**Demografia (v0.7, experimental).** A resposta da análise traz uma seção com a população residente e os domicílios ocupados estimados no raio: limites inferior e superior, estimativa central apenas quando defensável, unidade, ano de referência, cobertura, versão dos dados do IBGE, versão do método, avisos e um estado que explica qualquer ausência (origem do ponto não permitida, dados não importados, cobertura parcial, área sem células publicadas ou falha de consulta). Um valor ausente nunca é apresentado como zero.

### Análises salvas

| Método | Endpoint | Descrição |
|---|---|---|
| `POST` | `/api/v1/analyses` | Salva o resultado de uma análise (opcionalmente em um local candidato) |
| `GET` | `/api/v1/analyses` | Histórico paginado |
| `GET` | `/api/v1/analyses/{id}` | Reabre o snapshot salvo, sem consultar provedores |
| `DELETE` | `/api/v1/analyses/{id}` | Exclui uma análise salva |

### Projetos

| Método | Endpoint | Descrição |
|---|---|---|
| `POST` / `GET` | `/api/v1/projects` | Cria / lista projetos |
| `GET` / `PATCH` / `DELETE` | `/api/v1/projects/{id}` | Lê / edita / exclui um projeto |

### Locais candidatos

| Método | Endpoint | Descrição |
|---|---|---|
| `POST` / `GET` | `/api/v1/projects/{id}/locations` | Adiciona / lista os locais de um projeto |
| `GET` / `PATCH` / `DELETE` | `/api/v1/candidate-locations/{id}` | Lê (com análises relacionadas) / renomeia ou anota / remove |

### Comparação

| Método | Endpoint | Descrição |
|---|---|---|
| `POST` | `/api/v1/projects/{projectId}/compare` | Recebe a seleção de 2 a 5 locais candidatos do projeto e devolve a comparação lado a lado, montada a partir das análises salvas |

A comparação é calculada a cada chamada e não é gravada; não executa análises nem consulta provedores externos. Os locais precisam pertencer ao projeto e ao usuário da sessão e ter ao menos uma análise salva. A seleção vai no corpo da requisição, e não na URL. Desde a v0.7, inclui as estimativas demográficas com suas faixas, comparáveis apenas entre análises com a mesma versão dos dados e do método.

### Operação

| Método | Endpoint | Descrição |
|---|---|---|
| `GET` | `/health` | O processo está no ar |
| `GET` | `/ready` | A aplicação está pronta (banco disponível) |

## Exemplo ilustrativo

Um exemplo **sanitizado e simplificado** do tipo de informação que uma análise devolve está em [../examples/analysis-response.example.json](../examples/analysis-response.example.json). A parte comercial usa dados fictícios; a parte demográfica traz valores reais calculados pelo BLI a partir dos dados oficiais do IBGE, como indicado no próprio arquivo. Ele não reproduz o contrato interno exato.
