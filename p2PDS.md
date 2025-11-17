## 📜 Questão 1: Análise de Sistema FIR

Esta questão analisa um sistema de Resposta ao Impulso Finita (FIR) simples, $h[n]$.

* [cite_start]**Definição do Sistema:** Pela imagem[cite: 6], vemos que a resposta ao impulso é:
    [cite_start]$h[n] = 1 \cdot \delta[n] - 1 \cdot \delta[n-1] + 1 \cdot \delta[n-2]$ [cite: 101]

### (a) Transformada de Fourier de Tempo Discreto (DTFT)

O objetivo é encontrar $H(\omega)$ e esboçar seu módulo e fase.

1.  **Cálculo de $H(\omega)$:**
    [cite_start]A DTFT é calculada pela soma $H(\omega) = \sum h[n]e^{-j\omega n}$[cite: 101].
    $H(\omega) = 1 \cdot e^{-j\omega(0)} - 1 \cdot e^{-j\omega(1)} + 1 \cdot e^{-j\omega(2)}$
    $H(\omega) = 1 - e^{-j\omega} + e^{-j2\omega}$

2.  **Manipulação para Fase Linear:**
    Para analisar o módulo e a fase, o truque é fatorar um termo de "meio-atraso", $e^{-j\omega}$:
    [cite_start]$H(\omega) = e^{-j\omega}(e^{j\omega} - 1 + e^{-j\omega})$ [cite: 103]
    [cite_start]Usando a identidade de Euler ($2\cos(\omega) = e^{j\omega} + e^{-j\omega}$ [cite: 105]), agrupamos os termos:
    $H(\omega) = e^{-j\omega}((e^{j\omega} + e^{-j\omega}) - 1)$
    [cite_start]$H(\omega) = e^{-j\omega}(2\cos(\omega) - 1)$ [cite: 106]

3.  **Módulo $|H(\omega)|$:**
    O módulo é o valor absoluto da amplitude:
    $|H(\omega)| = |e^{-j\omega}| \cdot |2\cos(\omega) - 1| [cite_start]= \mathbf{|2\cos(\omega) - 1|}$ [cite: 108]
    * Em $\omega=0$: $|2\cos(0) - 1| = |2-1| [cite_start]= 1$. [cite: 109, 111]
    * Em $\omega=\pi/3$: $|2\cos(\pi/3) - 1| = |2(1/2) - 1| = 0$. (Zero do filtro) [cite_start][cite: 131]
    * Em $\omega=\pi/2$: $|2\cos(\pi/2) - 1| = |0-1| [cite_start]= 1$. [cite: 115, 117]
    * Em $\omega=\pi$: $|2\cos(\pi) - 1| = |2(-1) - 1| = |-3| [cite_start]= 3$. [cite: 119, 122]
    O esboço no gráfico da Questão 1 (página 1) e o esboço de rascunho (página 4) estão corretos.

4.  **Fase $\angle H(\omega)$:**
    A fase é a soma das fases: $\angle(e^{-j\omega}) + \angle(2\cos(\omega) - 1)$.
    * $\angle(e^{-j\omega}) = -\omega$.
    * $\angle(2\cos(\omega) - 1)$ é $0$ se $(2\cos(\omega) - 1) > 0$, ou $\pi$ (ou $-\pi$) se $(2\cos(\omega) - 1) < 0$.
    * O termo $(2\cos(\omega) - 1)$ é negativo quando $|\omega| > \pi/3$.
    * Portanto, a fase é $\angle H(\omega) = -\omega$ na faixa central ($-\pi/3 < \omega < \pi/3$) e salta $\pi$ radianos fora dessa faixa.
    * O gráfico da fase na Questão 1 (página 1) mostra exatamente isso: uma linha $\angle H(\omega) = -\omega$ com saltos de $\pi$ em $\pm\pi/3$.

### (b) Saída para uma entrada cosseno

[cite_start]Para uma entrada $x[n]=\cos(\omega_0 n)$, a saída $y[n]$ é $A \cos(\omega_0 n + \varphi)$, onde $A = |H(\omega_0)|$ e $\varphi = \angle H(\omega_0)$[cite: 42]. Basta lermos os valores dos gráficos:

* [cite_start]**$\omega_0 = 0$:** [cite: 44]
    * $A = |H(0)| [cite_start]= \mathbf{1}$ [cite: 111]
    * [cite_start]$\varphi = \angle H(0) = \mathbf{0}$ [cite: 110]
* [cite_start]**$\omega_0 = \pi/4$:** [cite: 46]
    * $A = |H(\pi/4)| = |2\cos(\pi/4) - 1| = |2(\sqrt{2}/2) - 1| [cite_start]= \mathbf{\sqrt{2} - 1}$ (aprox. 0.414) [cite: 114]
    * [cite_start]$\varphi = \angle H(\pi/4) = -\pi/4$ (está na região onde a fase é $-\omega$) [cite: 113]
* [cite_start]**$\omega_0 = \pi/2$:** [cite: 46]
    * $A = |H(\pi/2)| [cite_start]= \mathbf{1}$ [cite: 117]
    * $\varphi = \angle H(\pi/2)$. Aqui, $\omega=\pi/2$, que está fora da faixa central. [cite_start]A fase é $-\omega + \pi = -\pi/2 + \pi = \mathbf{\pi/2}$[cite: 116].
* [cite_start]**$\omega_0 = \pi$:** [cite: 49]
    * $A = |H(\pi)| [cite_start]= \mathbf{3}$ [cite: 122]
    * $\varphi = \angle H(\pi)$. Está fora da faixa central. [cite_start]A fase é $-\omega + \pi = -\pi + \pi = \mathbf{0}$[cite: 120].

---

## ⚙️ Questão 2: Análise de Sistema LTI

Aqui, o sistema é definido por um par entrada-saída.

* [cite_start]Entrada: $x[n] = (\frac{1}{2})^n u[n]$ [cite: 8] $\implies X(z) = \frac{1}{1 - \frac{1}{2}z^{-1}}$ , com Região de Convergência (ROC) $|z| > [cite_start]1/2$[cite: 141].
* [cite_start]Saída: $y[n] = (\frac{1}{4})^n u[n-1]$[cite: 8].
    * [cite_start]Reescrevemos $y[n]$ para usar a propriedade do atraso: $y[n] = \frac{1}{4} (\frac{1}{4})^{n-1} u[n-1]$[cite: 140].
    * $Y(z) = \frac{1}{4} \left( \frac{z^{-1}}{1 - \frac{1}{4}z^{-1}} \right)$, com ROC $|z| > [cite_start]1/4$[cite: 141].

### (a) Polos, Zeros e ROC de H(z)

A função de transferência $H(z)$ é a razão entre as transformadas:

[cite_start]$H(z) = \frac{Y(z)}{X(z)} = \frac{\frac{1}{4}z^{-1} / (1 - \frac{1}{4}z^{-1})}{1 / (1 - \frac{1}{2}z^{-1})}$ [cite: 142, 148]
[cite_start]$H(z) = \frac{\frac{1}{4}z^{-1}(1 - \frac{1}{2}z^{-1})}{1 - \frac{1}{4}z^{-1}} = \frac{\frac{1}{4}z^{-1} - \frac{1}{8}z^{-2}}{1 - \frac{1}{4}z^{-1}}$ [cite: 149, 150]

* **Polos (raízes do denominador):**
    $1 - \frac{1}{4}z^{-1} = 0 \implies 1 = \frac{1}{4z} \implies z = \mathbf{1/4}$.
* **Zeros (raízes do numerador):**
    $\frac{1}{4}z^{-1} - \frac{1}{8}z^{-2} = 0 \implies \frac{1}{4z} - \frac{1}{8z^2} = 0$
    Multiplicando por $8z^2$: $2z - 1 = 0 \implies z = \mathbf{1/2}$.
* **Polos/Zeros em z=0 ou z=∞:**
    Reescrevendo $H(z)$ com potências positivas de $z$:
    $H(z) = \frac{\frac{1}{4z} - \frac{1}{8z^2}}{1 - \frac{1}{4z}} = \frac{(2z-1)/(8z^2)}{(4z-1)/(4z)} = \frac{2z-1}{8z^2} \cdot \frac{4z}{4z-1} = \frac{2(z-1/2)}{2z \cdot 4(z-1/4)}$
    $H(z) = \frac{z - 1/2}{4z(z - 1/4)}$
    Isso confirma: **Zero em $z=1/2$** e **Polos em $z=1/4$ e $z=0$**.
* **Região de Convergência (ROC):**
    Como $x[n]$ e $y[n]$ são causais, $h[n]$ também é causal. A ROC de um sistema causal é sempre a região *externa* ao polo mais distante da origem.
    Os polos são $0$ e $1/4$. O mais distante é $1/4$.
    Portanto, a ROC é **$|z| > 1/4$**.

> O esboço na primeira página do PDF está **totalmente correto**:
> * Polos (X) em $z=0$ e $z=1/4$.
> * Zero (O) em $z=1/2$.
> * ROC (área verde) como $|z| > [cite_start]1/4$[cite: 23].

### (b) Resposta ao Impulso $h[n]$

Para encontrar $h[n]$, precisamos da Transformada Z Inversa de $H(z)$. A fração $H(z) = \frac{\frac{1}{4}z^{-1} - \frac{1}{8}z^{-2}}{1 - \frac{1}{4}z^{-1}}$ é "imprópria" (grau do numerador em $z^{-1}$ é maior ou igual ao do denominador). Usamos divisão longa:

($\frac{1}{4}z^{-1} - \frac{1}{8}z^{-2}$) dividido por ($1 - \frac{1}{4}z^{-1}$)
[cite_start]O rascunho da divisão na página 5 [cite: 143, 153-157] [cite_start]está confuso e leva a um resultado incorreto[cite: 158].

Vamos fazer a divisão corretamente (método de divisão de polinômios):
$H(z) = \frac{-\frac{1}{8}z^{-2} + \frac{1}{4}z^{-1}}{-\frac{1}{4}z^{-1} + 1}$
Dividindo o termo de maior ordem ($\frac{-1/8 z^{-2}}{-1/4 z^{-1}} = \frac{1}{2}z^{-1}$):
$H(z) = \frac{1}{2}z^{-1} + \frac{\text{Resto}}{1 - \frac{1}{4}z^{-1}}$
Resto = $(\frac{1}{4}z^{-1} - \frac{1}{8}z^{-2}) - (\frac{1}{2}z^{-1} \cdot (1 - \frac{1}{4}z^{-1}))$
Resto = $(\frac{1}{4}z^{-1} - \frac{1}{8}z^{-2}) - (\frac{1}{2}z^{-1} - \frac{1}{8}z^{-2}) = -\frac{1}{4}z^{-1}$
Então:
$H(z) = \mathbf{\frac{1}{2}z^{-1}} - \mathbf{\frac{\frac{1}{4}z^{-1}}{1 - \frac{1}{4}z^{-1}}}$

Agora, tiramos a inversa (lembrando que $\frac{az^{-1}}{1-az^{-1}} \leftrightarrow a^n u[n-1]$):
$h[n] = \frac{1}{2}\delta[n-1] - \frac{1}{4} \cdot (\frac{1}{4})^{n-1} u[n-1]$
$h[n] = \frac{1}{2}\delta[n-1] - (\frac{1}{4})^{n} u[n-1]$

### (c) Equação de Diferenças

Esta é a parte mais direta. [cite_start]Começamos com a $H(z)$ [cite: 159] e cruzamos os denominadores:
$\frac{Y(z)}{X(z)} = \frac{\frac{1}{4}z^{-1} - \frac{1}{8}z^{-2}}{1 - \frac{1}{4}z^{-1}}$
[cite_start]$Y(z) \cdot (1 - \frac{1}{4}z^{-1}) = X(z) \cdot (\frac{1}{4}z^{-1} - \frac{1}{8}z^{-2})$ [cite: 160]

Convertendo de volta para o domínio do tempo (onde $z^{-k} \leftrightarrow$ atraso de $k$ amostras):
[cite_start]$y[n] - \frac{1}{4}y[n-1] = \frac{1}{4}x[n-1] - \frac{1}{8}x[n-2]$ [cite: 161]

Isolando $y[n]$:
$y[n] = \frac{1}{4}y[n-1] + \frac{1}{4}x[n-1] - \frac{1}{8}x[n-2]$
[cite_start]O rascunho na página 6 [cite: 162] está **correto**.

---

## 🧐 Questão 3: Verdadeiro ou Falso

* [cite_start]**(a) Falso.** "É possível determinar unicamente $h[n]$ se forem conhecidas as localizações de polos e zeros... e o valor de $H(z_0)$..." [cite: 53]
    * [cite_start]**Justificativa:** Está FALSO[cite: 53]. [cite_start]Faltou a informação mais crucial: a **Região de Convergência (ROC)**[cite: 54]. Polos e zeros idênticos podem corresponder a um sistema causal, um anti-causal ou um de dois lados, cada um com um $h[n]$ diferente. A ROC define qual deles é.
* [cite_start]**(b) Verdadeiro.** "Se um sistema é FIR, então $H(z)$ não possui polos, exceto possivelmente em $z=0$." [cite: 55]
    * [cite_start]**Justificativa:** Está VERDADEIRO[cite: 55]. Um sistema FIR causal tem $H(z) = \sum_{n=0}^{M} h[n]z^{-n}$. Ao colocar em uma fração (potências positivas), $H(z) = \frac{h[0]z^M + ... + h[M]}{z^M}$. O denominador é $z^M$, o que significa que todos os $M$ polos estão na origem ($z=0$).
* [cite_start]**(c) Falso.** "Se $H(z)$ tem mais polos do que zeros, o sistema é causal." [cite: 56]
    * [cite_start]**Justificativa:** Está FALSO[cite: 56]. A causalidade não tem relação com a *quantidade* de polos ou zeros. Ela é definida pela ROC (exterior ao polo mais externo) ou pela condição $h[n]=0$ para $n<0$.
* [cite_start]**(d) Falso.** "Se $H(z)$ tem todos os seus polos e zeros dentro do círculo unitário, o sistema é estável." [cite: 57]
    * [cite_start]**Justificativa:** Está FALSO[cite: 57]. A estabilidade depende da ROC incluir o círculo unitário ($|z|=1$). Se um sistema for *anti-causal* (ROC é *interna* ao polo mais interno), ter todos os polos *dentro* do círculo (ex: $p=0.5$) faria com que a ROC ($|z|<0.5$) *não* incluísse o círculo unitário, tornando-o instável. (Os zeros são irrelevantes para a estabilidade).

---

##  convolução Questão 4: Convolução via Transformada Z

[cite_start]Devemos calcular $y[n] = x[n] * h[n]$[cite: 62], onde:
* [cite_start]$x[n] = -(-\frac{1}{2})^n u[n-1]$ [cite: 60]
* [cite_start]$h[n] = \delta[n] + (\frac{1}{2})^{n-1} u[n-1]$ [cite: 60]

Usar $Y(z) = X(z)H(z)$ é muito mais fácil.

1.  **Transformada $X(z)$:**
    [cite_start]$x[n] = -(-\frac{1}{2}) \cdot (-\frac{1}{2})^{n-1} u[n-1] = \frac{1}{2} \cdot (-\frac{1}{2})^{n-1} u[n-1]$ [cite: 166]
    Usando a propriedade $a^{n-1}u[n-1] \leftrightarrow \frac{z^{-1}}{1-az^{-1}}$:
    [cite_start]$X(z) = \frac{1}{2} \left( \frac{z^{-1}}{1 - (-\frac{1}{2})z^{-1}} \right) = \mathbf{\frac{1}{2} \frac{z^{-1}}{1 + \frac{1}{2}z^{-1}}}$ [cite: 166]

2.  **Transformada $H(z)$:**
    $h[n] = \delta[n] + (\frac{1}{2})^{n-1} u[n-1]$
    [cite_start]$H(z) = \mathbf{1 + \frac{z^{-1}}{1 - \frac{1}{2}z^{-1}}}$ [cite: 167]

3.  **Multiplicação $Y(z)$:**
    $Y(z) = X(z) \cdot H(z) = \left( \frac{1}{2} \frac{z^{-1}}{1 + \frac{1}{2}z^{-1}} \right) \cdot \left( 1 + \frac{z^{-1}}{1 - \frac{1}{2}z^{-1}} \right)$
    Vamos simplificar o termo de $H(z)$ primeiro (achando denominador comum):
    [cite_start]$H(z) = \frac{(1 - \frac{1}{2}z^{-1}) + z^{-1}}{1 - \frac{1}{2}z^{-1}} = \frac{1 + \frac{1}{2}z^{-1}}{1 - \frac{1}{2}z^{-1}}$ [cite: 167]
    Agora a multiplicação fica fácil:
    $Y(z) = \left( \frac{1}{2} \frac{z^{-1}}{1 + \frac{1}{2}z^{-1}} \right) \cdot \left( \frac{1 + \frac{1}{2}z^{-1}}{1 - \frac{1}{2}z^{-1}} \right)$
    Os termos $(1 + \frac{1}{2}z^{-1})$ se cancelam!
    [cite_start]$Y(z) = \mathbf{\frac{1}{2} \frac{z^{-1}}{1 - \frac{1}{2}z^{-1}}}$ [cite: 169]

4.  **Transformada Inversa $y[n]$:**
    $Y(z)$ tem a forma $\frac{1}{2} \cdot (\frac{z^{-1}}{1 - \frac{1}{2}z^{-1}})$.
    Esta é a transformada de $\frac{1}{2} \cdot (\frac{1}{2})^{n-1} u[n-1]$.
    $y[n] = \frac{1}{2} \cdot (\frac{1}{2})^{n-1} u[n-1] = (\frac{1}{2})^1 \cdot (\frac{1}{2})^{n-1} u[n-1]$
    $y[n] = (\frac{1}{2})^{n} u[n-1]$
    [cite_start]A resolução nas páginas 6 e 7 [cite: 163-170] está **correta**.

---

## ✅ Questões 5-8: Múltipla Escolha (Conceitos)

Estas questões não foram marcadas, mas aqui estão as respostas corretas e as justificativas:

### Questão 5: Existência da DTFT

* **Resposta Correta: D**
* **Justificativa:** A DTFT $X(\omega) = \sum x[n]e^{-j\omega n}$ é uma soma infinita. Uma condição *suficiente* para que ela convirja (exista) é que a sequência $x[n]$ seja **absolutamente somável** (ou seja, $\sum |x[n]| < \infty$). [cite_start]Além disso, a função $e^{-j\omega n}$ é inerentemente periódica em $\omega$ com período $2\pi$, o que torna $X(\omega)$ também **periódica com período $2\pi$**[cite: 67].

### Questão 6: ROC e Estabilidade

* **Resposta Correta: E**
* **Justificativa:** A estabilidade de um sistema LTI (LTI) requer que $h[n]$ seja absolutamente somável ($\sum |h[n]| < \infty$). A DTFT $H(\omega)$ é a Transformada Z $H(z)$ avaliada em $z=e^{j\omega}$ (o círculo unitário). A DTFT só existe se $h[n]$ for absolutamente somável (estável). [cite_start]Portanto, a condição para estabilidade é que a DTFT exista, o que significa que a **ROC de $H(z)$ deve incluir o círculo unitário ($|z|=1$)**[cite: 76, 77].

### Questão 7: Teorema da Amostragem

* **Resposta Correta: D**
* **Justificativa:** O Teorema de Nyquist-Shannon afirma que para reconstruir perfeitamente um sinal analógico (limitado em banda $F_{max}$) a partir de suas amostras, a frequência de amostragem $F_s$ deve ser pelo menos o dobro da frequência máxima.
    * [cite_start]Condição: **$F_s \ge 2F_{max}$**[cite: 85].
    * [cite_start]Violação: Se $F_s < 2F_{max}$ (subamostragem), as réplicas espectrais no domínio da frequência se sobrepõem, um fenômeno destrutivo chamado **aliasing**, que impossibilita a recuperação do sinal original[cite: 86].

### Questão 8: Reconstrução Ideal

* **Resposta Correta: C**
* **Justificativa:** O processo de amostragem cria réplicas do espectro original em múltiplos da frequência de amostragem ($\Omega_s$). O filtro de reconstrução ideal (um filtro passa-baixas ideal) tem duas funções:
    1.  **Remover completamente as réplicas** (imagens) indesejadas.
    2.  [cite_start]**Preservar a banda base** original (de $0$ a $\Omega_{max}$), aplicando um **ganho de T** (período de amostragem) para compensar a atenuação de $1/T$ que ocorre durante o processo de amostragem por impulsos[cite: 93].

