# NLP – UNIT I & UNIT II  
### Full 10-Marks Descriptive Answers (Exam Ready)

---

# ⭐ UNIT – I

---

## **1. Explain the role of NLP techniques in modern search engines. (10 Marks)**

Modern search engines like Google, Bing, and DuckDuckGo use Natural Language Processing (NLP) to understand the meaning behind user queries rather than relying only on keywords. NLP enhances search quality by analyzing language at multiple levels—lexical, syntactic, semantic, and contextual. The goal is to interpret *what the user intends*, not just *what the user types*.

---

### **1. Query Processing and Normalization**
Search engines first clean and process the query using:
- **Tokenization** – Splitting text into words  
- **Stemming/Lemmatization** – Converting "running", "ran" → "run"  
- **Stop-word Removal** – Removing “the”, “is”, “of”  
- **Spelling Correction** – Fixing typos (e.g., “wheather” → “weather”)  
This ensures high-quality matching with search indexes.

---

### **2. Semantic Understanding**
To understand word meaning, modern search engines use:
- **Word embeddings** (Word2Vec, GloVe)  
- **Contextual models** (BERT, GPT)  
These capture relationships between words.  
Example:  
“heart attack treatment” ≈ “cardiac arrest cure”  
Even though words differ, the meaning is the same.

---

### **3. Understanding User Intent**
Search engines classify queries into:
- **Informational** (“What is NLP?”)  
- **Transactional** (“buy iPhone 15 online”)  
- **Navigational** (“YouTube login”)  
- **Local** (“restaurants near me”)  

Accurate intent detection ensures more relevant results.

---

### **4. Named Entity Recognition (NER)**
NLP identifies named entities:
- People  
- Countries  
- Brands  
- Dates  
Example: “population of India 2024”  
NER extracts: India (country), 2024 (year)

---

### **5. Query Expansion**
NLP adds synonyms and related words automatically:
- “car” → “automobile”  
- “virus” → “malware” (in tech context)  

This helps retrieve more accurate results.

---

### **6. Ranking Using NLP**
After retrieving documents, NLP helps rank them by:
- Relevance  
- Semantic similarity  
- Topic alignment  
- User intent match  

Models like **BERT** significantly improve search ranking compared to older keyword-based approaches.

---

### **7. Voice Search and Conversational Search**
NLP helps in:
- Speech recognition  
- Dialogue context tracking  
- Follow-up question understanding  

Example:  
User: “Who is Virat Kohli?”  
User: “How old is he?” → NLP resolves “he”.

---

### **Conclusion**
NLP makes search engines intelligent, context-aware, and human-like by enabling deeper understanding of user queries, content, and intent.

---

---

## **2. Discuss the challenges in evaluating language understanding systems. (10 Marks)**

Evaluating Natural Language Understanding (NLU) systems is one of the hardest problems in NLP because human language is inherently ambiguous, context-dependent, culturally influenced, and subjective. Unlike math problems, language tasks often don’t have a single correct answer.

---

### **1. Ambiguity in Language**
Words and sentences often have multiple interpretations.  
Example:  
“I saw the man with the telescope.”  
Who has the telescope?  
Systems struggle with such ambiguity.

---

### **2. Context-Dependency**
Meaning depends on:
- Previous sentences  
- Speaker intention  
- World knowledge  

Example:  
“The glass fell and broke.”  
The system must infer *glass* broke.

---

### **3. Lack of Standard Evaluation Metrics**
Metrics such as:
- **BLEU**  
- **ROUGE**  
- **Accuracy**  
don’t always reflect true language understanding.  
For example, paraphrased answers may be penalized despite being correct.

---

### **4. Annotation Difficulty**
Human annotators may disagree about:
- Sentiment  
- Relevance  
- Intent  
This inconsistency makes evaluation unreliable.

---

### **5. Domain Variations**
A model trained on:
- News articles  
may fail on  
- medical or legal texts.

Thus evaluation must be domain-specific.

---

### **6. Bias in Training Data**
Models inherit biases from datasets (gender, political, cultural).  
This affects evaluation fairness.

---

### **7. Creativity and Diversity in Human Language**
Humans express the same meaning in many ways:
- “yes”, “yeah”, “sure”, “okay”, “absolutely”  
Difficult for metrics to judge correctness.

---

### **Conclusion**
Evaluation of NLU systems is challenging due to ambiguity, subjective interpretation, poor metrics, and domain variability. Better human-AI hybrid evaluation systems are required.

---

---

## **3. Explain all major levels of language analysis with suitable examples. (10 Marks)**

Language analysis occurs in layers, each contributing to understanding natural language. Together, these layers enable NLP systems to convert raw text into meaningful representations.

---

### **1. Phonological Level**
Deals with sound patterns.  
Example:  
“read” (present: /riːd/) vs “read” (past: /rɛd/)

---

### **2. Morphological Level**
Studies how words are formed from morphemes.  
Example:  
“unhappiness” = un + happy + ness

---

### **3. Lexical Level**
Focuses on word meaning and word categories.  
Example:  
“book” can be a noun or a verb.

Includes:
- POS tagging  
- Word sense disambiguation  

---

### **4. Syntactic Level**
Analyses grammatical structure.  
Example:  
“The dog chased the cat.”  
S → NP + VP  
Forms the parse tree.

---

### **5. Semantic Level**
Assigns meaning.  
Example:  
“Ravi ate an apple.”  
- Ravi = agent  
- Apple = object  
- Eat = action

---

### **6. Pragmatic Level**
Interprets meaning based on user intention and context.  
Example:  
“Can you open the window?”  
Meaning → Request, not a question.

---

### **7. Discourse Level**
Connects meaning across sentences.  
Example:  
“John bought a bike. He loves it.”  
He → John  
It → bike

---

### **Conclusion**
These layers allow NLP systems to understand language at every depth—from sounds to discourse-level meaning.

---

---

## **4. Compare frame-based and logic-based approaches to knowledge representation. (10 Marks)**

Knowledge Representation (KR) is essential for enabling NLP systems to reason about meaning. Two popular KR techniques are **Frame-Based** and **Logic-Based** approaches.

---

### **Frame-Based KR**
Frames are structured data templates similar to objects in OOP.  
They represent knowledge using **slots** (attributes) and **values**.

Example Frame:
```
Car:
  Brand: Toyota
  Color: Red
  Type: Sedan
```

### **Advantages**
- Simple and intuitive  
- Supports inheritance  
- Fast lookup  

### **Limitations**
- Not suitable for complex reasoning  
- Hard to represent rules  

---

### **Logic-Based KR**
Uses mathematical logic (mainly first-order logic) for representation.

Example:
```
Car(Toyota)
Color(Toyota, Red)
Type(Toyota, Sedan)
```

### **Advantages**
- Highly expressive  
- Supports formal reasoning  
- Can infer new facts

### **Limitations**
- Computationally expensive  
- Syntax and rules can be complex  

---

### **Comparison Table**
| Feature | Frame-Based | Logic-Based |
|--------|-------------|-------------|
| Structure | Slot-value | Predicate logic |
| Inference | Weak | Strong |
| Ease of Use | Easy | Difficult |
| Expressiveness | Low | High |
| Best For | Simple object knowledge | Expert systems |

---

### **Conclusion**
Frames are ideal for structured knowledge, whereas logic-based representations are powerful for reasoning and rule-based inference.

---

---

## **5. Explain with a neat block diagram the architecture of a typical NLU system. (10 Marks)**

A Natural Language Understanding (NLU) system converts raw human text into machine-interpretable meaning. The system uses several layers of processing.

---

### **Block Diagram (Text Representation)**

```
+------------------+
|     Input Text     |
+------------------+
          |
          v
+------------------+
| Lexical Analysis |
+------------------+
          |
          v
+------------------+
| Syntax Analysis  |
+------------------+
          |
          v
+------------------+
| Semantic Analysis |
+------------------+
          |
          v
+------------------+
| Pragmatic Analysis|
+------------------+
          |
          v
+-----------------------------+
| Final Meaning Representation |
+-----------------------------+
```

---

### **1. Lexical Analysis**
Breaks input into tokens and identifies word categories.

### **2. Syntax Analysis**
Builds grammatical structure (parse tree) from tokens.

### **3. Semantic Analysis**
Maps syntax structures to meaning, resolves word senses, identifies relationships.

### **4. Pragmatic Analysis**
Considers user intention, context, speaker meaning.

### **5. Discourse Integration**
Ensures consistency across multiple sentences.

---

### **Conclusion**
NLU architecture processes input step-by-step, ensuring accurate interpretation of text.

---

---

## **6. Explain the Linguistic Background of the English Language. (10 Marks)**

English is a Germanic language with influences from Latin, French, and Norse. Over more than 1500 years, English has evolved into one of the most widely spoken languages.

---

### **1. Origin and History**
- English originated from **West Germanic dialects** (Angles, Saxons, Jutes).  
- Later influenced by **Viking (Norse)** invasions.  
- After the Norman Conquest (1066), **French** heavily influenced English vocabulary.  

---

### **2. English Alphabet & Writing System**
- Uses the **26-letter Latin alphabet**.  
- English spelling is not phonetic (“though”, “through”, “tough”).  

---

### **3. Grammar Characteristics**
- English follows **SVO structure**:  
  “She reads books.”  
- Has limited inflections (less morphological complexity).

---

### **4. Vocabulary**
English has one of the **largest vocabularies** in the world because it borrows from:
- Latin  
- French  
- Greek  
- German  

Example:  
- Latin: “radius”  
- French: “restaurant”  
- Greek: “psychology”

---

### **5. Phonological Features**
English pronunciation varies widely across regions:
- American  
- British  
- Australian  

---

### **Conclusion**
English evolved through contact with many cultures, making it rich, complex, and globally dominant.

---

# ⭐ UNIT – II

---

## **1. Construct both top-down and bottom-up parses for the sentence: “The cat chased the mouse.” (10 Marks)**

### **Grammar Used**
```
S → NP VP
NP → Det N
VP → V NP
Det → the
N → cat | mouse
V → chased
```

---

### **A) Top-Down Parsing**

Start with **S** and expand using grammar rules.

```
S
├── NP
│   ├── Det → the
│   └── N → cat
└── VP
    ├── V → chased
    └── NP
        ├── Det → the
        └── N → mouse
```

Thus final generated sentence:  
**the cat chased the mouse**

---

### **B) Bottom-Up Parsing**

Start from words and build upwards.

1. the → Det  
2. cat → N  
3. Det + N → NP  
4. chased → V  
5. the mouse → NP  
6. NP + V + NP → S  

Thus final reduced form:  
**S**

---

## **2. Construct a transition network grammar for a simple English noun phrase. (10 Marks)**

A noun phrase typically consists of:
```
Det + (Adj)* + N
```

### **Transition Network Diagram (Text Form)**

```
(Start)
   |
   v
[Det] ---> [Adj Loop] ---> [Noun] ---> (Final)
```

- From Start → Determiner  
- Determiner → Adjectives (0 or more times)  
- Adjectives → Noun  
- Noun → Final state  

---

## **3. Discuss augmented grammars with number and gender agreement. (10 Marks)**

Augmented grammars extend CFGs by adding **feature structures** (like number, gender, person).

---

### **1. Number Agreement**

Example rule:
```
NP(num=X) → Det(num=X) N(num=X)
```

Correct:
- these books  
Incorrect:
- these book  

---

### **2. Gender Agreement (Spanish Example)**

Spanish adjectives agree with nouns:
```
Adj(gender=X) N(gender=X)
```

Examples:
- niño bonito (masculine)  
- niña bonita (feminine)  

---

## **4. Explain the Shannon game with an example of letter prediction. (10 Marks)**

Claude Shannon introduced a game where you predict the next letter in a sentence based on probability.

---

### **Example: “the cat”**

Predict next character after:
- “t” → likely “h”  
- “th” → likely “e”  
- “the ” → likely “c” or “s”

This forms the basis of:
- n-gram models  
- Markov chains  
- language models  

---

## **5. Construct an Augmented Transition Network (ATN) for parsing simple English sentences. (10 Marks)**

### **ATN Structure**

```
Sentence Network:
 S0 → (call NP) → S1
 S1 → (call VP) → S2
 S2 → ACCEPT

NP Network:
 NP0 → Det → NP1 → N → RETURN

VP Network:
 VP0 → V → VP1 → NP → RETURN
```

ATNs support:
- recursion  
- conditions  
- registers  

---

## **6. Why cross-entropy loss is used in NLP? (10 Marks)**

Cross-entropy measures the distance between predicted probabilities and the true distribution.

---

### **Reasons**

1. **Works well with Softmax**  
2. **Penalizes wrong predictions strongly**  
3. **Provides smooth gradients**  
4. **Ideal for classification tasks**  
5. **Used in:**
   - next-word prediction  
   - translation  
   - text classification  

---

# 🎉 END OF README.md
