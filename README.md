# 📊 Análise de Padrões Raros na Mega-Sena

> *Uma investigação impulsionada pela curiosidade analítica: qual é a ocorrência real de padrões numéricos atípicos em jogos aleatórios?*

🔗 **Acesse o relatório e painel online:** [silvaniosg.github.io/analise_mega_sena](https://silvaniosg.github.io/analise_mega_sena/)

---

## 🎯 Contexto e Provocação

Durante o acompanhamento dos resultados da Mega-Sena, o **Concurso 2888** apresentou uma combinação peculiar de dezenas:

* **Dezenas Sorteadas:** `[3, 9, 15, 27, 39, 59]`
* **Vetor de Diferenças Consecutivas:** `[6, 6, 12, 12, 20]`

A cadência dos intervalos despertou uma dúvida prática: **esse padrão de espaçamento já havia ocorrido antes na história da loteria?**

---

## 🔄 Fluxo do Processo Analítico

```
[1. Hipótese] ➔ [2. Extração de Dados] ➔ [3. Processamento Vetorial] ➔ [4. Resultados] ➔ [5. Deploy]
```

1. **Hipótese:** Definir o cálculo de diferenças relativas consecutivas ($\Delta = x_{i+1} - x_i$) para cada concurso.
2. **Extração:** Leitura do histórico com 2.888 concursos usando `Pandas`.
3. **Processamento:** Varredura vetorial com `NumPy` para identificar a sequência exata `[6, 6, 12, 12, 20]`.
4. **Consolidação:** Mapeamento de frequência e probabilidade empírica.
5. **Deploy:** Criação da página responsiva via GitHub Pages.

---

## 🛠️ Código em Python

```python
import pandas as pd
import numpy as np

def calcular_diferencas(dezenas):
    return list(np.diff(sorted(dezenas)))

padrao_raro = [6, 6, 12, 12, 20]

url = "https://www.dropbox.com/scl/fi/22qkzvty0xq0g19fxaylf/mega_sena.csv?rlkey=w7c7il0jb7lp9l8cvqykhcz5h&dl=1"
df = pd.read_csv(url)

col_dezenas = [col for col in df.columns if 'dezena' in col.lower()]

ocorrencias = [
    i for i, row in df[col_dezenas].iterrows() 
    if calcular_diferencas(row.dropna().astype(int).tolist()) == padrao_raro
]
```

---

## 📈 Resultados Encontrados

| Métrica | Valor Registrado |
| :--- | :--- |
| **Total de Concursos Analisados** | 2.888 |
| **Ocorrências Anteriores do Padrão** | 0 (Inédito) |
| **Probabilidade Empírica** | **0,0346%** |

---

## ⚙️ Tecnologias Utilizadas

* **Linguagem & Análise:** Python 3 (Pandas, NumPy, Matplotlib)
* **Visualização & Deploy:** GitHub Pages (HTML5, CSS3)

---

## 👤 Sobre o Autor & Contato

**Silvânio Gois**  
*Gestor de Operações e Negócios orientados a dados.*

Atuo unindo gestão, processos e análise de dados para transformar informações brutas em clareza estratégica e tomada de decisão.

* 🌐 **Portfólio:** [silvaniogois.com.br](https://www.silvaniogois.com.br/)
* 💼 **LinkedIn:** [linkedin.com/in/silvanio-gois](https://www.linkedin.com/in/silvanio-gois/)
* 🚀 **Projeto Online:** [silvaniosg.github.io/analise_mega_sena](https://silvaniosg.github.io/analise_mega_sena/)
