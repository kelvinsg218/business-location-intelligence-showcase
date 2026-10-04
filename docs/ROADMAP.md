# Roadmap

Estado atual do desenvolvimento: **v0.7**. O projeto está em desenvolvimento ativo e ainda não tem release pública.

## Disponível

Funcionalidades implementadas e testadas até a v0.7.

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

**Demografia (v0.7, experimental)**
- População residente e domicílios ocupados estimados no raio, a partir da Grade Estatística do Censo 2022 do IBGE
- Limites inferior e superior, estimativa central apenas quando defensável, densidade bruta, ano de referência, cobertura, origem dos dados e limitações na interface
- Importação versionada e verificável dos arquivos oficiais do IBGE, com publicação atômica de cada versão
- Demografia registrada nas análises salvas e incluída na comparação, sem misturar versões de dados ou de método
- Cálculo apenas para pontos posicionados pelo usuário (cautela com os termos do provedor de mapas)
- **Cobertura atual:** o sistema suporta os 56 quadrantes oficiais do Brasil; o ambiente demonstrado tem 2 importados (Espírito Santo e entorno)
- **Pendente:** confirmação da licença da Grade Estatística para uso comercial; até lá, a funcionalidade é experimental

## Planejado

Direção atual do produto, sujeita a mudanças conforme o produto for testado com usuários reais. Sem datas e sem compromisso de entrega.

- Importação dos 56 quadrantes do Brasil e confirmação da licença dos dados demográficos para uso comercial
- Outras informações demográficas (como faixas etárias e rendimento), apenas com regras de precisão próprias
- Ampliação do contexto comercial analisado
- Custos do ponto informados pelo usuário
- Registro de visitas de campo
- Relatórios

## Fora do escopo atual

O BLI não pretende prever o sucesso de um negócio, garantir demanda, classificar locais em um ranking ou escolher automaticamente o melhor ponto.
