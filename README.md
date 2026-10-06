# SOC Hands-on - Console de Triagem

Exercício prático **sem nota** para vivenciar o dia a dia de um analista de SOC (nível 1).
Você assume o plantão da **OrbitaPay**, uma fintech **fictícia**, e precisa triar a fila de alertas.

> Todos os dados são sintéticos. Nenhum IP, domínio ou hash deste exercício existe de verdade.
> Não adianta pesquisar os IOCs na internet: use os botões **Consultar** do próprio console.

## Como abrir
1. Baixe a pasta e dê **duplo clique em `index.html`** (qualquer navegador atual).
2. Não precisa de internet nem de instalação.
3. Se quiser, digite seu nome/RM no topo (só aparece no relatório que você baixar).

## Seu objetivo
Triar os **12 alertas** da fila, em **30-40 minutos**. Em cada alerta:

1. **Leia a evidência** (logs) com atenção.
2. **Consulte os IOCs** (botão *Consultar*). Isso simula VirusTotal, AbuseIPDB, urlscan, CMDB etc.
3. **Decida o veredito:**
   - *Verdadeiro positivo*: atividade maliciosa de verdade;
   - *Falso positivo*: o alerta disparou, mas a atividade é legítima;
   - *Inconclusivo*: faltam evidências para decidir (e então?).
4. **Defina a severidade REAL.** Ela pode ser diferente da que o sistema atribuiu.
5. **Escolha a técnica MITRE ATT&CK** que melhor descreve o comportamento.
6. **Diga se o alerta se relaciona com outros** (faz parte de uma cadeia de ataque ou é isolado).
7. **Marque as ações de resposta** adequadas.
8. Escreva uma **justificativa curta** (1-2 linhas) e clique em **Registrar triagem**.

Depois de registrar, aparece a **análise de referência**. Ela mostra o que você acertou, o que errou e por quê. A triagem **não pode ser refeita** (o botão *Reiniciar* apaga tudo).

## Como funciona a pontuação
Não vale nota. Cada alerta dá até **5 pontos de aderência** (veredito, severidade, técnica, correlação, ações).
O objetivo é **aprender com os erros**, não "zerar" o placar.

## Botões do topo
| Botão | Para quê |
|---|---|
| **Relatório** | Baixa um `.md` com suas triagens e justificativas. |
| **Debrief** | Resumo do turno, linha do tempo e perguntas de discussão. Use ao final. |
| **Reiniciar** | Apaga as triagens e começa de novo. |

## Dicas (sem spoilers)
- **Ferramenta suspeita não é igual a ataque.** Pergunte sempre: *quem* executou, *de onde*, *em que horário*, *existe uma mudança aprovada*?
- **O contexto decide.** O mesmo comando pode ser rotina de TI num caso e invasão em outro.
- **Um IOC sozinho é um indício, não uma prova.** Procure um segundo ponto de evidência antes de concluir.
- **Correlacione.** Anote hosts, usuários, IPs, domínios e horários. Quando algo se repete entre alertas, pode ser o mesmo incidente.
- **Reavalie a severidade.** A do sistema é um ponto de partida. Pergunte: o ataque *funcionou*? Há dado sensível envolvido? O atacante já está dentro?
- **Ordem importa.** Num incidente ativo, o que você contém primeiro? E o que faz depois?
- **Controle que funcionou também é achado.** Se um ataque falhou, o que o barrou?
- **"Sem resultado" não é "limpo".** Um domínio novo pode simplesmente ainda não ter reputação.
- **Ação não é só bloquear.** Pense em quem precisa ser avisado, em contas, em e-mails já entregues e em configuração a corrigir.
- **Na dúvida, justifique.** Uma boa justificativa vale mais que um chute certo.

## Glossário rápido
| Sigla | Significado |
|---|---|
| **IOC** | Indicator of Compromise: IP, domínio, hash, URL etc. que indica atividade maliciosa. |
| **TP / FP** | True Positive / False Positive. |
| **EDR** | Endpoint Detection and Response: monitora e contém ameaças no computador. |
| **SIEM** | Plataforma que reúne e correlaciona logs de vários sistemas. |
| **DLP** | Data Loss Prevention: detecta saída indevida de dados. |
| **WAF** | Web Application Firewall. |
| **C2** | Command and Control: servidor que o atacante usa para controlar a máquina infectada. |
| **ATT&CK** | Base de conhecimento da MITRE com táticas e técnicas de atacantes. |
| **IR** | Incident Response: time ou processo de resposta a incidentes. |

## Combinados
- É um ambiente **de treino**: errar faz parte.
- Discuta com a dupla, mas **registre a sua própria triagem**.
- Não compartilhe o gabarito com quem ainda não fez.
- Os IOCs deste exercício **não são reais**: nunca os use para bloquear nada em ambiente de verdade.

## Confiança (metacognição)
Em cada decisão você informa **o quanto confia nela** (1 = chutei, 5 = tenho certeza). No Debrief você vê seus erros com **confiança alta**: são o ponto cego mais perigoso de um profissional de segurança, e o melhor lugar para estudar primeiro.

## Objetivos de aprendizagem
Ao final você será capaz de: **distinguir** verdadeiro e falso positivo usando contexto; **correlacionar** alertas em uma cadeia de ataque; **priorizar** pelo impacto real (não pela severidade do sistema); e **mapear** comportamentos a técnicas do MITRE ATT&CK.

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
- MITRE ATT&CK (attack.mitre.org)
- NIST SP 800-61 (Computer Security Incident Handling Guide)
- Bianco, D. *The Pyramid of Pain*
