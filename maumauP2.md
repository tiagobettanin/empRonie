# Resumo Geral: Aulas 08 e 09 - Fundamentos de Controle

Com base no material das Aulas 08 e 09, aqui está um resumo geral da teoria, fórmulas e exemplos abordados.

---

### **Aula 08: Não Linearidades e Linearização**

**Teoria:**

* **Sistemas Lineares vs. Não Lineares:**
    * Um sistema é linear se sua saída for diretamente proporcional à sua entrada, o que é representado graficamente por uma linha reta.
    * Sistemas não lineares não obedecem a essa proporção. Muitos sistemas físicos reais são inerentemente não lineares.
* **Exemplos de Não Linearidades Comuns:**
    * **Saturação de Amplificador (Amplifier saturation):** A saída para de aumentar após a entrada atingir um certo nível.
    * **Zona Morta de Motor (Motor dead zone):** O sistema não responde a entradas abaixo de um certo limiar.
    * **Folga em Engrenagens (Backlash in gears):** Um tipo de histerese causada por folgas mecânicas.
* **Linearização:**
    * É uma técnica usada para aproximar o comportamento de um sistema não linear em torno de um ponto de operação específico (um ponto de equilíbrio).
    * A ideia é substituir a curva não linear pela linha tangente à curva naquele ponto. Isso permite usar as ferramentas de análise linear (como a Transformada de Laplace) para estudar o sistema para pequenas variações em torno desse ponto.

**Fórmulas:**

* **Equação Geral de Linearização:** A função não linear $f(x)$ é aproximada em torno do ponto $x_0$:
    * <img src="https://latex.codecogs.com/svg.latex?f(x) \approx f(x_0) + m_a(x-x_0)" alt="f(x) \approx f(x_0) + m_a(x-x_0)"/>
    * Onde $m_a$ é o coeficiente angular (a derivada) da função no ponto $x_0$: <img src="https://latex.codecogs.com/svg.latex?m_a = \frac{df(x)}{dx}|_{x=x_0}" alt="m_a = df(x)/dx em x=x_0"/>
* **Forma de Variação (Perturbação):** Definindo <img src="https://latex.codecogs.com/svg.latex?\delta x = (x-x_0)" alt="delta x = (x - x0)"/> e <img src="https://latex.codecogs.com/svg.latex?\delta f(x) = [f(x)-f(x_0)]" alt="delta f(x) = [f(x) - f(x0)]"/>, a fórmula se torna:
    * <img src="https://latex.codecogs.com/svg.latex?\delta f(x) \approx m_a \delta x" alt="delta f(x) \approx m_a * delta x"/>

**Exemplos:**

* **Linearização de Função (Exemplo 2.26):**
    * **Problema:** Linearizar <img src="https://latex.codecogs.com/svg.latex?f(x) = 5 \cos(x)" alt="f(x) = 5 cos(x)"/> em torno de <img src="https://latex.codecogs.com/svg.latex?x = \pi/2" alt="x = pi/2"/>.
    * **Solução:** A derivada é <img src="https://latex.codecogs.com/svg.latex?\frac{df}{dx} = -5 \sin(x)" alt="df/dx = -5 sin(x)"/>. No ponto <img src="https://latex.codecogs.com/svg.latex?x = \pi/2" alt="x = pi/2"/>, o coeficiente angular é $Slope = -5$. A função linearizada para pequenas variações <img src="https://latex.codecogs.com/svg.latex?\delta x" alt="delta x"/> é <img src="https://latex.codecogs.com/svg.latex?f(x) = -5\delta x" alt="f(x) = -5*delta x"/>.
* **Linearização de Equação Diferencial (Exemplo 2.27):**
    * **Problema:** Linearizar <img src="https://latex.codecogs.com/svg.latex?\frac{d^{2}x}{dt^{2}}+2\frac{dx}{dt}+\cos x=0" alt="d^2x/dt^2 + 2dx/dt + cos(x) = 0"/> em torno de <img src="https://latex.codecogs.com/svg.latex?x = \pi/4" alt="x = pi/4"/>.
    * **Solução:** O termo não linear <img src="https://latex.codecogs.com/svg.latex?\cos(x)" alt="cos(x)"/> é linearizado como <img src="https://latex.codecogs.com/svg.latex?\cos(\delta x+\frac{\pi}{4}) \approx \cos(\frac{\pi}{4})-\sin(\frac{\pi}{4})\delta x" alt="cos(delta x + pi/4) \approx cos(pi/4) - sin(pi/4)*delta x"/>. A equação diferencial linearizada resultante é <img src="https://latex.codecogs.com/svg.latex?\frac{d^{2}\delta x}{dt^{2}}+2\frac{d\delta x}{dt}-\frac{\sqrt{2}}{2}\delta x = -\frac{\sqrt{2}}{2}" alt="d^2(delta x)/dt^2 + 2d(delta x)/dt - (sqrt(2)/2)*delta x = -sqrt(2)/2"/>.
* **Linearização de Circuito Elétrico (Exemplo 2.28):**
    * **Problema:** Encontrar a função de transferência de um circuito com um resistor não linear <img src="https://latex.codecogs.com/svg.latex?i_r = 2e^{0.1v_r}" alt="i_r = 2e^(0.1v_r)"/>.
    * **Solução:** A equação do circuito <img src="https://latex.codecogs.com/svg.latex?L\frac{di}{dt} + 10\ln(\frac{1}{2}i) - 20 = v(t)" alt="Ldi/dt + 10ln(1/2*i) - 20 = v(t)"/> é linearizada. O termo não linear é linearizado em torno do ponto de operação <img src="https://latex.codecogs.com/svg.latex?i_0 = 14.78" alt="i_0 = 14.78"/>. Isso resulta em uma equação diferencial linear <img src="https://latex.codecogs.com/svg.latex?\frac{d\delta i}{dt} + 0.677\delta i = v(t)" alt="d(delta i)/dt + 0.677*delta i = v(t)"/>, que leva à função de transferência <img src="https://latex.codecogs.com/svg.latex?\frac{V_L(s)}{V(s)} = \frac{s}{s+0.677}" alt="V_L(s)/V(s) = s / (s + 0.677)"/>.

---

### **Aula 09: Polos, Zeros e a Resposta do Sistema**

**Teoria:**

* **Polos e Zeros:**
    * **Polos:** São as raízes do denominador da função de transferência. Eles ditam a resposta natural (o comportamento intrínseco) do sistema.
    * **Zeros:** São as raízes do numerador da função de transferência. Eles afetam a amplitude (os resíduos) dos termos da resposta.
* **Resposta Forçada vs. Resposta Natural:**
    * A resposta total de um sistema <img src="https://latex.codecogs.com/svg.latex?c(t)" alt="c(t)"/> é a soma de duas partes.
    * **Resposta Forçada:** É a parte da resposta devida aos polos da entrada (ex: o polo em <img src="https://latex.codecogs.com/svg.latex?s=0" alt="s=0"/> de uma entrada degrau). Ela dita o comportamento em regime permanente.
    * **Resposta Natural:** É a parte da resposta devida aos polos do sistema. Ela dita o comportamento transitório (como o sistema chega ao regime permanente).

#### **Sistemas de Primeira Ordem**

* **Forma Padrão:** <img src="https://latex.codecogs.com/svg.latex?G(s) = \frac{a}{s+a}" alt="G(s) = a / (s + a)"/>
* **Resposta ao Degrau:** <img src="https://latex.codecogs.com/svg.latex?c(t) = 1 - e^{-at}" alt="c(t) = 1 - e^(-at)"/>
* **Métricas de Desempenho:**
    * **Constante de Tempo (<img src="https://latex.codecogs.com/svg.latex?T_c" alt="T_c"/>):** <img src="https://latex.codecogs.com/svg.latex?T_c = 1/a" alt="T_c = 1/a"/>. É o tempo para a resposta atingir 63% do valor final.
    * **Tempo de Subida (<img src="https://latex.codecogs.com/svg.latex?T_r" alt="T_r"/>):** Tempo para ir de 10% a 90% do valor final. <img src="https://latex.codecogs.com/svg.latex?T_r = \frac{2.2}{a}" alt="T_r = 2.2 / a"/>
    * **Tempo de Acomodação (<img src="https://latex.codecogs.com/svg.latex?T_s" alt="T_s"/>):** Tempo para a resposta ficar dentro de 2% do valor final. <img src="https://latex.codecogs.com/svg.latex?T_s = \frac{4}{a}" alt="T_s = 4 / a"/>

#### **Sistemas de Segunda Ordem**

* **Formas Padrão:**
    * Geral: <img src="https://latex.codecogs.com/svg.latex?G(s) = \frac{b}{s^2 + as + b}" alt="G(s) = b / (s^2 + as + b)"/>
    * Parametrizada: <img src="https://latex.codecogs.com/svg.latex?G(s) = \frac{\omega_n^2}{s^2 + 2\zeta\omega_n s + \omega_n^2}" alt="G(s) = omega_n^2 / (s^2 + 2*zeta*omega_n*s + omega_n^2)"/>
* **Parâmetros Fundamentais:**
    * **Frequência Natural (<img src="https://latex.codecogs.com/svg.latex?\omega_n" alt="omega_n"/>):** A frequência de oscilação do sistema sem amortecimento. <img src="https://latex.codecogs.com/svg.latex?\omega_n = \sqrt{b}" alt="omega_n = sqrt(b)"/>
    * **Fator de Amortecimento (<img src="https://latex.codecogs.com/svg.latex?\zeta" alt="zeta"/>):** Controla a natureza da resposta. <img src="https://latex.codecogs.com/svg.latex?a=2\zeta\omega_{n}" alt="a = 2*zeta*omega_n"/> ou <img src="https://latex.codecogs.com/svg.latex?\zeta = \frac{a}{2\omega_n}" alt="zeta = a / (2*omega_n)"/>

* **Tipos de Resposta (baseado nos polos e em <img src="https://latex.codecogs.com/svg.latex?\zeta" alt="zeta"/>):**
    1.  **Superamortecida (<img src="https://latex.codecogs.com/svg.latex?\zeta > 1" alt="zeta > 1"/>):**
        * **Polos:** Dois polos reais e distintos.
        * **Resposta:** Soma de duas exponenciais, sem oscilação. <img src="https://latex.codecogs.com/svg.latex?c(t) = K_1e^{-\sigma_1 t} + K_2e^{-\sigma_2 t}" alt="c(t) = K1*e^(-sigma1*t) + K2*e^(-sigma2*t)"/>
    2.  **Subamortecida (<img src="https://latex.codecogs.com/svg.latex?0 < \zeta < 1" alt="0 < zeta < 1"/>):**
        * **Polos:** Um par de polos complexos conjugados.
        * **Resposta:** Uma senóide amortecida. <img src="https://latex.codecogs.com/svg.latex?c(t) = Ae^{-\sigma_d t}\cos(\omega_d t - \phi)" alt="c(t) = A*e^(-sigma_d*t)*cos(omega_d*t - phi)"/>. A parte real (<img src="https://latex.codecogs.com/svg.latex?\sigma_d" alt="sigma_d"/>) gera o decaimento exponencial, e a parte imaginária (<img src="https://latex.codecogs.com/svg.latex?\omega_d" alt="omega_d"/>) gera a oscilação.
    3.  **Criticamente Amortecida (<img src="https://latex.codecogs.com/svg.latex?\zeta = 1" alt="zeta = 1"/>):**
        * **Polos:** Dois polos reais e iguais.
        * **Resposta:** A resposta mais rápida possível sem ultrapassagem. <img src="https://latex.codecogs.com/svg.latex?c(t) = K_1e^{-\sigma_1 t} + K_2te^{-\sigma_1 t}" alt="c(t) = K1*e^(-sigma1*t) + K2*t*e^(-sigma1*t)"/>
    4.  **Não Amortecida (<img src="https://latex.codecogs.com/svg.latex?\zeta = 0" alt="zeta = 0"/>):**
        * **Polos:** Um par de polos imaginários puros.
        * **Resposta:** Uma senóide pura (oscilação sustentada). <img src="https://latex.codecogs.com/svg.latex?c(t) = A\cos(\omega_1 t - \phi)" alt="c(t) = A*cos(omega1*t - phi)"/>

* **Métricas de Desempenho (para Sistemas Subamortecidos):**
    * **Instante de Pico (<img src="https://latex.codecogs.com/svg.latex?T_p" alt="T_p"/>):** Tempo para atingir o primeiro pico máximo.
        * <img src="https://latex.codecogs.com/svg.latex?T_p = \frac{\pi}{\omega_n\sqrt{1-\zeta^2}}" alt="T_p = pi / (omega_n * sqrt(1-zeta^2))"/> ou <img src="https://latex.codecogs.com/svg.latex?T_p = \frac{\pi}{\omega_d}" alt="T_p = pi / omega_d"/>
    * **Ultrapassagem Percentual (%UP):** O quanto a resposta ultrapassa o valor final.
        * <img src="https://latex.codecogs.com/svg.latex?\%UP=100 \times e^{-(\zeta\pi/\sqrt{1-\zeta^{2}})}" alt="%UP = 100 * exp(-(zeta*pi) / sqrt(1-zeta^2))"/>
    * **Tempo de Acomodação (<img src="https://latex.codecogs.com/svg.latex?T_s" alt="T_s"/>):** Tempo para ficar dentro de $\pm$2% do valor final.
        * <img src="https://latex.codecogs.com/svg.latex?T_s = \frac{4}{\zeta\omega_n}" alt="T_s = 4 / (zeta*omega_n)"/> ou <img src="https://latex.codecogs.com/svg.latex?T_s = \frac{4}{\sigma_d}" alt="T_s = 4 / sigma_d"/>
    * **Tempo de Subida (<img src="https://latex.codecogs.com/svg.latex?T_r" alt="T_r"/>):** Tempo de 10% a 90% do valor final. É obtido a partir de gráficos ou tabelas.

**Exemplos:**

* **Exemplo 4.4:** Classificar sistemas com base em <img src="https://latex.codecogs.com/svg.latex?\zeta" alt="zeta"/>.
    * <img src="https://latex.codecogs.com/svg.latex?G(s) = \frac{12}{s^2+8s+12}" alt="G(s) = 12 / (s^2 + 8s + 12)"/> $\implies$ <img src="https://latex.codecogs.com/svg.latex?\zeta=1.155" alt="zeta = 1.155"/> (Superamortecido).
    * <img src="https://latex.codecogs.com/svg.latex?G(s) = \frac{16}{s^2+8s+16}" alt="G(s) = 16 / (s^2 + 8s + 16)"/> $\implies$ <img src="https://latex.codecogs.com/svg.latex?\zeta=1" alt="zeta = 1"/> (Criticamente Amortecido).
    * <img src="https://latex.codecogs.com/svg.latex?G(s) = \frac{20}{s^2+8s+20}" alt="G(s) = 20 / (s^2 + 8s + 20)"/> $\implies$ <img src="httpsK" alt="zeta = 0.894"/> (Subamortecido).
* **Exemplo 4.5:** Calcular métricas a partir da função de transferência.
    * **Problema:** <img src="https://latex.codecogs.com/svg.latex?G(s) = \frac{100}{s^2+15s+100}" alt="G(s) = 100 / (s^2 + 15s + 100)"/>.
    * **Solução:** Calcula-se <img src="https://latex.codecogs.com/svg.latex?\omega_n=10" alt="omega_n = 10"/> e <img src="https://latex.codecogs.com/svg.latex?\zeta=0.75" alt="zeta = 0.75"/>. Usando as fórmulas, obtém-se <img src="https://latex.codecogs.com/svg.latex?T_p=0.475" alt="T_p = 0.475"/>s, <img src="https://latex.codecogs.com/svg.latex?\%UP=2.838" alt="%UP = 2.838"/> e <img src="https://latex.codecogs.com/svg.latex?T_s=0.533" alt="T_s = 0.533"/>s.

---

### Tabela de Fórmulas e Definições (Aulas 08 e 09)

| Categoria | Fórmula (como Imagem) | Descrição | Aula |
| :--- | :--- | :--- | :--- |
| **Linearização** | <img src="https://latex.codecogs.com/svg.latex?f(x) \approx f(x_0) + m_a(x-x_0)" alt="f(x) \approx f(x_0) + m_a(x-x_0)"/> | Aproxima uma função não linear $f(x)$ pela sua reta tangente no ponto de operação $x_0$. | 08 |
| **Linearização** | <img src="https://latex.codecogs.com/svg.latex?m_a = \frac{df(x)}{dx}|_ {x=x_0}" alt="m_a = df(x)/dx em x=x_0"/> | Coeficiente angular (derivada) da reta tangente usada para a linearização. | 08 |
| **Linearização** | <img src="https://latex.codecogs.com/svg.latex?\delta f(x) \approx m_a \delta x" alt="delta f(x) \approx m_a * delta x"/> | Relação linearizada que associa a pequena variação na saída ($\delta f(x)$) à pequena variação na entrada ($\delta x$). | 08 |
| **1ª Ordem** | <img src="https://latex.codecogs.com/svg.latex?G(s) = \frac{a}{s+a}" alt="G(s) = a / (s + a)"/> | Forma padrão da função de transferência de um sistema de primeira ordem. | 09 |
| **1ª Ordem** | <img src="https://latex.codecogs.com/svg.latex?c(t)=1-e^{-at}" alt="c(t) = 1 - e^(-at)"/> | Resposta ao degrau unitário no domínio do tempo para o sistema de primeira ordem padrão. | 09 |
| **1ª Ordem** | <img src="https://latex.codecogs.com/svg.latex?T_c = 1/a" alt="T_c = 1/a"/> | **Constante de Tempo ($T_c$):** Tempo para a resposta atingir 63% do valor final. | 09 |
| **1ª Ordem** | <img src="https://latex.codecogs.com/svg.latex?T_{r}=\frac{2.2}{a}" alt="T_r = 2.2 / a"/> | **Tempo de Subida ($T_r$):** Tempo para a resposta ir de 10% a 90% do valor final. | 09 |
| **1ª Ordem** | <img src="https://latex.codecogs.com/svg.latex?T_{s}=\frac{4}{a}" alt="T_s = 4 / a"/> | **Tempo de Acomodação ($T_s$):** Tempo para a resposta ficar dentro de $\pm$2% do valor final. | 09 |
| **2ª Ordem** | <img src="https://latex.codecogs.com/svg.latex?G(s) = \frac{b}{s^2 + as + b}" alt="G(s) = b / (s^2 + as + b)"/> | Forma geral da função de transferência de um sistema de segunda ordem. | 09 |
| **2ª Ordem** | <img src="https://latex.codecogs.com/svg.latex?G(s)=\frac{\omega_{n}^{2}}{s^{2}+2\zeta\omega_{n}s+\omega_{n}^{2}}" alt="G(s) = omega_n^2 / (s^2 + 2*zeta*omega_n*s + omega_n^2)"/> | Forma parametrizada padrão de uma função de transferência de segunda ordem. | 09 |
| **2ª Ordem** | <img src="https://latex.codecogs.com/svg.latex?\omega_{n}=\sqrt{b}" alt="omega_n = sqrt(b)"/> | **Frequência Natural ($\omega_n$):** Frequência de oscilação do sistema sem amortecimento. | 09 |
| **2ª Ordem** | <img src="https://latex.codecogs.com/svg.latex?\zeta = \frac{a}{2\omega_n}" alt="zeta = a / (2*omega_n)"/> | **Fator de Amortecimento ($\zeta$):** Parâmetro adimensional que define a natureza da resposta. | 09 |
| **2ª Ordem (Respostas)** | <img src="https://latex.codecogs.com/svg.latex?c(t)=K_{1}e^{-\sigma_{1}t}+K_{2}e^{-\sigma_{2}t}" alt="c(t) = K1*e^(-sigma1*t) + K2*e^(-sigma2*t)"/> | Forma geral da resposta **Superamortecida** ($\zeta > 1$). | 09 |
| **2ª Ordem (Respostas)** | <img src="https://latex.codecogs.com/svg.latex?c(t)=Ae^{-\sigma_{d}t}\cos(\omega_{d}t-\phi)" alt="c(t) = A*e^(-sigma_d*t)*cos(omega_d*t - phi)"/> | Forma geral da resposta **Subamortecida** ($0 < \zeta < 1$). | 09 |
| **2ª Ordem (Respostas)** | <img src="https://latex.codecogs.com/svg.latex?c(t)=K_{1}e^{-\sigma_{1}t}+K_{2}te^{-\sigma_{1}t}" alt="c(t) = K1*e^(-sigma1*t) + K2*t*e^(-sigma1*t)"/> | Forma geral da resposta **Criticamente Amortecida** ($\zeta = 1$). | 09 |
| **2ª Ordem (Respostas)** | <img src="https://latex.codecogs.com/svg.latex?c(t)=A \cos(\omega_{1}t-\phi)" alt="c(t) = A*cos(omega1*t - phi)"/> | Forma geral da resposta **Não Amortecida** ($\zeta = 0$). | 09 |
| **2ª Ordem (Métricas)** | <img src="https://latex.codecogs.com/svg.latex?T_p = \frac{\pi}{\omega_n\sqrt{1-\zeta^{2}}}" alt="T_p = pi / (omega_n * sqrt(1-zeta^2))"/> | **Instante de Pico ($T_p$):** Tempo para atingir o primeiro pico (para sistemas subamortecidos). | 09 |
| **2ª Ordem (Métricas)** | <img src="https://latex.codecogs.com/svg.latex?\%UP=100 \times e^{-(\zeta\pi/\sqrt{1-\zeta^{2}})}" alt="%UP = 100 * exp(-(zeta*pi) / sqrt(1-zeta^2))"/> | **Ultrapassagem Percentual (%UP):** Pico máximo acima do valor final (para sistemas subamortecidos). | 09 |
| **2ª Ordem (Métricas)** | <img src="https://latex.codecogs.com/svg.latex?T_s = \frac{4}{\zeta\omega_n}" alt="T_s = 4 / (zeta*omega_n)"/> | **Tempo de Acomodação ($T_s$):** Tempo para ficar dentro de $\pm$2% do valor final. | 09 |
| **2ª Ordem (Métricas)** | <img src="https://latex.codecogs.com/svg.latex?\omega_d = \omega_n\sqrt{1-\zeta^2}" alt="omega_d = omega_n * sqrt(1-zeta^2)"/> | **Frequência Amortecida ($\omega_d$):** A frequência de oscilação real de um sistema subamortecido. | 09 |
| **2ª Ordem (Métricas)** | <img src="https://latex.codecogs.com/svg.latex?\sigma_d = \zeta\omega_n" alt="sigma_d = zeta * omega_n"/> | **Decaimento Exponencial ($\sigma_d$):** A parte real do polo subamortecido, que define a velocidade de decaimento. | 09 |
| **2ª Ordem (Métricas)** | <img src="https://latex.codecogs.com/svg.latex?T_p = \frac{\pi}{\omega_d}" alt="T_p = pi / omega_d"/> | Forma alternativa para o Instante de Pico, usando a frequência amortecida. | 09 |
| **2ª Ordem (Métricas)** | <img src="httpsG" alt="T_s = 4 / sigma_d"/> | Forma alternativa para o Tempo de Acomodação, usando o fator de decaimento. | 09 |

#Aula 10

# Aula 10: Redução de Subsistemas e Análise de Resposta Transitória

Este documento resume os conceitos de redução de diagramas de blocos e a subsequente análise de resposta transitória de sistemas de controle.

## 1\. Redução de Diagramas de Blocos

O objetivo principal é simplificar um diagrama de sistema complexo em uma única função de transferência, $T(s) = C(s) / R(s)$.

### 1.1. Blocos em Série

  * **Descrição:** Blocos conectados sequencialmente, onde a saída de um é a entrada do próximo.
  * **Regra:** Multiplicam-se as funções de transferência.
  * **Equivalente:** $G_{eq}(s) = G_1(s) \cdot G_2(s) \cdot G_3(s)$

<!-- end list -->

```mermaid
graph LR
    R(s) --> G1[G1(s)] --> G2[G2(s)] --> G3[G3(s)] --> C(s);
```

*Equivale a:*

```mermaid
graph LR
    R(s) --> G_eq[G1(s)G2(s)G3(s)] --> C(s);
```

### 1.2. Blocos em Paralelo

  * **Descrição:** Blocos que partem do mesmo sinal de entrada e têm suas saídas somadas (ou subtraídas).
  * **Regra:** Somam-se (ou subtraem-se) as funções de transferência.
  * **Equivalente:** $G_{eq}(s) = \pm G_1(s) \pm G_2(s) \pm G_3(s)$

<!-- end list -->

```mermaid
graph TD
    R(s) -- " " --> G1[G1(s)];
    R(s) -- " " --> G2[G2(s)];
    R(s) -- " " --> G3[G3(s)];
    G1 --> S(Σ);
    G2 --> S;
    G3 --> S;
    S --> C(s);
```

*Equivale a:*

```mermaid
graph LR
    R(s) --> G_eq[±G1(s) ±G2(s) ±G3(s)] --> C(s);
```

### 1.3. Malha de Realimentação (Feedback)

  * **Descrição:** A topologia mais comum, onde a saída $C(s)$ é "amostrada" por $H(s)$ e realimentada para o somador de entrada. $G(s)$ é o caminho direto e $H(s)$ é o caminho de realimentação.
  * **Regra:** Esta é a fórmula de redução de malha fechada.
  * **Equivalente:** $G_{eq}(s) = \frac{G(s)}{1 \pm G(s)H(s)}$
      * **Nota:** O sinal no denominador (1 **±** ...) é **oposto** ao sinal no somador de realimentação. A maioria dos sistemas de controle usa realimentação negativa (sinal `-` no somador), resultando em `1 + G(s)H(s)` no denominador.

-----

## 2\. Análise de Resposta Transitória (Sistemas de 2ª Ordem)

Após reduzir um diagrama de blocos (especialmente um com realimentação), frequentemente obtemos uma função de transferência de segunda ordem.

**Forma Típica (Ex: Exemplo 5.4):**
$$T(s) = \frac{K}{s^2 + as + K}$$

**Forma Padrão (para análise):**
$$T(s) = \frac{\omega_n^2}{s^2 + 2\zeta\omega_n s + \omega_n^2}$$

Comparando as duas formas, podemos extrair os parâmetros-chave do sistema.

### 2.1. Parâmetros Fundamentais

  * **$\omega_n$ (Frequência Natural):** A frequência com que o sistema oscilaria se não houvesse amortecimento ($\zeta=0$).
      * Comparando $T(s)$: $\omega_n^2 = K \implies \omega_n = \sqrt{K}$
  * **$\zeta$ (Zeta - Fator de Amortecimento):** Determina o tipo de resposta (subamortecida, crítica, etc.).
      * Comparando $T(s)$: $2\zeta\omega_n = a \implies \zeta = a / (2\omega_n)$

### 2.2. Métricas de Desempenho (para $\zeta < 1$)

Para um sistema **subamortecido** ($0 < \zeta < 1$), que é o único caso que oscila e tem ultrapassagem, podemos calcular:

  * **%OS (Ultrapassagem Percentual / %UP):** O quanto o sistema ultrapassa o valor final.
      * $\%OS = 100 \cdot e^{\frac{-\zeta \pi}{\sqrt{1 - \zeta^2}}}$
  * **$T_s$ (Tempo de Acomodação):** O tempo para a resposta ficar dentro de 2% do valor final.
      * $T_s = \frac{4}{\zeta\omega_n}$
      * Também definido como $T_s = 4 / \sigma_d$, onde $\sigma_d = \zeta\omega_n$ é a parte real dos polos.
  * **$T_p$ (Tempo de Pico):** O tempo para atingir o primeiro pico (o máximo da ultrapassagem).
      * $T_p = \frac{\pi}{\omega_n \sqrt{1 - \zeta^2}}$
      * Também definido como $T_p = \pi / \omega_d$, onde $\omega_d = \omega_n \sqrt{1-\zeta^2}$ é a parte imaginária dos polos.

-----

## 3\. Exemplos da Aula

### 3.1. Exemplo 5.3: Análise de Resposta

  * **Problema:** Para o sistema com $G(s) = \frac{25}{s(s+5)}$ e realimentação unitária, encontrar $T_p$, %OS e $T_s$.
  * **Solução:**
    1.  **FTMF:** $T(s) = \frac{G}{1+G} = \frac{25 / (s(s+5))}{1 + 25 / (s(s+5))} = \frac{25}{s^2 + 5s + 25}$
    2.  **Parâmetros:**
          * $\omega_n^2 = 25 \implies \omega_n = 5$
          * $2\zeta\omega_n = 5 \implies 2 \cdot \zeta \cdot 5 = 5 \implies \zeta = 0.5$
    3.  **Métricas:** (Sistema subamortecido, pois $\zeta < 1$)
          * %OS = 16.3%
          * $T_s = 4 / (\zeta\omega_n) = 4 / (0.5 \cdot 5) = 1.6 \text{ s}$
          * $T_p = \pi / (\omega_n \sqrt{1 - \zeta^2}) = \pi / (5 \sqrt{1 - 0.5^2}) = 0.726 \text{ s}$

### 3.2. Exemplo 5.4: Projeto de Ganho

  * **Problema:** Para o sistema com $G(s) = \frac{K}{s(s+5)}$, determinar $K$ para uma ultrapassagem de 10%.
  * **Solução:**
    1.  **FTMF:** $T(s) = \frac{K}{s^2 + 5s + K}$
    2.  **Relações:** $2\zeta\omega_n = 5$ e $\omega_n = \sqrt{K}$.
    3.  **Relação $\zeta$-K:** Substituindo $\omega_n$, temos $\zeta = 5 / (2\sqrt{K})$.
    4.  **Meta:** Uma ultrapassagem de 10% exige (pela fórmula de %OS) um $\zeta \approx 0.591$.
    5.  **Resultado:** $0.591 = 5 / (2\sqrt{K}) \implies K = (5 / (2 \cdot 0.591))^2 \approx 17.9$.

-----

## 4\. Tópicos da Lista de Exercícios

A lista de exercícios aplica diretamente esses conceitos:

  * **Exercício 11 (Fig. P5.11):** Pede para encontrar %UP, Ts e Tp para $G(s) = \frac{225}{s(s+15)}$. (Idêntico ao Exemplo 5.3).
  * **Exercício 14 (Fig. P5.14):** Pede para encontrar $K$ para 10% de %UP para $G(s) = \frac{K}{s(s+30)}$. (Idêntico ao Exemplo 5.4).
  * **Exercício 15 (Fig. P5.15):** Pede para projetar $K$ e $a$ em $G(s) = \frac{K}{s(s+a)}$ para atingir metas de Ts e %UP.
  * **Exercício 16 (Fig. P5.16):** Um problema de projeto mais avançado onde é preciso encontrar $K_1$ (ganho) e $K_2s$ (realimentação de tacômetro) para atingir metas de Tp e Ts.
  * **Exercício 17 (Fig. P5.17):** Um exercício completo. Primeiro, pede para **reduzir** um diagrama de blocos complexo a uma única $T(s)$. Depois, pede para **analisar** essa $T(s)$ e encontrar todas as métricas (ζ, ωn, %UP, Ts, Tp, etc.).

#Aula 11

Aqui está o apanhado completo da "Aula 11 - Estabilidade", formatado em Markdown e sem os ``, pronto para ser usado no GitHub.

---

# Apanhado da Aula 11: Estabilidade

A "Aula 11" foca em um dos conceitos mais importantes da engenharia de controle: determinar se um sistema é estável, instável ou marginalmente estável. A aula explica as definições de estabilidade e introduz o **Critério de Estabilidade de Routh-Hurwitz** como a principal ferramenta de análise.

## 1. Definições de Estabilidade

A estabilidade de um sistema pode ser definida de duas maneiras principais:

* **Baseado na Resposta Natural** (a resposta do sistema a si mesmo, sem entradas):
    * **Sistema Estável:** A resposta natural tende a zero à medida que o tempo tende ao infinito.
    * **Sistema Instável:** A resposta natural tende ao infinito à medida que o tempo tende ao infinito.
    * **Sistema Marginalmente Estável:** A resposta natural não decai nem cresce, mas permanece constante ou oscila indefinidamente.

* **Baseado na Resposta Total (BIBO - Bounded-Input, Bounded-Output):**
    * **Sistema Estável (BIBO):** Toda entrada limitada (finita) gera uma saída limitada (finita).
    * **Sistema Instável (BIBO):** Existe pelo menos uma entrada limitada que gera uma saída ilimitada (infinita).

## 2. Estabilidade e os Polos do Sistema

A estabilidade de um sistema é determinada **exclusivamente** pela localização dos **polos** da sua função de transferência de malha fechada no plano-s:

* **Semi-Plano Esquerdo (LHP):** Polos com parte real negativa (ex: -2.672, -0.164).
    * **Resultado:** Sistema **ESTÁVEL**. A resposta decai com o tempo.
* **Semi-Plano Direito (RHP):** Polos com parte real positiva (ex: +0.0434).
    * **Resultado:** Sistema **INSTÁVEL**. A resposta cresce exponencialmente ao infinito.
* **Eixo Imaginário ($j\omega$):** Polos com parte real nula (polos na origem ou pares imaginários puros).
    * **Resultado:** Sistema **MARGINALMENTE ESTÁVEL** (se os polos não forem repetidos).

## 3. O Critério de Estabilidade de Routh-Hurwitz

O Critério de Routh-Hurwitz é um método poderoso que permite determinar **quantos polos** estão no RHP **sem ter que calcular** as raízes do polinômio do denominador.

A análise é feita construindo-se uma tabela (Tabela de Routh) a partir dos coeficientes do polinômio do denominador da função de transferência de malha fechada.

**Regra Principal:**
O número de **trocas de sinal** na **primeira coluna** da Tabela de Routh é exatamente igual ao número de **polos no semi-plano direito (RHP)**.

* No **Exemplo 6.1**, o polinômio $s^{3}+10s^{2}+31s+1030$ resultou em uma primeira coluna com `[1, 10, -72, 1030]`.
* Isso apresenta **duas trocas de sinal** (de 10 para -72, e de -72 para 1030).
* **Conclusão:** O sistema tem 2 polos no RHP e é **instável**.

## 4. Casos Especiais do Critério de Routh-Hurwitz

Existem duas situações especiais que exigem procedimentos diferentes:

### Caso 1: Zero Apenas na Primeira Coluna

* **O Problema:** Um `0` aparece na primeira coluna (Exemplo 6.2), o que causaria uma divisão por zero no cálculo da próxima linha.
* **A Solução (Método do Épsilon):** O zero é substituído por um número muito pequeno e positivo, **$\epsilon$**. A tabela é concluída usando $\epsilon$, e os sinais da primeira coluna são analisados fazendo o limite de $\epsilon \to 0^+$.

### Caso 2: Uma Linha Inteira de Zeros

* **O Problema:** Uma linha inteira da tabela se torna zero (Exemplo 6.4).
* **O Significado:** Isso indica que o polinômio possui raízes **simétricas em relação à origem** (ex: $s = \pm 2$ ou $s = \pm j5$ ou $s = \pm 1 \pm j3$).
* **A Solução (Polinômio Auxiliar):**
    1.  Forma-se um **Polinômio Auxiliar, $P(s)$**, com os coeficientes da linha *acima* da linha de zeros.
    2.  Calcula-se a **derivada** desse polinômio, $\frac{dP(s)}{ds}$.
    3.  Os coeficientes da derivada são usados para **substituir** a linha de zeros, e a tabela continua.

## 5. Aplicação: Projeto de Estabilidade (Exemplo 6.9)

O critério de Routh-Hurwitz é usado para "Projeto de Estabilidade", onde se determina a **faixa de valores de um ganho $K$** que torna o sistema estável.

* **Problema:** Encontrar $K$ para $G(s)=\frac{K}{s(s+7)(s+11)}$.
* **Método:**
    1.  Encontra-se o polinômio do denominador de malha fechada, que incluirá $K$: $s^{3}+18s^{2}+77s+K$.
    2.  Constrói-se a Tabela de Routh, mantendo $K$ como uma variável.
    3.  Para estabilidade, **todos os termos da primeira coluna devem ser positivos** (assumindo $K>0$).
    4.  Isso gera inequações. No Exemplo 6.9, as condições foram:
        * Da linha $s^0$: $K > 0$
        * Da linha $s^1$: $\frac{1386-K}{18} > 0 \implies K < 1386$
* **Resultado:** O sistema é **estável** para $0 < K < 1386$. É **marginalmente estável** em $K = 1386$ (quando a linha $s^1$ se torna zero) e **instável** para $K > 1386$.


