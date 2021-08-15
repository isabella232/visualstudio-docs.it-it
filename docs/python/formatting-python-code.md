---
title: Formattare il codice Python
description: Visual Studio è in grado di riformattare automaticamente il codice Python, inclusi spaziatura, istruzioni, ritorno a capo e commenti.
ms.date: 03/13/2019
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.technology: vs-python
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: b6852d06048acf86f50c8d56fb91bc8a298ec949d77d9a23afef5cc56adb68ae
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121230196"
---
# <a name="format-python-code"></a>Formattare il codice Python

Visual Studio consente di riformattare rapidamente il codice in base a opzioni di formattazione preconfigurate.

- Per formattare una selezione: selezionare **Modifica**  >  **selezione formato**  >  **avanzata** o premere **CTRL** + **E**  >  **F**.
- Per formattare l'intero file, selezionare **Modifica**  >  **documento**  >  **di formato avanzato** o premere  +   >  **CTRL+D.**

Le opzioni vengono impostate tramite Strumenti **Opzioni**  >  **Editor di** testo  >    >  **Formattazione Python**  >   e le relative schede annidate. È necessario selezionare **Mostra tutte le impostazioni** per visualizzare queste opzioni:

![Opzioni di formattazione di Python in Visual Studio](media/options-editor-formatting.png)

Per impostazione predefinita, le opzioni di formattazione sono impostate in modo corrispondente a un superset della [guida di stile PEP 8](https://www.python.org/dev/peps/pep-0008/). La scheda **Generale** determina quando viene applicata la formattazione. Le impostazioni per le altre tre schede sono descritte in questo articolo.

Il [supporto di Python in Visual Studio](installing-python-support-in-visual-studio.md) aggiunge anche l'utile comando [**Riempi paragrafo di commento**](#fill-comment-paragraph-command) al menu **Modifica** > **Avanzate** come descritto in una sezione successiva.

## <a name="spacing"></a>Spaziatura

La scheda **Spacing** (Spaziatura) consente di controllare la posizione in cui inserire o rimuovere gli spazi attorno a costrutti di linguaggio. Esistono tre possibili valori per ogni opzione:

- Selezionato con segno di spunta: assicura che la spaziatura venga applicata.
- Deselezionato: rimuove qualsiasi spaziatura.
- Indeterminato: mantiene la formattazione originale.

Le tabelle seguenti includono esempi per le varie opzioni:

| Opzione Definizioni di classe | Selezionata | Cancellato |
| --- | --- | --- |
| **Insert space between a class declaration's name and bases list (Inserisci spazio tra il nome della dichiarazione di classe e l'elenco di basi)** | `class X (object): pass` | `class X(object): pass` |
| **Insert space within bases list parentheses (Inserisci spazio tra le parentesi dell'elenco di basi)** | `class X( object ): pass` | `class X(object): pass` |
| **Insert space within empty bases list parentheses (Inserisci spazio tra le parentesi dell'elenco di basi vuoto)** | `class X( ): pass` | `class X(): pass` |

<br/>

| Opzione Definizioni di funzioni | Selezionata | Cancellato |
| --- | --- | --- |
| **Insert space between a function declaration's name and parameter list (Inserisci spazio tra il nome della dichiarazione di funzione e l'elenco di parametri)** | `def X (): pass` | `def X(): pass` |
| **Insert space within parameter list parentheses (Inserisci spazio tra le parentesi dell'elenco di parametri)** | `def X( a, b ): pass` | `def X(a, b): pass` |
| **Insert space within empty parameter list parentheses (Inserisci spazio tra le parentesi dell'elenco di parametri vuoto)** | `def X( ): pass` | `def X(): pass` |
| **Insert spaces around '=' in default parameter values (Inserisci spazi intorno a '=' nei valori di parametri predefiniti)** | `includes X(a = 42): pass` | `includes X(a=42): pass` |
| **Insert space before and after return annotation operators (Inserisci spazio prima e dopo gli operatori di annotazione di restituzione)** | `includes X() -> 42: pass` | `includes X()->42: pass` |

<br/>

| Opzione Operators (Operatori) | Selezionata | Cancellato |
| --- | --- | --- |
| **Inserisci spazio tra gli operatori binari** | `a + b` | `a+b` |
| **Inserisci gli spazi intorno agli operatori di assegnazione** | `a = b` | `a=b` |

<br/>

| Opzione Expression spacing (Spaziatura espressioni) | Selezionata | Cancellato |
| --- | --- | --- |
| **Inserisci spazio tra il nome della funzione e l'elenco argomenti nelle chiamate** | `X ()` | `X()` |
| **Inserisci spazio tra le parentesi dell'elenco di argomenti vuoto** | `X( )` | `X()` |
| **Inserisci spazio tra le parentesi dell'elenco di argomenti** | `X( a, b )` | `X(a, b)` |
| **Inserisci spazio tra le parentesi delle espressioni** | `( a )` | `(a)` |
| **Inserisci spazio tra le parentesi della tupla vuota** | `( )` | `()` |
| **Inserisci spazio tra le parentesi della tupla** | `( a, b )` | `(a, b)` |
| **Inserisci uno spazio tra parentesi quadre vuote** | `[ ]` | `[]` |
| **Inserisci spazio tra le parentesi quadre degli elenchi** | `[ a, b ]` | `[a, b]` |
| **Inserisci spazio prima della parentesi quadra di apertura** | `x [i]` | `x[i]` |
| **Inserisci spazio tra parentesi quadre** | `x[ i ]` | `x[i]` |

<br/>

## <a name="statements"></a>Istruzioni

Le opzioni relative alle **istruzioni** consentono di controllare la riscrittura automatica di varie istruzioni in altri formati Python.

| Opzione | Prima della formattazione | Dopo la formattazione |
| --- | --- | --- |
| **Inserisci i moduli importati in una nuova riga** | `import sys, pickle` | `import sys`<br/>`import pickle` |
| **Rimuovi i punti e virgola non necessari** | `x = 42;` | `x = 42` |
| **Place multiple statements on new lines** (Inserisci più istruzioni in nuove righe) | `x = 42; y = 100` | `x = 42`<br/>`y = 100` |

## <a name="wrapping"></a>Ritorno a capo

**Wrapping** consente di impostare la **larghezza massima dei commenti**, che per impostazione predefinita è 80. Se viene impostata l'opzione **Esegui il wrapping dei commenti troppo lunghi**, Visual Studio riformatta i commenti in modo che non superino la larghezza massima.

```python
# Wrapped to 40 columns
# There should be one-- and preferably
# only one --obvious way to do it.
```

```python
# Not-wrapped:
# There should be one-- and preferably only one --obvious way to do it.
```

## <a name="fill-comment-paragraph-command"></a>Comando Fill Comment Paragraph (Riempi paragrafo commenti)

**Modifica**  >  **Avanzate**  >  **Riempi paragrafo di commento** (**CTRL** E P ) ridisposi il testo dei commenti e lo formatta, combinando le righe brevi e +   >  suddividendo quelle lunghe.

Esempio:

```python
# foo
# bar
# baz
```

diventa:

```python
# foo bar baz
```

```python
# This is a very long long long long long long long long long long long long long long long long long long long comment
```

diventa:

```python
# This is a very long long long long long long long long long long long long
# long long long long long long long comment
```
