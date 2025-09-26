# Tokenização

<img width="1504" height="880" alt="Image" src="https://github.com/user-attachments/assets/5c4efaf1-a6f7-4992-82f0-454545928615" />

## 1. Conceito
- **Tokenização** é o processo de dividir o texto em partes menores chamadas **tokens** (palavras, subpalavras, caracteres ou bytes).  
- Esses tokens são então convertidos em **IDs numéricos**, que são o que os modelos realmente processam.  
- **Objetivo**: representar o texto de forma **significativa para a máquina**, sem perder contexto.  
- Isso permite que os algoritmos reconheçam padrões e compreendam a linguagem humana.

---

## 2. Por que é importante?
- **Eficiência**: menos tokens = menor custo computacional.  
- **Custos e limites**: modelos de IA contam tokens (não palavras) → prompts longos custam mais e podem estourar o limite de contexto.  
- **Precisão**: uma tokenização bem feita melhora a compreensão de nuances e reduz problemas com palavras desconhecidas (*OOV*).  

---

## 3. Tipos de Tokenização

### a) Tokenização de Palavras
- Divide o texto em palavras inteiras.  
- Bom para idiomas com separação clara (ex.: inglês).  
- **Limitação**: não lida bem com palavras raras ou novas.

### b) Tokenização de Caracteres
- Cada caractere é um token.  
- Útil em idiomas sem separação clara de palavras (ex.: chinês, japonês).  
- **Contras**: gera sequências muito longas.

### c) Tokenização de Subpalavras
- Divide em pedaços menores que uma palavra, mas maiores que caracteres.  
- Ex.: *Chatbots* → "Chat" + "bots".  
- Bom para lidar com palavras desconhecidas ou compostas.  
- Métodos principais:  
  - **BPE (Byte Pair Encoding)**: combina pares frequentes.  
  - **WordPiece**: usado em BERT, otimiza segmentação pelo corpus.  
  - **Unigram**: seleciona subpalavras mais prováveis, usado em SentencePiece.

### d) Byte-level BPE
- Baseado em bytes (0–255).  
- Suporta **qualquer caractere Unicode**, emojis e textos multilíngues.  
- Evita problemas de OOV (fora do vocabulário).

---

## 4. Ferramentas e Implementações

- **NLTK**  
  Biblioteca em Python, oferece tokenização de palavras e frases. Boa para aprendizado inicial.

- **spaCy**  
  Rápida e eficiente, suporta múltiplos idiomas, indicada para aplicações de grande escala.

- **BERT Tokenizer**  
  Baseado em subpalavras (WordPiece), reconhece nuances de contexto.  
  Essencial em projetos avançados de NLP.

- **SentencePiece**  
  Não supervisionado, funciona bem em vários idiomas.  
  Usa Unigram ou BPE para gerar subpalavras.

- **Hugging Face Transformers**  
  - Tokenizadores rápidos escritos em Rust.  
  - Suporte a BPE, WordPiece e Unigram.  
  - Modelos já vêm com tokenizadores pré-treinados correspondentes.

---

## 5. Tokens Especiais
- `<bos>` → início da sequência.  
- `<eos>` → fim da sequência.  
- `<pad>` → preenchimento.  
- `<unk>` → token desconhecido.  
- `<mask>` → usado em treino de modelos como BERT.  

---

## 6. Exemplo Didático
Frase: **“Não vou ao café às 8h30.”**

- **Word-level**: ["Não", "vou", "ao", "café", "às", "8h30", "."]  
- **BPE**: ["Não", "vou", "ao", "caf", "##é", "às", "8", "h", "30", "."]  
- **SentencePiece**: ["▁Não", "▁vou", "▁ao", "▁café", "▁às", "▁8", "h", "30", "."]

---

## 7. Boas Práticas
- Padronizar texto (acentos, maiúsculas, espaços).  
- Usar delimitadores claros (listas, tabelas, blocos de código).  
- Dividir documentos longos em **chunks por tokens**, não por caracteres.  
- Monitorar número de tokens com ferramentas (ex.: contadores da OpenAI ou Hugging Face).  

---

## 8. Resumindo
- Tokenização ≠ divisão por palavras.  
- É a **ponte entre linguagem humana e números** que a máquina entende.  
- Métodos modernos usam **subpalavras** ou **bytes** para eficiência.  
- A escolha da ferramenta/tokenizador depende do **idioma** e do **tipo de projeto**.

[Acesse o Tiktokenizer](https://tiktokenizer.vercel.app/)
