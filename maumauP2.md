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
    * $f(x) \approx f(x_0) + m_a(x-x_0)$
    * Onde $m_a$ é o coeficiente angular (a derivada) da função no ponto $x_0$: $m_a = \frac{df(x)}{dx}|_{x=x_0}$.
* **Forma de Variação (Perturbação):** Definindo $\delta x = (x-x_0)$ e $\delta f(x) = [f(x)-f(x_0)]$, a fórmula se torna:
    * $\delta f(x) \approx m_a \delta x$

**Exemplos:**

* **Linearização de Função (Exemplo 2.26):**
    * **Problema:** Linearizar $f(x) = 5 \cos(x)$ em torno de $x = \pi/2$.
    * **Solução:** A derivada é $\frac{df}{dx} = -5 \sin(x)$. No ponto $x = \pi/2$, o coeficiente angular é $Slope = -5$. A função linearizada para pequenas variações $\delta x$ é $f(x) = -5\delta x$.
* **Linearização de Equação Diferencial (Exemplo 2.27):**
    * **Problema:** Linearizar $\frac{d^{2}x}{dt^{2}}+2\frac{dx}{dt}+\cos x=0$ em torno de $x = \pi/4$.
    * **Solução:** O termo não linear $\cos(x)$ é linearizado como $\cos(\delta x+\frac{\pi}{4}) \approx \cos(\frac{\pi}{4})-\sin(\frac{\pi}{4})\delta x$. A equação diferencial linearizada resultante é $\frac{d^{2}\delta x}{dt^{2}}+2\frac{d\delta x}{dt}-\frac{\sqrt{2}}{2}\delta x = -\frac{\sqrt{2}}{2}$.
* **Linearização de Circuito Elétrico (Exemplo 2.28):**
    * **Problema:** Encontrar a função de transferência de um circuito com um resistor não linear $i_r = 2e^{0.1v_r}$.
    * **Solução:** A equação do circuito $L\frac{di}{dt} + 10\ln(\frac{1}{2}i) - 20 = v(t)$ é linearizada. O termo não linear é linearizado em torno do ponto de operação $i_0 = 14.78$. Isso resulta em uma equação diferencial linear $\frac{d\delta i}{dt} + 0.677\delta i = v(t)$, que leva à função de transferência $\frac{V_L(s)}{V(s)} = \frac{s}{s+0.677}$.

---

### **Aula 09: Polos, Zeros e a Resposta do Sistema**

**Teoria:**

* **Polos e Zeros:**
    * **Polos:** São as raízes do denominador da função de transferência. Eles ditam a resposta natural (o comportamento intrínseco) do sistema.
    * **Zeros:** São as raízes do numerador da função de transferência. Eles afetam a amplitude (os resíduos) dos termos da resposta.
* **Resposta Forçada vs. Resposta Natural:**
    * A resposta total de um sistema $c(t)$ é a soma de duas partes.
    * **Resposta Forçada:** É a parte da resposta devida aos polos da entrada (ex: o polo em $s=0$ de uma entrada degrau). Ela dita o comportamento em regime permanente.
    * **Resposta Natural:** É a parte da resposta devida aos polos do sistema. Ela dita o comportamento transitório (como o sistema chega ao regime permanente).

#### **Sistemas de Primeira Ordem**

* **Forma Padrão:** $G(s) = \frac{a}{s+a}$.
* **Resposta ao Degrau:** $c(t) = 1 - e^{-at}$.
* **Métricas de Desempenho:**
    * **Constante de Tempo ($T_c$):** $T_c = 1/a$. É o tempo para a resposta atingir 63% do valor final.
    * **Tempo de Subida ($T_r$):** Tempo para ir de 10% a 90% do valor final. $T_r = \frac{2.2}{a}$.
    * **Tempo de Acomodação ($T_s$):** Tempo para a resposta ficar dentro de 2% do valor final. $T_s = \frac{4}{a}$.

#### **Sistemas de Segunda Ordem**

* **Formas Padrão:**
    * Geral: $G(s) = \frac{b}{s^2 + as + b}$.
    * Parametrizada: $G(s) = \frac{\omega_n^2}{s^2 + 2\zeta\omega_n s + \omega_n^2}$.
* **Parâmetros Fundamentais:**
    * **Frequência Natural ($\omega_n$):** A frequência de oscilação do sistema sem amortecimento. $\omega_n = \sqrt{b}$.
    * **Fator de Amortecimento ($\zeta$):** Controla a natureza da resposta. $a=2\zeta\omega_{n}$ ou $\zeta = \frac{a}{2\omega_n}$.

* **Tipos de Resposta (baseado nos polos e em $\zeta$):**
    1.  **Superamortecida ($\zeta > 1$):**
        * **Polos:** Dois polos reais e distintos.
        * **Resposta:** Soma de duas exponenciais, sem oscilação. $c(t) = K_1e^{-\sigma_1 t} + K_2e^{-\sigma_2 t}$.
    2.  **Subamortecida ($0 < \zeta < 1$):**
        * **Polos:** Um par de polos complexos conjugados.
        * **Resposta:** Uma senóide amortecida. $c(t) = Ae^{-\sigma_d t}\cos(\omega_d t - \phi)$. A parte real ($\sigma_d$) gera o decaimento exponencial, e a parte imaginária ($\omega_d$) gera a oscilação.
    3.  **Criticamente Amortecida ($\zeta = 1$):**
        * **Polos:** Dois polos reais e iguais.
        * **Resposta:** A resposta mais rápida possível sem ultrapassagem. $c(t) = K_1e^{-\sigma_1 t} + K_2te^{-\sigma_1 t}$.
    4.  **Não Amortecida ($\zeta = 0$):**
        * **Polos:** Um par de polos imaginários puros.
        * **Resposta:** Uma senóide pura (oscilação sustentada). $c(t) = A\cos(\omega_1 t - \phi)$.

* **Métricas de Desempenho (para Sistemas Subamortecidos):**
    * **Instante de Pico ($T_p$):** Tempo para atingir o primeiro pico máximo.
        * $T_p = \frac{\pi}{\omega_n\sqrt{1-\zeta^2}}$ ou $T_p = \frac{\pi}{\omega_d}$.
    * **Ultrapassagem Percentual (%UP):** O quanto a resposta ultrapassa o valor final.
        * $\%UP = 100 \times e^{-(\zeta\pi/\sqrt{1-\zeta^2})}$.
    * **Tempo de Acomodação ($T_s$):** Tempo para ficar dentro de $\pm$2% do valor final.
        * $T_s = \frac{4}{\zeta\omega_n}$ ou $T_s = \frac{4}{\sigma_d}$.
    * **Tempo de Subida ($T_r$):** Tempo de 10% a 90% do valor final. É obtido a partir de gráficos ou tabelas.

**Exemplos:**

* **Exemplo 4.4:** Classificar sistemas com base em $\zeta$.
    * $G(s) = \frac{12}{s^2+8s+12} \implies \zeta=1.155$ (Superamortecido).
    * $G(s) = \frac{16}{s^2+8s+16} \implies \zeta=1$ (Criticamente Amortecido).
    * $G(s) = \frac{20}{s^2+8s+20} \implies \zeta=0.894$ (Subamortecido).
* **Exemplo 4.5:** Calcular métricas a partir da função de transferência.
    * **Problema:** $G(s) = \frac{100}{s^2+15s+100}$.
    * **Solução:** Calcula-se $\omega_n=10$ e $\zeta=0.75$. Usando as fórmulas, obtém-se $T_p=0.475$s, $\%UP=2.838$ e $T_s=0.533$s.

---

### Tabela de Fórmulas e Definições (Aulas 08 e 09)

| Categoria | Fórmula | Descrição | Aula |
| :--- | :--- | :--- | :--- |
| **Linearização** | $f(x) \approx f(x_0) + m_a(x-x_0)$ | Aproxima uma função não linear $f(x)$ pela sua reta tangente no ponto de operação $x_0$. | 08 |
| **Linearização** | $m_a = \frac{df(x)}{dx}\|_ {x=x_0}$ | Coeficiente angular (derivada) da reta tangente usada para a linearização. | 08 |
| **Linearização** | $\delta f(x) \approx m_a \delta x$ | Relação linearizada que associa a pequena variação na saída ($\delta f(x)$) à pequena variação na entrada ($\delta x$). | 08 |
| **1ª Ordem** | $G(s) = \frac{a}{s+a}$ | Forma padrão da função de transferência de um sistema de primeira ordem. | 09 |
| **1ª Ordem** | $c(t)=1-e^{-at}$ | Resposta ao degrau unitário no domínio do tempo para o sistema de primeira ordem padrão. | 09 |
| **1ª Ordem** | $T_c = 1/a$ | **Constante de Tempo ($T_c$):** Tempo para a resposta atingir 63% do valor final. | 09 |
| **1ª Ordem** | $T_{r}=\frac{2.2}{a}$ | **Tempo de Subida ($T_r$):** Tempo para a resposta ir de 10% a 90% do valor final. | 09 |
| **1ª Ordem** | $T_{s}=\frac{4}{a}$ | **Tempo de Acomodação ($T_s$):** Tempo para a resposta ficar dentro de $\pm$2% do valor final. | 09 |
| **2ª Ordem** | $G(s) = \frac{b}{s^2 + as + b}$ | Forma geral da função de transferência de um sistema de segunda ordem. | 09 |
| **2ª Ordem** | $G(s)=\frac{\omega_{n}^{2}}{s^{2}+2\zeta\omega_{n}s+\omega_{n}^{2}}$ | Forma parametrizada padrão de uma função de transferência de segunda ordem. | 09 |
| **2ª Ordem** | $\omega_{n}=\sqrt{b}$ | **Frequência Natural ($\omega_n$):** Frequência de oscilação do sistema sem amortecimento. | 09 |
| **2ª Ordem** | $\zeta = \frac{a}{2\omega_n}$ | **Fator de Amortecimento ($\zeta$):** Parâmetro adimensional que define a natureza da resposta. | 09 |
| **2ª Ordem (Respostas)** | $c(t)=K_{1}e^{-\sigma_{1}t}+K_{2}e^{-\sigma_{2}t}$ | Forma geral da resposta **Superamortecida** ($\zeta > 1$). | 09 |
| **2ª Ordem (Respostas)** | $c(t)=Ae^{-\sigma_{d}t}\cos(\omega_{d}t-\phi)$ | Forma geral da resposta **Subamortecida** ($0 < \zeta < 1$). | 09 |
| **2ª Ordem (Respostas)** | $c(t)=K_{1}e^{-\sigma_{1}t}+K_{2}te^{-\sigma_{1}t}$ | Forma geral da resposta **Criticamente Amortecida** ($\zeta = 1$). | 09 |
| **2ª Ordem (Respostas)** | $c(t)=A \cos(\omega_{1}t-\phi)$ | Forma geral da resposta **Não Amortecida** ($\zeta = 0$). | 09 |
| **2ª Ordem (Métricas)** | $T_p = \frac{\pi}{\omega_n\sqrt{1-\zeta^{2}}}$ | **Instante de Pico ($T_p$):** Tempo para atingir o primeiro pico (para sistemas subamortecidos). | 09 |
| **2ª Ordem (Métricas)** | $\%UP=100 \times e^{-(\zeta\pi/\sqrt{1-\zeta^{2}})}$ | **Ultrapassagem Percentual (%UP):** Pico máximo acima do valor final (para sistemas subamortecidos). | 09 |
| **2ª Ordem (Métricas)** | $T_s = \frac{4}{\zeta\omega_n}$ | **Tempo de Acomodação ($T_s$):** Tempo para ficar dentro de $\pm$2% do valor final. | 09 |
| **2ª Ordem (Métricas)** | $\omega_d = \omega_n\sqrt{1-\zeta^2}$ | **Frequência Amortecida ($\omega_d$):** A frequência de oscilação real de um sistema subamortecido. | 09 |
| **2ª Ordem (Métricas)** | $\sigma_d = \zeta\omega_n$ | **Decaimento Exponencial ($\sigma_d$):** A parte real do polo subamortecido, que define a velocidade de decaimento. | 09 |
| **2ª Ordem (Métricas)** | $T_p = \frac{\pi}{\omega_d}$ | Forma alternativa para o Instante de Pico, usando a frequência amortecida. | 09 |
| **2ª Ordem (Métricas)** | $T_s = \frac{4}{\sigma_d}$ | Forma alternativa para o Tempo de Acomodação, usando o fator de decaimento. | 09 |
