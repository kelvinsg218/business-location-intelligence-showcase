# Segurança (visão geral)

Práticas adotadas no BLI, descritas em alto nível. Configurações, parâmetros e implementação não são publicados.

## Contas e sessões

- Senhas nunca são armazenadas em texto puro: apenas um hash gerado por um algoritmo moderno, próprio para senhas.
- Senhas fracas ou muito comuns são recusadas no cadastro.
- Login com mensagens que não revelam se um e-mail está cadastrado.
- Sessões mantidas no servidor. O navegador recebe apenas um identificador opaco em cookie protegido, inacessível a scripts e restrito ao próprio site.
- A sessão expira por inatividade e também por tempo máximo, e é renovada no login.
- Logout invalida a sessão no servidor.

## Requisições

- Verificação de origem em requisições que alteram dados, além das proteções do próprio cookie.
- Toda entrada é validada por esquema. Campos desconhecidos são recusados onde fazem diferença.
- Limites de tamanho para o corpo das requisições.
- Limites de taxa para cadastro, tentativas de login, análises e buscas de endereço.
- Cabeçalhos HTTP de segurança.

## Dados e isolamento

- Cada recurso pertence a um usuário, e o dono é sempre determinado pela sessão, nunca por dados enviados pelo navegador.
- Todas as consultas são filtradas pelo usuário. O banco de dados também impede vínculos entre dados de usuários diferentes.
- Recursos de outro usuário respondem exatamente como recursos inexistentes.
- Comparações só aceitam locais do mesmo projeto e do próprio usuário; qualquer outra seleção é recusada da mesma forma.
- Consultas SQL sempre parametrizadas. Uma regra de lint e testes de arquitetura impedem SQL montado por concatenação.
- Resultados salvos não podem ser alterados, nem pela API nem diretamente no banco.

## Privacidade

- A localização do usuário só é persistida quando ele salva explicitamente uma análise ou um local.
- A localização obtida pelo navegador não é armazenada por si só.
- Coordenadas e endereços trafegam no corpo das requisições nos fluxos novos, e os logs não registram parâmetros de consulta.
- Mensagens de erro não ecoam endereços, coordenadas ou detalhes internos.
- Falhas de banco retornam erros genéricos, sem dados de conexão.

## Segredos e ambiente

- Segredos apenas em variáveis de ambiente, nunca no código. Em produção, a aplicação se recusa a iniciar sem os segredos obrigatórios.
- Chaves de provedores externos ficam somente no servidor e nunca chegam ao navegador.
- O CI roda sem segredos e sem chamar serviços pagos. O ambiente de testes bloqueia chamadas reais a provedores externos.
- Scripts de instalação de dependências são revisados e bloqueados por padrão.

## Terceiros

O armazenamento de conteúdo de provedores externos respeita os termos de cada provedor: guarda-se apenas o que é permitido, e o que não pode ser guardado é removido antes de salvar.

## Reportar um problema

Se você encontrar algo que pareça um problema de segurança relacionado a este projeto, entre em contato com o autor de forma privada. Não abra uma issue pública.
