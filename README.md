# **Título**

**Simulação e Visualização 3D da Dispersão de Poluentes em Ambientes Aquáticos Utilizando Modelo Simplificado de Difusão**

---

# **Resumo**

Este trabalho propõe o desenvolvimento de uma ferramenta de simulação e visualização 3D destinada a representar a dispersão de poluentes em corpos d’água, utilizando um modelo matemático simplificado baseado na equação da difusão. A proposta combina métodos numéricos computacionalmente leves com renderização tridimensional, permitindo analisar qualitativamente o comportamento de propagação de contaminantes. A abordagem foi escolhida por equilibrar relevância ambiental, fundamentação científica e viabilidade técnica em um período de três meses. Além disso, o projeto pode ser integrado a dados ambientais reais provenientes de bases como NOAA, Copernicus Marine Service e ANA, potencializando a análise e reforçando sua aplicabilidade em estudos ambientais e educacionais.

---

# **1. Introdução**

A dispersão de poluentes em ambientes aquáticos é um fenômeno de grande relevância científica e ambiental, especialmente em contextos de acidentes industriais, derramamentos de óleo e contaminação por efluentes. Grandes modelos de dinâmica de fluidos, como Navier–Stokes, oferecem descrições completas, porém são computacionalmente custosos e complexos, o que inviabiliza sua implementação em projetos de curto prazo.

Este trabalho busca uma solução intermediária, empregando um modelo simplificado — a equação da difusão — para descrever a propagação horizontal de um poluente em um corpo d’água. A simulação é então convertida em uma visualização tridimensional, aproveitando técnicas de modelagem e renderização 3D, tornando a análise mais intuitiva e envolvente, especialmente para fins de ensino ou demonstração.

A proposta permite ao estudante explorar simultaneamente modelagem matemática, programação, computação científica e visualização 3D, dentro de um escopo realista para o tempo disponível.

---

# **2. Objetivo Geral**

Desenvolver um sistema capaz de simular e visualizar em 3D a dispersão de um poluente em um corpo d’água utilizando um modelo matemático baseado na equação da difusão.

---

# **3. Objetivos Específicos**

* Implementar numericamente a equação da difusão em duas dimensões.
* Simular a evolução temporal da concentração de um poluente.
* Integrar os resultados a um ambiente 3D em Unity, Three.js ou Blender.
* Validar o comportamento qualitativo do modelo por meio de dados reais.
* Permitir interação visual (zoom, rotação, variação de parâmetros).
* Analisar o impacto de parâmetros como coeficiente de difusão e forma da fonte de poluição.

---

# **4. Fundamentação Teórica**

## **4.1 Dispersão de poluentes**

No ambiente aquático, a dispersão horizontal de substâncias é fortemente influenciada por difusão molecular e, principalmente, difusão turbulenta. Em escalas pequenas e médias, a difusão é um mecanismo dominante para a suavização de gradientes de concentração.

## **4.2 Equação da Difusão**

A equação da difusão em duas dimensões é dada por:

[
\frac{\partial C}{\partial t} = D\left( \frac{\partial^2 C}{\partial x^2} + \frac{\partial^2 C}{\partial y^2} \right),
]

onde:

* ( C(x,y,t) ) = concentração do poluente,
* ( D ) = coeficiente de difusão,
* ( x, y ) = coordenadas espaciais,
* ( t ) = tempo.

Esta equação descreve o espalhamento natural de uma substância de regiões de alta concentração para regiões de baixa concentração.

## **4.3 Métodos Numéricos**

A solução numérica será obtida via método de diferenças finitas, utilizando o esquema explícito FTCS (Forward Time, Centered Space):

[
C_{i,j}^{t+1} = C_{i,j}^{t}

* D \Delta t
  \left(
  \frac{C_{i+1,j}^t - 2C_{i,j}^t + C_{i-1,j}^t}{\Delta x^2}
*

\frac{C_{i,j+1}^t - 2C_{i,j}^t + C_{i,j-1}^t}{\Delta y^2}
\right)
]

O método é computacionalmente leve e adequado para simulações em tempo real.

---

# **5. Metodologia**

## **5.1 Etapas**

1. **Preparação do grid** (malha regular 2D).
2. **Definição das condições iniciais:** concentração inicial de poluente.
3. **Definição das condições de contorno:** fluxo zero ou borda absorvente.
4. **Implementação numérica da equação da difusão.**
5. **Execução da simulação temporal.**
6. **Exportação dos mapas de concentração como matrizes.**
7. **Construção da visualização 3D:** extrusão vertical proporcional à concentração.
8. **Renderização e interatividade.**

## **5.2 Tecnologias utilizadas**

* **Python** (NumPy, Matplotlib) ou JavaScript para a simulação.
* **Unity 3D**, **Three.js** ou **Blender** para visualização.
* **Bibliotecas de dataset:** xarray, netCDF4 (se usar dados NOAA).

---

# **6. Dados Utilizados**

O projeto poderá utilizar:

* **Copernicus Marine Service**: velocidades médias da água e difusividade.
* **NOAA**: casos reais de derramamento, batimetria e correntes.
* **ANA (Brasil)**: dados de qualidade da água (opcional).

Os dados podem servir como:

* condições iniciais,
* validação qualitativa,
* material para construir cenários reais em 3D.

---

# **7. Resultados Esperados**

* Representação visual clara da evolução da concentração.
* Cena 3D imersiva permitindo observar a dispersão no tempo.
* Gráficos e mapas da concentração simulada.
* Capacidade de alterar parâmetros e perceber diferenças de comportamento.
* Demonstração de que um modelo simples pode capturar padrões qualitativos da dispersão real.

---

# **8. Cronograma (3 meses)**

| Semana | Atividade                              |
| ------ | -------------------------------------- |
| 1–2    | Revisão teórica + escolha dos datasets |
| 3–4    | Implementação da simulação de difusão  |
| 5–6    | Testes numéricos e ajustes             |
| 7–9    | Construção da visualização 3D          |
| 10–11  | Integração simulação + 3D              |
| 12     | Produção do relatório e apresentação   |

---

# **9. Conclusão**

O projeto propõe uma solução simples, realista e viável para analisar e visualizar a dispersão de poluentes em água. Ao utilizar a equação da difusão como modelo matemático central, mantém-se rigor científico sem comprometer a viabilidade técnica dentro do período proposto. A visualização 3D acrescenta valor demonstrativo, educacional e exploratório ao trabalho, tornando-o acessível e impactante mesmo para públicos não técnicos.

---

# **10. Referências (exemplos)**

* CRANK, J. *The Mathematics of Diffusion.* Oxford University Press, 1975.
* NOAA – National Oceanic and Atmospheric Administration.
* COPERNICUS Marine Environment Monitoring Service.
* SMITH, R. *Environmental Modelling: An Introduction.* 2018.
* JENSEN, J. *OpenGL Insights for Scientific Visualization.* 2016.

---

