# Roadmap

Estado atual do desenvolvimento: **v0.6**. O projeto está em desenvolvimento ativo e ainda não tem release pública.

## Disponível

Funcionalidades implementadas e testadas até a v0.6.

**Base**
- Cadastro, login e logout com sessões no servidor
- Persistência em PostgreSQL com migrations versionadas
- Isolamento de dados por usuário

**Análise de localização**
- Seleção do ponto por endereço, localização do navegador, clique no mapa e arrasto do marcador
- Identificação automática do endereço de um ponto, quando disponível
- Análise de concorrência no raio escolhido: contagem, densidade, distância média, nível de concorrência
- Indicador de concorrência local (0–100), descritivo
- Contexto comercial: negócios complementares e possíveis geradores de fluxo, para tipos de negócio com perfil mapeado

**Registro**
- Análises salvas como snapshots imutáveis e versionados
- Histórico paginado; reabrir sem refazer consultas; excluir

**Estudos**
- Projetos (novo negócio ou expansão)
- Locais candidatos por projeto, visualizados no mapa
- Análises vinculadas a cada local candidato

**Comparação**
- Comparação lado a lado de 2 a 5 locais candidatos do mesmo projeto
- Baseada nas análises salvas (a mais recente de cada local por padrão, com opção de escolher outra), sem novas consultas e sem gravar a comparação
- Destaque apenas do maior e do menor valor observado, em linguagem neutra; sem ranking nem recomendação
- Dados ausentes indicados como ausentes; resultados de versões diferentes do método não são misturados
- Locais comparados exibidos no mapa, quando permitido

## Planejado

Direção atual do produto, sujeita a mudanças conforme o produto for testado com usuários reais. Sem datas e sem compromisso de entrega.

- Dados demográficos da região
- Ampliação do contexto comercial analisado
- Custos do ponto informados pelo usuário
- Registro de visitas de campo
- Relatórios

## Fora do escopo atual

O BLI não pretende prever o sucesso de um negócio, garantir demanda, classificar locais em um ranking ou escolher automaticamente o melhor ponto.
