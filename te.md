# Análise de Filtro Digital LTI

Este documento detalha o cálculo da saída $y[n]$ de um filtro digital com resposta ao impulso $h[n]$ para um dado sinal de entrada $x[n]$.

## Equações Iniciais

* **Sinal de Entrada:**
    $$
    x[n] = \sin\left(\frac{\pi}{4}n\right)
    $$

* **Resposta ao Impulso do Filtro:**
    $$
    h[n] = \delta[n] - \sqrt{2}\delta[n-1]
    $$

## Passo 1: Cálculo da Convolução

A saída $y[n]$ é a convolução do sinal de entrada com a resposta ao impulso do filtro.

$$y[n] = x[n] * h[n]$$

Substituindo $h[n]$ na equação:

$$y[n] = x[n] * (\delta[n] - \sqrt{2}\delta[n-1])$$

Utilizando a propriedade distributiva da convolução e a propriedade de amostragem do impulso delta, obtemos:

$$y[n] = x[n] - \sqrt{2}x[n-1]$$

Agora, substituímos a expressão para $x[n]$:

$$y[n] = \sin\left(\frac{\pi}{4}n\right) - \sqrt{2}\sin\left(\frac{\pi}{4}(n-1)\right)$$

## Passo 2: Simplificação Trigonométrica

Para simplificar a expressão, utilizamos a identidade da diferença de ângulos para o seno: $\sin(A-B) = \sin(A)\cos(B) - \cos(A)\sin(B)$.

$$y[n] = \sin\left(\frac{\pi}{4}n\right) - \sqrt{2}\left[\sin\left(\frac{\pi}{4}n\right)\cos\left(\frac{\pi}{4}\right) - \cos\left(\frac{\pi}{4}n\right)\sin\left(\frac{\pi}{4}\right)\right]$$

Sabemos que $\cos(\frac{\pi}{4}) = \sin(\frac{\pi}{4}) = \frac{\sqrt{2}}{2}$. Substituindo esses valores:

$$y[n] = \sin\left(\frac{\pi}{4}n\right) - \sqrt{2}\left[\sin\left(\frac{\pi}{4}n\right)\frac{\sqrt{2}}{2} - \cos\left(\frac{\pi}{4}n\right)\frac{\sqrt{2}}{2}\right]$$

Distribuindo o termo $-\sqrt{2}$ para dentro dos colchetes:

$$y[n] = \sin\left(\frac{\pi}{4}n\right) - \left(\sqrt{2} \cdot \frac{\sqrt{2}}{2}\right)\sin\left(\frac{\pi}{4}n\right) + \left(\sqrt{2} \cdot \frac{\sqrt{2}}{2}\right)\cos\left(\frac{\pi}{4}n\right)$$

Como $\sqrt{2} \cdot \frac{\sqrt{2}}{2} = \frac{2}{2} = 1$, a equação se torna:

$$y[n] = \sin\left(\frac{\pi}{4}n\right) - \sin\left(\frac{\pi}{4}n\right) + \cos\left(\frac{\pi}{4}n\right)$$

Os termos com seno se cancelam.

## Resultado Final

A expressão final para a saída $y[n]$ é:

$$y[n] = \cos\left(\frac{\pi}{4}n\right)$$

Comparando com o formato geral $y[n] = |y|\cos(\omega n + \angle y)$, podemos identificar:

* **Amplitude:** $|y| = 1$
* **Fase:** $\angle y = 0$ radianos