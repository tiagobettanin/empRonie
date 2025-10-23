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
