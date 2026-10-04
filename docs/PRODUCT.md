# Produto

## Para quem

Para quem está avaliando onde abrir ou expandir um negócio físico (uma academia, um restaurante, uma farmácia) e quer organizar essa avaliação: comparar mentalmente alternativas de ponto, registrar o que viu e voltar a isso depois.

## Proposta

**Entenda uma região antes de investir nela.** O BLI reúne em um só lugar a escolha do ponto, a análise do entorno, o registro do resultado e a comparação entre os locais considerados.

O BLI **apoia** uma decisão. Ele não prevê sucesso, não garante demanda e não escolhe o melhor ponto. O indicador de concorrência local descreve a concorrência encontrada; ele não mede demanda nem é uma recomendação. A demografia estimada descreve quem mora na região; ela não mede demanda nem potencial de faturamento.

## Conceitos

| Conceito | O que é |
|---|---|
| **Projeto** | Um estudo de localização, por exemplo "Nova unidade em Vila Velha". Tem objetivo (novo negócio ou expansão), tipo de negócio, cidade/região e notas |
| **Local candidato** | Um ponto que o usuário está considerando dentro de um projeto ("Opção A", "Loja Centro"). Não é uma análise: é o lugar em estudo |
| **Análise** | O levantamento da concorrência e do contexto comercial ao redor de um ponto, para um tipo de negócio e um raio |
| **Snapshot** | Uma análise salva. Registra o resultado daquele momento e não muda depois |
| **Histórico** | Todas as análises salvas pelo usuário, com ou sem projeto |
| **Comparação** | Uma visão lado a lado de 2 a 5 locais candidatos de um mesmo projeto, montada a partir das análises salvas. Não é salva e não é uma recomendação |
| **Demografia da região** | Estimativa de população residente e de domicílios ocupados dentro do raio, com limites inferior e superior, a partir do Censo 2022 do IBGE (experimental) |

## Jornada

1. **Entrar:** criar conta ou fazer login.
2. **Organizar:** criar um projeto com o tipo de negócio e a região de interesse.
3. **Marcar pontos:** adicionar locais candidatos por endereço, pela localização do navegador ou pelo mapa, clicando ou arrastando o marcador.
4. **Analisar:** executar a análise de um local. O tipo de negócio do projeto já vem preenchido. Nada é executado automaticamente ao marcar um ponto.
5. **Registrar:** salvar a análise, que fica vinculada ao local e aparece no histórico.
6. **Comparar:** em "Comparar locais", escolher de 2 a 5 locais do projeto que já tenham análise salva e ver as diferenças lado a lado.
7. **Revisitar:** reabrir projetos, locais e análises a qualquer momento, sem refazer consultas. A comparação não é gravada: ela é montada de novo, a partir do que foi salvo, sempre que é aberta.

**A decisão é do usuário.** O BLI apresenta evidências e diferenças; ele não escolhe o local, não classifica os locais e não estima chance de sucesso.

## O que a análise mostra

- estabelecimentos concorrentes encontrados no raio escolhido;
- densidade de concorrentes por km² e distância média até o ponto;
- nível de concorrência (baixo, médio, alto) e o **indicador de concorrência local** (0 a 100);
- para tipos de negócio com perfil mapeado, negócios complementares e possíveis geradores de fluxo próximos;
- avisos sobre as limitações da cobertura (a busca não é um censo completo da região);
- a **demografia da região** (experimental): população residente e domicílios ocupados estimados no raio, com a faixa entre os limites inferior e superior, a estimativa central quando ela é defensável, o ano de referência (Censo 2022), a cobertura disponível e as limitações do método.

## Como ler a demografia

- **São estimativas, não contagens.** O círculo da análise não coincide com as células do IBGE: o limite inferior conta só as células inteiramente dentro do raio, e o superior conta todas as células tocadas. A diferença vem de não se saber onde os moradores estão dentro de cada célula; **não é um intervalo de confiança estatístico**.
- **Quando a faixa é larga, só a faixa aparece.** Em raios pequenos ou áreas rurais, a tela pode dizer "Dados insuficientes para estimativa".
- **Moradores não são clientes.** A demografia mostra onde as pessoas moram em 2022, não quem circula pela região, não a demanda e não o faturamento possível.
- **Cobertura conta.** Só há números onde os dados oficiais já foram importados; fora disso, a tela informa que os dados não estão disponíveis, em vez de mostrar zero.
- **Origem do ponto conta.** A demografia é calculada para pontos marcados ou ajustados pelo usuário no mapa, coordenadas informadas ou a localização do dispositivo; pontos vindos de busca de endereço não são usados, por cautela com os termos do provedor de mapas.

## O que a comparação mostra

Para cada local, lado a lado, a partir da análise salva escolhida (por padrão, a mais recente daquele local):

- raio analisado;
- concorrentes encontrados, densidade de concorrentes e distância média dos concorrentes;
- indicador de concorrência local e nível de concorrência;
- negócios complementares e geradores de fluxo, quando o tipo de negócio tem perfil mapeado;
- população residente, domicílios ocupados e densidade bruta estimados, com suas faixas, quando as análises têm demografia.

Como ela deve ser lida:

- **Diferença não é veredito.** A tela aponta apenas o maior e o menor valor observado em cada linha. Não há ranking, nota geral ou "melhor local".
- **Concorrência depende de contexto.** Mais concorrentes não é automaticamente pior: pode indicar mercado disputado, concentração do segmento ou presença de demanda. Menos concorrentes não é automaticamente melhor.
- **Ausência não é zero.** Um dado que não existe naquela análise aparece como "Não disponível" ou "Não se aplica".
- **Análises precisam ser comparáveis.** Resultados produzidos por versões diferentes do método de análise não são comparados entre si, e raios diferentes são sinalizados.
- **Nada é recalculado.** A comparação usa o que foi salvo; para dados atuais, faz-se uma nova análise do local.
- **Faixas que se sobrepõem não têm "maior".** Na demografia, o maior e o menor valor só são apontados quando as faixas dos locais não se sobrepõem, e só entre análises com a mesma versão dos dados do IBGE e do método. Análises salvas antes da v0.7 aparecem como "Não disponível".

## Princípios

- **Transparência:** limitações e o caráter descritivo do indicador aparecem junto do resultado.
- **Nada é salvo sem ação do usuário:** escolher um ponto ou usar a localização do navegador não grava nada.
- **Histórico fiel:** o que foi salvo não é recalculado nem alterado silenciosamente.
- **Neutralidade:** comparações descrevem diferenças; não recomendam.
- **Honestidade sobre a incerteza:** estimativas aparecem como estimativas, com faixa, fonte, data de referência e limitações; nunca como contagens exatas.
- **Português do Brasil** em toda a interface.
