---
title: Comando Sostituisci
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- edit.replace
helpviewer_keywords:
- Edit.Replace command
- Replace command
ms.assetid: a15767f1-5a3d-44f5-8c77-7b0f1157f340
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 620e55938a9c96393d8cd7de6f238d3f98715d29
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "75596684"
---
# <a name="replace-command"></a>Comando Sostituisci
Sostituisce il testo nei file usando un subset delle opzioni disponibili nella scheda **Sostituisci nei file** della finestra **Trova e sostituisci**.

## <a name="syntax"></a>Sintassi

```
Edit.Replace findwhat replacewith [/all] [/case]
[/doc|/proc|/open|/sel] [/hidden] [/options] [/reset] [/up]
[/wild|/regex] [/word]
```

## <a name="arguments"></a>Argomenti
`findwhat`

Obbligatorio. Testo da cercare.

`replacewith`

Obbligatorio. Il testo di sostituzione per il testo corrispondente.

## <a name="switches"></a>Commutatori
/all o /a

facoltativo. Sostituisce tutte le occorrenze del testo di ricerca con il testo di sostituzione.

/case o /c

facoltativo. Vengono rilevate corrispondenze solo se i caratteri maiuscoli e minuscoli corrispondono esattamente a quelli specificati nell'argomento `findwhat`.

/doc o /d

facoltativo. Cerca solo nel documento corrente. Specificare solo uno degli ambiti di ricerca disponibili, `/doc`, `/proc`, `/open` o `/sel`.

/hidden o /h

facoltativo. Cerca il testo compresso e nascosto, come i metadati di un controllo DTC, un'area nascosta di un documento strutturato o un metodo o una classe compressi.

/open o /o

facoltativo. Cerca in tutti i documenti aperti come se fossero un unico documento. Specificare solo uno degli ambiti di ricerca disponibili, `/doc`, `/proc`, `/open` o `/sel`.

/options o /t

facoltativo. Visualizza l'elenco delle impostazioni correnti dell'opzione di ricerca e non esegue una ricerca.

/proc o /p

facoltativo. Cerca solo nella routine corrente. Specificare solo uno degli ambiti di ricerca disponibili, `/doc`, `/proc`, `/open` o `/sel`.

/regex o /r

facoltativo. Usa caratteri speciali predefiniti nell'argomento `findwhat` come notazioni che rappresentano modelli di testo anziché i caratteri letterali. Per l'elenco completo dei caratteri espressione regolare, vedere [Espressioni regolari](../../ide/using-regular-expressions-in-visual-studio.md).

/reset o /e

facoltativo. Ripristina le impostazioni predefinite delle opzioni di ricerca e non esegue la ricerca.

/sel o /s

facoltativo. Cerca solo nella selezione corrente. Specificare solo uno degli ambiti di ricerca disponibili, `/doc`, `/proc`, `/open` o `/sel`.

/up o /u

facoltativo. Esegue la ricerca dalla posizione corrente nel file verso la parte superiore del file. Per impostazione predefinita, le ricerche iniziano in corrispondenza della posizione del file e procedono verso la fine del file.

/wild o /l

facoltativo. Usa caratteri speciali predefiniti nell'argomento `findwhat` come notazioni per rappresentare un carattere o una sequenza di caratteri.

/word o /w

facoltativo. Cerca solo parole intere.

## <a name="example"></a>Esempio
In questo esempio `btnSend` con `btnSubmit` tutti i documenti aperti.

```
>Edit.Replace btnSend btnSubmit /open
```

## <a name="see-also"></a>Vedere anche

- [Ricerca e sostituzione di testo](../../ide/finding-and-replacing-text.md)
- [Finestra di comando](../../ide/reference/command-window.md)
- [Casella Trova/comando](../../ide/find-command-box.md)
- [Comandi di Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Alias di comandi di Visual Studio](../../ide/reference/visual-studio-command-aliases.md)
