# NLP – UNIT I & UNIT II
## Short–Descriptive 10 Marks Answers (Clean, Exam-Ready)

---

# UNIT – I

## 1. Role of NLP in Modern Search Engines

NLP helps search engines understand user queries beyond simple keyword matching. It enables meaning-based, intent-based, and context-aware search.

### Key Roles
1. **Query Understanding**  
   Tokenization, stemming, POS tagging help identify important words.

2. **Semantic Search**  
   Uses embeddings (Word2Vec, BERT) to understand meaning.  
   Example: “fever treatment” ≈ “medicine for fever”.

3. **Intent Detection**  
   - Informational  
   - Transactional  
   - Navigational  
   Helps refine results.

4. **Named Entity Recognition (NER)**  
   Extracts people, places, dates for accurate results.

5. **Query Expansion**  
   Adds synonyms automatically.  
   Example: “car” → “automobile”.

6. **Content Ranking using NLP**  
   Pages are ranked based on relevance, semantic similarity, and context.

7. **Voice Search & Conversational Search**  
   NLP handles speech, follow-up questions, and natural dialogues.

**In summary**, NLP makes searching more intelligent, accurate, and human-like.

---

## 2. Challenges in Evaluating Language Understanding Systems

Language is complex and ambiguous, making NLP evaluation difficult.

### Challenges

1. **Ambiguity**  
   Words can have multiple meanings. Example: “bank”.

2. **Context Dependence**  
   Meaning changes based on surrounding sentences or situation.

3. **Subjectivity in Annotations**  
   Human annotators often disagree.

4. **Metric Limitations**  
   BLEU and ROUGE do not measure real meaning.

5. **Bias in Data**  
   Models may reflect racial, gender, or cultural bias.

6. **Domain Sensitivity**  
   A model trained on news may fail on medical data.

**Conclusion:** Evaluating NLP is difficult due to linguistic complexity and inconsistent human interpretation.

---

## 3. Major Levels of Language Analysis with Examples

NLP processes language in several layers:

### Levels

1. **Phonological** – sound patterns  
   Example: “read” pronounced differently in past and present.

2. **Morphological** – word formation  
   Example: happy → unhappiness (prefix + root + suffix)

3. **Lexical** – dictionary meanings  
   Example: “book” (noun/verb)

4. **Syntactic** – grammar structure  
   Example: NP + VP formation.

5. **Semantic** – literal meaning  
   Example: “Ravi ate an apple” → who did what.

6. **Pragmatic** – intended meaning  
   Example: “Can you open the window?” = request.

7. **Discourse** – context across sentences  
   Example: resolving pronouns (“he”, “it”).

---

## 4. Frame-Based vs Logic-Based Knowledge Representation

### Frame-Based
- Uses objects with attributes (slots).
- Example Frame:
  Car:
    - Color: Red
    - Type: SUV
- Easy to understand and supports inheritance.

### Logic-Based
- Uses first-order logic like:
  Car(Toyota), Color(Toyota, Red)
- More expressive and good for reasoning.

### Comparison
| Feature | Frame-Based | Logic-Based |
|--------|-------------|-------------|
| Structure | Slot-value | Predicates |
| Inference | Weak | Strong |
| Complexity | Low | High |
| Best Use | Simple KR | Rule-based reasoning |

---

## 5. Architecture of a Typical NLU System

### Block Diagram (Text Form)

Input  
 ↓  
Lexical Analysis  
 ↓  
Syntax Analysis  
 ↓  
Semantic Analysis  
 ↓  
Pragmatic Analysis  
 ↓  
Discourse Integration  
 ↓  
Output Meaning  

### Explanation
- **Lexical:** splits text into tokens  
- **Syntax:** builds parse tree  
- **Semantic:** assigns meaning  
- **Pragmatic:** interprets context  
- **Discourse:** handles multi-sentence meaning

---

## 6. Linguistic Background of English Language

### Key Points
- Originated from **Germanic languages**, influenced by **French** and **Latin**.
- Uses **26-letter alphabet**.
- Has **Subject-Verb-Object (SVO)** order.
- Morphology is simple; relies more on word order.
- Vocabulary is the largest due to borrowing.
- English pronunciation is irregular:
  Example: “though”, “tough”, “through”.

---

# UNIT – II

## 1. Top-Down & Bottom-Up Parsing for “The cat chased the mouse”

### Grammar
S → NP VP  
NP → Det N  
VP → V NP  

### Top-Down Parse Tree (Text Diagram)

S  
├── NP  
│   ├── Det(the)  
│   └── N(cat)  
└── VP  
    ├── V(chased)  
    └── NP  
        ├── Det(the)  
        └── N(mouse)  

### Bottom-Up Derivation
the → Det  
cat → N → NP  
the mouse → NP  
NP V NP → S

---

## 2. Transition Network Grammar for a Noun Phrase

Noun phrase = Det + (Adj)* + N

### Diagram (Text Form)
(Start) → Det → State1 → Adj* → State2 → N → (Final)

---

## 3. Augmented Grammars with Number and Gender Agreement

### Number Feature Example:
NP(num=X) → Det(num=X) N(num=X)

Correct: these books  
Incorrect: these book

### Gender Feature Example:
Spanish:
niña bonita (fem)  
niño bonito (masc)

---

## 4. Shannon Game (Letter Prediction)

Shannon proposed predicting next characters based on probabilities.

Example:
Sentence: “the cat”
- After “t”: “h” is most probable  
- After “th”: “e” is most probable  

Foundation for:
- n-grams  
- Markov models  
- Language models  

---

## 5. ATN for Simple English Sentences

### ATN Structure

Sentence-Network:
 S0 → NP → S1 → VP → S2 → ACCEPT

NP-Network:
 NP0 → Det → NP1 → N → RETURN

VP-Network:
 VP0 → V → VP1 → NP → RETURN

---

## 6. Why Cross-Entropy Loss is Used in NLP?

### Reasons
- Measures difference between predicted & true probabilities.
- Works with Softmax output.
- Penalizes incorrect predictions strongly.
- Improves training speed and accuracy.
- Best for classification tasks like:
  - next-word prediction  
  - translation  
  - text classification  

---

# END OF NOTES
