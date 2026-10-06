# SOC Hands-on 2 - Mini-SIEM

Exercício prático **sem nota**, continuação do Lab 1 (triagem de alertas).
Aqui não existe alerta pronto: você recebe o **log bruto de um dia** da OrbitaPay (fintech **fictícia**) e precisa **achar a intrusão**, **decidir o que é real ou falso positivo**, **escrever regras de detecção** e **organizar a resposta**.

> Todos os dados são sintéticos. Nenhum IP, domínio, usuário ou hash existe de verdade.
> Não adianta pesquisar os IOCs na internet. Use a **Base de contexto** dentro do próprio console.

## Como abrir
1. Baixe a pasta e dê **duplo clique em `index.html`** (qualquer navegador atual). Não precisa de internet nem de instalação.
2. Se quiser, digite seu nome/RM no topo (só aparece no relatório que você baixar).

## As 4 partes (sugestão: 60-80 min)

| Parte | O que você faz | Conecta com |
|---|---|---|
| **1 - Caça** | Busca e filtra ~1.500 eventos (auth, proxy, DNS, EDR, firewall) e marca com 🚩 o que parece suspeito. Clique em um valor azul para filtrar por ele (pivot). | Threat hunting |
| **2 - Veredito** | Seus eventos são agrupados por correlação. Para cada grupo: incidente real ou falso positivo? Justifique. | Triagem de SOC |
| **3 - Detecção** | Monte regras (condições + limiar + janela) e veja quantos ataques ela pega (recall) e quantos falsos alertas gera (precisão). 3 desafios. | Engenharia de detecção |
| **4 - Resposta** | Ordene a cronologia, defina o escopo e classifique as ações por fase (contenção, erradicação, recuperação, pós-incidente). | Resposta a incidentes |

Você pode navegar entre as abas livremente. A **Parte 3** funciona mesmo sem terminar a Parte 1, mas ela rende mais se você já entendeu o ataque.

## Como funciona o feedback
- **Parte 2 e Parte 4:** depois de registrar, aparecem a resposta esperada e a explicação. O registro não pode ser refeito (o botão *Reiniciar* apaga tudo).
- **Parte 3:** você pode testar e ajustar a regra **quantas vezes quiser**. É assim que se aprende a calibrar.
- Não vale nota. O objetivo é errar aqui para acertar num SOC de verdade.

## Dicas (sem spoilers)
- **Leia a Base de contexto** (Parte 1) antes de decidir. Analista sem contexto só consegue chutar.
- **Um evento isolado quase nunca prova nada.** Procure padrões: mesma origem, mesmo usuário, mesmo horário, sequência de ações.
- **Horário importa.** O que é normal às 10h pode ser suspeito às 3h.
- **Quem, de onde, quando e por quê:** o mesmo comando pode ser rotina ou ataque dependendo desses quatro fatores.
- **Pivote.** Achou um IP ou usuário estranho? Clique e veja tudo que ele fez no dia.
- **Pense na linha do tempo.** Ataques têm fases: acesso, reconhecimento, ação e impacto. Se achou o fim, volte e procure o começo.
- **Contas de serviço são previsíveis.** Fuja do "parece normal": compare com o que o contexto diz que deveria acontecer.
- **Regra boa = pega o ataque e ignora a rotina.** Se a sua regra alerta em tudo, ninguém vai ler os alertas. Se não alerta em nada, ela é inútil.
- **Janela e agrupamento são ferramentas.** Ataques lentos precisam de janelas longas; ruído global se resolve contando "por origem" ou "por usuário".
- **Use as dicas dos desafios** só depois de tentar. Elas são progressivas.

## Glossário rápido
| Termo | Significado |
|---|---|
| **IOC** | Indicator of Compromise: IP, domínio, hash, comando etc. que indica atividade maliciosa. |
| **Recall** | Dos ataques que existem, quantos a regra pegou. |
| **Precisão** | Dos alertas que a regra gerou, quantos eram ataque de verdade. |
| **FP / TP** | Falso positivo / verdadeiro positivo. |
| **Hunting** | Busca proativa por ameaças, sem esperar um alerta. |
| **Pivot** | Usar um dado achado (IP, usuário) para buscar mais evidências relacionadas. |
| **Conta de serviço** | Conta usada por sistemas (jobs, aplicações), não por pessoas. |
| **IR** | Incident Response (resposta a incidentes). |
| **TTP** | Táticas, técnicas e procedimentos do atacante. |

## Combinados
- Ambiente de **treino**: errar faz parte.
- Discuta com a dupla, mas **registre o seu próprio trabalho**.
- Não compartilhe a solução com quem ainda não terminou.
- Os IOCs e regras deste exercício **não devem ser usados em ambientes reais** sem adaptação e teste.

## Confiança (metacognição)
Em cada decisão você informa **o quanto confia nela** (1 = chutei, 5 = tenho certeza). No Debrief você vê seus erros com **confiança alta**: são o ponto cego mais perigoso de um profissional de segurança, e o melhor lugar para estudar primeiro.

## Objetivos de aprendizagem
Ao final você será capaz de: **procurar** indicadores de intrusão em logs brutos; **projetar e calibrar regras de detecção** avaliando precisão, recall e F1; **reconstruir** a linha do tempo de um incidente; e **organizar a resposta** por fase (contenção, erradicação, recuperação, pós-incidente).

## Entregando o resultado (opcional)
Ao final, clique em **Exportar .json** e envie o arquivo ao professor. Ele agrega os resultados da turma para ver **quais conceitos precisam ser reforçados**; o nome/RM é opcional. O arquivo é só diagnóstico: não vale nota.

## Série de labs (todos sem nota, 100% offline)
| Lab | Repositório |
|---|---|
| Triagem de alertas (SOC) | https://github.com/juliocataldo/soc-lab |
| Mini-SIEM: caça, detecção e resposta | https://github.com/juliocataldo/soc-lab (pasta `lab2-siem/`) |
| Threat Modeling: STRIDE + DREAD | https://github.com/juliocataldo/threat-modeling-lab |
| Supply Chain: revisão de dependências | https://github.com/juliocataldo/supply-chain-lab |

## Para ler depois
- NIST SP 800-61 (resposta a incidentes) e NIST CSF 2.0 (funções Detect, Respond e Recover)
- Palantir, *Alerting and Detection Strategy Framework*
- SigmaHQ (regras de detecção abertas)
- Hutchins et al., *Intrusion Kill Chains* (2011)
