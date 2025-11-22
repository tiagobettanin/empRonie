Ótima abordagem. Aprender a lógica por trás ("como pensar") é muito mais valioso do que apenas ter a resposta, pois isso garantirá que você vá bem na prova.

Vou dividir o raciocínio questão por questão, usando **exemplos análogos** (parecidos, mas não iguais) para que você possa aplicar o conhecimento na sua lista.

---

### **Questão 1: Formalização (Lógica de Predicados)**

**O que a questão pede:** Traduzir frases do português para símbolos lógicos ($\forall, \exists, \to, \wedge, \neg$).

**Como pensar:**
1.  **Identifique o Quantificador:**
    * **Todo / Qualquer / Nenhum:** Usa-se o **Universal** ($\forall$). Geralmente vem acompanhado de uma **implicação** ($\to$).
    * **Algum / Existe / Pelo menos um:** Usa-se o **Existencial** ($\exists$). Geralmente vem acompanhado de uma **conjunção** ($\wedge$, o "e").

2.  **Identifique os Predicados:** O que é sujeito e o que é característica?

**Exemplos de Treino:**
Suponha: $C(x) = \text{é cachorro}$, $L(x) = \text{late}$.

* **Frase:** "Todo cachorro late."
    * *Pensamento:* Para todo $x$, se $x$ é cachorro, então $x$ late.
    * *Lógica:* $\forall x (C(x) \to L(x))$
    * *Dica:* Nunca use $\wedge$ com $\forall$ em frases universais simples (isso significaria "tudo no universo é cachorro e late").

* **Frase:** "Alguns cachorros latem."
    * *Pensamento:* Existe um $x$ tal que $x$ é cachorro **E** $x$ late.
    * *Lógica:* $\exists x (C(x) \wedge L(x))$
    * *Dica:* O "Algum" pede o "E" ($\wedge$). Se você usar $\to$, a lógica fica fraca (verdadeira mesmo se não existir cachorro).

* **Frase:** "Nenhum cachorro late."
    * *Pensamento:* Para todo $x$, se é cachorro, então **não** late.
    * *Lógica:* $\forall x (C(x) \to \neg L(x))$
    * *Alternativa:* Não existe $x$ tal que seja cachorro e lata ($\neg \exists x (C(x) \wedge L(x))$).

* **Frase:** "Nem tudo late."
    * *Pensamento:* Não é verdade que para todo $x$, $x$ late.
    * *Lógica:* $\neg \forall x L(x)$ (que é igual a $\exists x \neg L(x)$).

---

### **Questão 2: Formas Sintáticas e Categóricas**

**O que a questão pede:** Classificar frases baseando-se nas **Proposições Categóricas de Aristóteles**.

**Como pensar:**
Você precisa decorar ou entender a tabela das 4 formas clássicas (A, E, I, O).

| Nome | Frase Tipo | Estrutura Lógica | Sigla |
| :--- | :--- | :--- | :--- |
| **Universal Afirmativa** | Todo S é P | $\forall x (S_x \to P_x)$ | **A** |
| **Universal Negativa** | Nenhum S é P | $\forall x (S_x \to \neg P_x)$ | **E** |
| **Particular Afirmativa** | Algum S é P | $\exists x (S_x \wedge P_x)$ | **I** |
| **Particular Negativa** | Algum S não é P | $\exists x (S_x \wedge \neg P_x)$ | **O** |

**Dica para o seu exercício:**
Se a frase for **"Nem toda bóia é fria"**, pense: isso significa que *existe pelo menos uma que não é*.
* "Nem todo" = "Algum... não..." $\rightarrow$ Forma **O**.

---

### **Questão 3: Métodos de Prova**

**O que a questão pede:** Provar que a conclusão segue das premissas usando regras específicas.

**Como agir em cada método:**

**(a) Prova Condicional**
* *Quando usar:* Quando a **conclusão** é uma implicação ($A \to B$).
* *Ação:* Você assume o lado esquerdo da conclusão ($A$) como uma nova premissa provisória e tenta chegar no lado direito ($B$).
* *Exemplo:* Quer provar $P \to Q$.
    1. Assuma $P$ (Premissa Provisória).
    2. Use as outras regras.
    3. Chegue em $Q$.
    4. Conclua $P \to Q$.

**(b) Modus Ponens**
* *Regra de Ouro:* Se você tem "Se A então B" ($A \to B$) e você tem "A", você pode criar "B".
* *Ação:* Procure nas premissas uma implicação e a confirmação da primeira parte dela. Lembre-se de instanciar quantificadores universais ($\forall x$) para uma constante (tipo $s$ ou $a$) para poder "cortar".

**(c) e (d) Redução ao Absurdo (RAA)**
* *Estratégia:* "O advogado do diabo".
* *Ação:*
    1. Olhe para a conclusão que você quer provar.
    2. Assuma a **negação** dela como premissa.
    3. Tente encontrar uma contradição nas suas premissas (tipo $P \wedge \neg P$).
    4. Se achou a contradição, a sua suposição inicial estava errada, logo a conclusão original é verdadeira.

---

### **Questão 4: Tableaux Semântico (Árvores de Refutação)**

**O que a questão pede:** Provar visualmente que o argumento é válido.

**Como pensar:**
O Tableaux é uma prova por absurdo gráfica.
1.  Liste todas as premissas.
2.  Liste a **negação da conclusão**.
3.  Aplique as regras de expansão ($\alpha$ e $\beta$):
    * **Regra do "E" ($A \wedge B$):** Escreva um embaixo do outro.
    * **Regra do "OU" ($A \vee B$):** Abra a árvore em dois galhos (bifurcação).
    * **Regra da Implicação ($A \to B$):** Vira $\neg A \vee B$ (bifurca: $\neg A$ num galho, $B$ no outro).
4.  **Objetivo:** Tentar fechar todos os galhos. Um galho fecha quando você encontra uma contradição nele (tipo $Fa$ e $\neg Fa$). Se todos fecharem, o argumento é válido.

---

### **Questão 5: Interpretação de Modelos**

**O que a questão pede:** Substituir símbolos por valores matemáticos e dizer se é Verdadeiro ou Falso.

**O Cenário (Exemplo Análogo):**
* Universo = Números Naturais ($\mathbb{N} = \{0, 1, 2, ...\}$).
* $I[a] = 2$ (a constante 'a' vale 2).
* $I[f(d)] = d + 1$ (a função 'f' soma 1).
* $I[p(x,y)]$: significa $x > y$.

**Como resolver:**

* Item exemplo: $H = p(f(a), a)$
    1.  Substitua 'a' por 2: $p(f(2), 2)$.
    2.  Resolva a função $f(2)$: $2 + 1 = 3$.
    3.  Ficou: $p(3, 2)$.
    4.  Interprete o predicado: $3 > 2$?
    5.  **Resposta:** Verdadeiro.

* Item com quantificador: $\forall x (p(f(x), x))$
    1.  Tradução: "Para todo número natural $x$, o sucessor ($x+1$) é maior que $x$ ($x+1 > x$)".
    2.  Isso é verdade em $\mathbb{N}$? Sim.
    3.  **Resposta:** Verdadeiro.

---

### **Questão 6: Argumento em Texto**

**O que a questão pede:** Transformar texto em letras ($P, Q, R$), montar a fórmula e ver se faz sentido.

**Como agir:**
1.  **Crie um dicionário:**
    * $I$: Investimentos constantes.
    * $G$: Gastos aumentam.
    * $D$: Desemprego cresce.
    * $T$: Impostos reduzidos.

2.  **Traduza frase por frase:**
    * "Se investimentos constantes, então (gastos aumentam OU desemprego cresce)" $\rightarrow I \to (G \vee D)$.
    * "Se gastos NÃO aumentam, impostos reduzidos" $\rightarrow \neg G \to T$.
    * "Se impostos reduzidos E investimentos constantes, NÃO haverá desemprego" $\rightarrow (T \wedge I) \to \neg D$.

3.  **Analise a Conclusão:**
    * "Portanto, gastos não aumentarão" ($\neg G$).
    * *Dica:* Tente forçar que as premissas sejam verdadeiras e a conclusão falsa. Se conseguir, o argumento é inválido. Se não conseguir (der erro), é válido. (Ou use Tabela Verdade).

---

**Próximo Passo:**
Agora que você tem o "mapa mental" de como agir, escolha **uma** questão (sugiro a 1 ou a 5 para começar aquecendo) e tente resolver um item aqui comigo. Eu te digo se sua lógica está certa. O que acha?
