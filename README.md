# Plano de Experimento – Scoping e Planejamento
Disciplina: Engenharia de Software  
Projeto: Simulação e Visualização 3D da Dispersão de Poluentes em Ambientes Aquáticos  
ID / código: EXP-DP-01

## 1. Identificação básica

### 1.1 Título do experimento
Simulação e Validação de um Modelo de Difusão 2D com Visualização 3D Interativa.

### 1.2 Versão do documento e histórico de revisão
Versão: v1.0 (26/11/2025)  
Histórico: v1.0: Documento inicial com escopo, GQM e plano de execução.

### 1.3 Datas (criação, última atualização)
Criação: 26/11/2025  
Última atualização: 26/11/2025

### 1.4 Autores (nome, área, contato)
Autor principal: Victor Reis Carlota – Engenharia de Software

### 1.5 Responsável principal (PI / dono do experimento)
Responsável (PI): Victor Reis Carlota

### 1.6 Projeto / produto / iniciativa relacionada
Trabalho de conclusão / projeto acadêmico em Engenharia de Software com foco em modelagem numérica e visualização científica.

---

## 2. Contexto e problema

A dispersão de poluentes em corpos d'água é um problema ambiental que pode ser estudado por modelos simplificados (equação da difusão). O objetivo é construir um protótipo leve e interativo que permita simular, validar e visualizar a dispersão, integrado a técnicas e práticas de engenharia de software (versionamento, testes, documentação, usabilidade).

---

## 3. Objetivos e questões (Goal / Question / Metric - GQM)

Objetivo Geral: Desenvolver, validar e avaliar um protótipo que simula a dispersão de poluentes em 2D via equação da difusão, exporta mapas temporais e os integra a uma visualização 3D interativa, avaliando acurácia numérica, desempenho computacional e usabilidade.

### 3.1 Objetivos específicos (mín. 4)
- O1: Implementar numericamente a equação da difusão 2D (FTCS explícito) e validar a solução numérica.
- O2: Avaliar eficiência computacional e escalabilidade da simulação (tempo, memória).
- O3: Construir e avaliar uma visualização 3D interativa dos mapas de concentração.
- O4: Validar o modelo contra dados reais (quando disponíveis) e analisar sensibilidade a parâmetros.
- O5: Fornecer interface interativa com parâmetros ajustáveis e avaliar usabilidade/latência.

### 3.2 Tabela GQM (Objetivo | Perguntas | Métricas)
| Objetivo | Pergunta | Métricas (≥2 por pergunta) |
|---|---|---|
| O1: Implementação e validação numérica | Q1.1: Qual é o erro numérico frente à solução analítica (casos testáveis)? | M1 (Erro L2), M2 (Erro L∞) |
| O1 | Q1.2: A massa total do contaminante é preservada dentro de tolerância? | M3 (Erro de conservação de massa), M9 (RMSE vs dados reais quando aplicável) |
| O1 | Q1.3: Qual é a ordem de convergência ao refinar a malha? | M4 (Taxa de convergência), M5 (Margem de estabilidade / CFL) |
| O2: Eficiência e escalabilidade | Q2.1: Quanto tempo de CPU por passo e por simulação completa? | M6 (Tempo por passo), M7 (Tempo total de simulação) |
| O2 | Q2.2: Qual o uso de memória em diferentes tamanhos de grid? | M8 (Uso de memória), M14 (Número de elementos do grid) |
| O2 | Q2.3: Como varia o desempenho ao alterar resolução e Δt? | M6 (Tempo por passo), M4 (Taxa de convergência) |
| O3: Visualização 3D | Q3.1: A visualização mantém framerate aceitável em diferentes resoluções? | M11 (FPS na visualização), M8 (Uso de memória) |
| O3 | Q3.2: A latência de interação (zoom/rotac/seleção) é aceitável? | M12 (Latência de interação), M6 (Tempo por passo ao renderizar) |
| O3 | Q3.3: Qual a qualidade percebida da visualização pelos usuários? | M13 (Satisfação do usuário — Likert), M10 (Coef. de correlação espacial vs referência) |
| O4: Validação e sensibilidade | Q4.1: Quão bem o modelo reproduz padrões observados em dados reais? | M9 (RMSE vs dados reais), M10 (Coef. de correlação espacial) |
| O4 | Q4.2: Quais parâmetros (D, Δx, Δt, fonte) mais influenciam o resultado? | M15 (Sensibilidade relativa por parâmetro), M1 (Erro L2) |
| O4 | Q4.3: O modelo é robusto a pequenas perturbações nas condições iniciais? | M3 (Erro de conservação de massa), M15 (Sensibilidade relativa) |
| O5: Interface e usabilidade | Q5.1: Usuários ajustam parâmetros e entendem efeitos em tempo razoável? | M12 (Latência de interação), M13 (Satisfação do usuário) |
| O5 | Q5.2: A interface permite exportar mapas/frames sem perda de dados? | M7 (Tempo total para exportação), M8 (Uso de memória durante exportação) |
| O5 | Q5.3: Qual o esforço médio para produzir e visualizar um cenário? | M6 (Tempo por passo), M11 (FPS durante a sessão) |

Observação: cada objetivo contém no mínimo 3 perguntas; cada pergunta tem pelo menos duas métricas associadas. As métricas podem repetir entre perguntas; no total há ≥10 métricas distintas (definidas abaixo).

---

## 4. Métricas (descrição e unidade)

| Métrica | Descrição | Unidade |
|---|---:|---|
| M1 – Erro L2 | Norma L2 do vetor de diferença entre solução numérica e referência | mesma unidade de concentração |
| M2 – Erro L∞ | Erro máximo pontual entre solução numérica e referência | mesma unidade de concentração |
| M3 – Erro de conservação de massa | Variação percentual da massa total ao longo da simulação | % |
| M4 – Taxa de convergência | Estimativa da ordem de convergência ao refinar Δx | expoente (valor adimensional) |
| M5 – Margem de estabilidade (CFL) | Relação D·Δt/Δx^2 e verificação de condição estável | adimensional |
| M6 – Tempo por passo | Tempo médio de CPU/real por iteração de tempo | segundos |
| M7 – Tempo total de simulação / exportação | Tempo total para concluir uma simulação ou exportar dados | segundos / minutos |
| M8 – Uso de memória | Pico de memória durante simulação / visualização | MB |
| M9 – RMSE vs dados reais | Root Mean Square Error entre simulação e observações reais | mesma unidade de concentração |
| M10 – Coeficiente de correlação espacial | Correlação espacial (Pearson / Spearman) entre mapas simulados e referência | coeficiente (-1 a 1) |
| M11 – FPS na visualização | Frames por segundo mantidos pela cena 3D | frames/segundo |
| M12 – Latência de interação | Tempo de resposta a ações do usuário (ms) | milissegundos |
| M13 – Satisfação do usuário | Avaliação subjetiva (Likert 1–5) sobre usabilidade/qualidade | escala 1–5 |
| M14 – Número de elementos do grid | Quantidade de células na malha (nx * ny) | contagem |
| M15 – Sensibilidade relativa por parâmetro | Variação percentual na saída por variação percentual do parâmetro | % / % (razão) |

(Existem 15 métricas distintas definidas, atendendo ao requisito de ≥10 métricas diferentes.)

---

## 5. Escopo e contexto do experimento

### 5.1 Incluído
- Implementação do FTCS explícito em 2D, testes de validação (casos analíticos), cenários sintéticos e comparação com dados reais (quando disponíveis).
- Exportação de mapas (CSV/NetCDF), integração a visualização 3D (Three.js/Unity) e testes de usabilidade.
- Coleta automatizada de tempos, uso de memória e logs para reprodutibilidade.

### 5.2 Excluído
- Modelagem completa de dinâmica de fluidos (Navier–Stokes) e modelos turbulentos avançados.
- Comparação exaustiva entre múltiplas ferramentas comerciais.

---

## 6. Stakeholders e impacto esperado

- Estudantes e professores da disciplina de Engenharia de Software (uso educacional).
- Pesquisador/autor do projeto (executante).
- Comunidade acadêmica (repositório e reprodutibilidade).
Impacto: ferramenta demonstrativa, material de ensino, base para trabalhos futuros.

---

## 7. Riscos, premissas e critérios de sucesso

### 7.1 Riscos principais
- R1: Instabilidade numérica se Δt violar condição CFL.  
- R2: Dados reais indisponíveis ou incompatíveis.  
- R3: Má performance em hardware limitado.  
- R4: Baixa amostra em testes de usabilidade.

### 7.2 Premissas
- Ambiente de execução com Python 3.x, NumPy, e navegador com WebGL (Three.js) ou Unity instalado.
- Usuários testers com conhecimento básico de computação.

### 7.3 Critérios de sucesso
- Erro L2 aceitável em casos analíticos (ex.: <5%).
- FPS interativo ≥ 30 em cenários didáticos.
- Satisfação média do usuário ≥ 4/5.
- Exportação de mapas sem perda de informação.

---

## 8. Metodologia resumida e cronograma (sugestão para 3 meses)

1. Semana 1–2: Revisão teórica, definição de casos teste e infraestrutura.  
2. Semana 3–5: Implementação do solver FTCS e testes de validação analítica.  
3. Semana 6–7: Benchmarks de performance e profiling (tempo/memória).  
4. Semana 8–9: Construção da visualização 3D e integração de exportadores.  
5. Semana 10: Testes de usabilidade e coleta de feedback.  
6. Semana 11–12: Ajustes finais, documentação e elaboração do relatório.

---

## 9. Instrumentação e protocolo operacional (resumo)

- Scripts Python para simulação com logging de tempo e memória (timeit, memory-profiler).  
- Casos de validação analítica (p.ex. solução gaussiana) e cenários sintéticos.  
- Formulário de avaliação de usabilidade (Likert) e tarefas padronizadas para usuários.  
- Repositório Git com instruções reproducíveis e notebooks de demonstração.

---

## 10. Plano de análise de dados (resumo)

- Comparação de solução numérica vs referência com M1, M2 e M4.  
- Testes de desempenho: M6–M8, análise de escalabilidade com M14.  
- Validação com dados reais: M9 e M10.  
- Análise de usabilidade: M11–M13.  
- Sensibilidade: variação controlada de parâmetros e cálculo de M15.

---

## 11. Documentação e reprodutibilidade

- Código versionado em repositório público com README, scripts de reprodução e dados de exemplo.  
- Templates de exportação (CSV/NetCDF) e documentação de API/usuário.

---

## 12. Contatos e próximos passos

- Responsável: Victor Reis Carlota (disciplina: Engenharia de Software).  
Próximos passos: confirmar ferramentas (Three.js vs Unity), preparar casos analíticos e montar ambiente de desenvolvimento reprodutível.
