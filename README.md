# Pitanja

The Pitanja file is a custom file format designed for the sole purpose of easily structuring questions
for matura examinations conducted by the *Pedagogical institute of Tuzla canton*. 

# Pitanja file specification

Every Pitanja file is a standard UTF-8 encoded plaintext file with the following structure:

- Its first line is a declaration of form `@PITANJA_FILE <name>`
- Questions are declared by `@PITANJE <type>`
- Questions are delimited by `---===---`
- After every question declaration a new line starts with `??? <question>`
- Empty lines are ignored

The following subsections shall further describe all possible question types.

## zaokruzi

These are the questions which offer several answers, out of which at least one is correct and their
structure is the following:

- Every correct answer starts with a `@+`
- Every incorrect answer starts with a `@-`

## da-ne

These are the questions whose only answers can be "yes" and "no". For the sake of easier parsing,
their internal representation shall be "true" and "false".

- If the answer is "yes", then it is declared with a `@DA`, otherwise it is declared as `@NE`

## dopuni

These are the questions which require the user to add missing words/sentences into empty spaces. Any number
of possible/alternative answers can be provided, but they should all be case insensitive.

- The question itself denotes these missing parts with `{{{#}}}` where `#` is the answer number
- Every answer (or its alternative) starts with `@#` where `#` is the answer number.

# Example

Here is an example of a Pitanja file

```
@PITANJA_FILE bosanski

@PITANJE zaokruzi
??? Poznati srednjovjekovni bosanski pisani spomenici su?
@- romani
@- balade
@- pjesme
@+ natpisi na stećcima

---===---

@PITANJE da-ne
??? Hektor je lik iz epa "Ilijada"?
@TACNO

---===---

@PITANJE dopuni
??? Kakva je po sastavu rečenica "Kad urediš zapisnik, donesi ga na potpis."? {{{1}}}
@1 prosta
@1 prosto-proširena
@1 proširena

---===---
```
