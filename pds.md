# Resolução Detalhada: Teoria de Processamento Digital de Sinais (Simulado 2)

**Disciplina:** Processamento Digital de Sinais

---

## 3. Verdadeiro ou Falso (8 Pontos)

**Enunciado:** Para cada afirmação abaixo, preencha V se ela for verdadeira e F se for falsa.

### a) ( V ) É possível determinar unicamente $h[n]$ se forem conhecidas as localizações de polos e zeros de $H(z)$ e o valor de $H(z_0)$ em um único ponto não singular $z_0$.

* **Justificativa:** A função de transferência de um sistema LTI pode ser expressa na forma fatorada como $H(z) = G \frac{\prod(z - z_k)}{\prod(z - p_k)}$. As localizações dos zeros ($z_k$) e polos ($p_k$) definem os termos do produtório, mas deixam o termo de ganho $G$ indefinido. Ao fornecer o valor de $H(z)$ em um ponto específico $z_0$ (que não seja um polo nem um zero), é possível montar uma equação algébrica simples para encontrar $G$, determinando assim todo o sistema unicamente.

### b) ( V ) Se um sistema é FIR, então $H(z)$ não possui polos, exceto possivelmente em $z=0$.

* **Justificativa:** Um filtro FIR (Resposta ao Impulso Finita) tem a equação $H(z) = \sum_{n=0}^{M} h[n]z^{-n}$. Reduzindo ao mesmo denominador, obtemos um polinômio no numerador dividido por $z^M$. Isso implica que existem $M$ polos localizados na origem ($z=0$), chamados de polos triviais. Não existem polos em outros lugares do plano-z, o que é consistente com a estabilidade incondicional dos filtros FIR.

### c) ( F ) Se $H(z)$ tem mais polos do que zeros, o sistema é causal.

* **Justificativa:** A causalidade de um sistema é determinada pela **Região de Convergência (RDC)**, não pela contagem de polos e zeros. Para um sistema ser causal, a RDC deve ser o exterior de um círculo ($|z| > R_{max}$), incluindo o infinito. A relação entre a quantidade de polos e zeros diz respeito apenas se a função de transferência é própria ou imprópria, mas não garante que o sistema "viaje" para frente no tempo.

### d) ( F ) Se $H(z)$ tem todos os seus polos e zeros dentro do círculo unitário, o sistema é estável.

* **Justificativa:** A estabilidade de um sistema LTI discreto exige que o **Círculo Unitário esteja contido na RDC**. Se os polos estão dentro do círculo unitário ($|p_k| < 1$), existem duas possibilidades para a RDC:
    1.  $|z| > |p_{max}|$ (Sistema Causal): A RDC inclui o círculo unitário $\rightarrow$ **Estável**.
    2.  $|z| < |p_{min}|$ (Sistema Anti-causal): A RDC *não* inclui o círculo unitário $\rightarrow$ **Instável**.
    Como a afirmação não especifica que o sistema é causal, não se pode garantir a estabilidade apenas pela posição dos polos.

---

## 5. Múltipla Escolha (6 Pontos)

**Enunciado:** Qual das alternativas abaixo descreve a condição fundamental para a existência da DTFT de uma sequência $x[n]$ e qual é a propriedade essencial de periodicidade de $X(\omega)$?

* **Alternativa A (Incorreta):** *"...a sequência $x[n]$ deve ser de energia finita e $X(\omega)$ é aperiódica."*
    * **Erro:** A DTFT de uma sequência discreta é sempre periódica com período $2\pi$. Dizer que é aperiódica viola a definição fundamental da DTFT.

* **Alternativa B (Incorreta):** *"...$X(\omega)$ é periódica com período $\pi$."*
    * **Erro:** O período fundamental da DTFT é $2\pi$, não $\pi$. O período $\pi$ ocorreria apenas em casos específicos, não sendo a regra geral.

* **Alternativa C (Incorreta):** *"...a sequência $x[n]$ deve ser causal..."*
    * **Erro:** A DTFT existe para sequências não-causais e anti-causais, desde que satisfaçam a condição de convergência.

* **Alternativa D (Correta):** *"...a sequência $x[n]$ deve ser absolutamente somável e $X(\omega)$ é periódica com período $2\pi$."*
    * **Acerto:** Esta é a definição exata da Condição de Dirichlet para convergência suficiente ($\sum |x[n]| < \infty$). Além disso, a DTFT $X(\omega)$ é sempre periódica com $2\pi$.

* **Alternativa E (Incorreta):** *"...$X(\omega)$ é periódica com período 4$\pi$."*
    * **Erro:** O período fundamental é $2\pi$. A condição de que a sequência *deve* ser finita também é restritiva demais.

---

## 6. Múltipla Escolha (6 Pontos)

**Enunciado:** Qual é a implicação direta da RDC de um sistema LTI incluir o círculo unitário $(|z|=1)$, e como isso se relaciona com a DTFT?

* **Alternativa A (Incorreta):** *"Se a RDC incluir o círculo unitário, o sistema é não-causal..."*
    * **Erro:** A inclusão do círculo unitário define estabilidade, não causalidade. Um sistema causal pode ser estável ou instável.

* **Alternativa B (Incorreta):** *"A inclusão do círculo unitário... é necessária e suficiente para que o sistema seja invertível."*
    * **Erro:** Invertibilidade depende da existência de um sistema inverso estável e causal, não apenas da estabilidade do sistema original.

* **Alternativa C (Incorreta):** *"...o sistema deve ser do tipo FIR. A DTFT não tem relação direta com o círculo unitário."*
    * **Erro:** Sistemas IIR (com polos) também podem ser estáveis. A DTFT é a Transformada Z calculada *sobre* o círculo unitário, logo a relação é total.

* **Alternativa D (Incorreta):** *"A RDC deve ser o exterior de um círculo, garantindo que o sistema seja causal..."*
    * **Erro:** Esta alternativa define causalidade, mas não responde à pergunta sobre a implicação de $|z|=1$ na RDC.

* **Alternativa E (Correta):** *"A inclusão do círculo unitário $(|z|=1)$ na RDC é a condição necessária e suficiente para que o sistema LTI seja estável. Quando $|z|=1$ está na ROC, a DTFT $H(\omega)$ existe."*
    * **Acerto:** Esta é a definição de estabilidade BIBO no domínio Z. A segunda parte confirma que a DTFT só converge se o círculo unitário fizer parte da RDC.

---

## 7. Múltipla Escolha (6 Pontos)

**Enunciado:** Qual das alternativas descreve corretamente o Teorema de Amostragem de Nyquist-Shannon e o efeito de violar essa condição?

* **Alternativa A (Incorreta):** *"...basta que $F_s > F_{max}$..."*
    * **Erro:** O teorema exige $F_s > 2F_{max}$. Amostrar apenas acima de $F_{max}$ é insuficiente e causa aliasing.

* **Alternativa B (Incorreta):** *"...é necessário que $F_s < 2F_{max}$..."*
    * **Erro:** A desigualdade está invertida. Amostrar abaixo de $2F_{max}$ causa aliasing.

* **Alternativa C (Incorreta):** *"...a condição sobre $F_s$ não é relevante, desde que o sinal seja periódico."*
    * **Erro:** A periodicidade do sinal não impede a sobreposição espectral (aliasing) se a taxa de Nyquist for violada.

* **Alternativa D (Correta):** *"Para reconstrução perfeita... é necessário que a frequência de amostragem satisfaça $F_s \ge 2F_{max}$. Se $F_s < 2F_{max}$, ocorre aliasing, tornando impossível recuperar $x_a(t)$ sem distorção."*
    * **Acerto:** Define corretamente a Taxa de Nyquist e identifica o aliasing como consequência da violação.

* **Alternativa E (Incorreta):** *"...é necessário que $F_s = F_{max}$."*
    * **Erro:** Igualar a frequência de amostragem à frequência máxima viola o critério de Nyquist (que exige o dobro).

---

## 8. Múltipla Escolha (6 Pontos)

**Enunciado:** Qual é a função essencial do filtro de reconstrução ideal $H_r(\Omega)$ para garantir a reconstrução perfeita do sinal?

* **Alternativa A (Incorreta):** *"Apenas introduzir um atraso de tempo..."*
    * **Erro:** A função principal é a filtragem espectral, não o atraso.

* **Alternativa B (Incorreta):** *"Atuar como uma função de interpolação ideal $h_r(t)$, que deve ter energia finita..."*
    * **Erro:** Justificativa vaga. O foco deve ser a remoção de imagens espectrais.

* **Alternativa C (Correta):** *"Preservar o espectro da banda base, aplicando um ganho de T, e, simultaneamente, remover completamente as réplicas de imagem."*
    * **Acerto:** Descreve mecanicamente o processo:
        1.  **Remove as imagens:** Elimina frequências acima de $F_s/2$.
        2.  **Ganho de T:** Compensa a escala $1/T$ introduzida pela amostragem por impulsos.

* **Alternativa D (Incorreta):** *"Garantir que o sistema reconstruído seja causal..."*
    * **Erro:** O filtro de reconstrução ideal (Sinc) é não-causal.

* **Alternativa E (Incorreta):** *"Atuar como um filtro passa-altas..."*
    * **Erro:** O filtro de reconstrução deve ser Passa-Baixas para manter o sinal original e remover as cópias de alta frequência.
