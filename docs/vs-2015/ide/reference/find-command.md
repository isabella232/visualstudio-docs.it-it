---
title: Comando Find | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- edit.find
helpviewer_keywords:
- Find command
- Edit.Find command
ms.assetid: f0c705dc-2b97-423d-abbf-5584d4827208
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 6ce0e4a3aaca752cbdeda0a83e469977306c3404
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72657687"
---
# <a name="find-command"></a>Comando Trova
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Esegue la ricerca di testo nei file usando un subset delle opzioni disponibili nella scheda **Cerca nei file** della finestra **Trova e sostituisci**.

## <a name="syntax"></a>Sintassi

```
Edit.Find findwhat [/case] [/doc | /proc | /open | /sel]
[/markall] [/options] [/reset] [/up] [/wild | /regex] [/word]
```

## <a name="arguments"></a>Argomenti
 `findwhat` Obbligatorio. Testo da cercare.

## <a name="switches"></a>Opzioni
 /case o /c Facoltativo. Vengono rilevate corrispondenze solo se i caratteri maiuscoli e minuscoli corrispondono esattamente a quelli specificati nell'argomento `findwhat`.

 /doc o /d Facoltativo. Cerca solo nel documento corrente. Specificare solo uno degli ambiti di ricerca disponibili, `/doc`, `/proc`, `/open` o `/sel`.

 /markall o /m Facoltativo. Inserisce un grafo per ogni riga che contiene una corrispondenza della ricerca all'interno del documento corrente.

 /open or /o Facoltativo. Cerca in tutti i documenti aperti come se fossero un unico documento. Specificare solo uno degli ambiti di ricerca disponibili, `/doc`, `/proc`, `/open` o `/sel`.

 /open or /o Facoltativo. Visualizza l'elenco delle impostazioni correnti dell'opzione di ricerca e non esegue una ricerca.

 /proc o /p Facoltativo. Cerca solo nella routine corrente. Specificare solo uno degli ambiti di ricerca disponibili, `/doc`, `/proc`, `/open` o `/sel`.

 /reset o /e Facoltativo. Ripristina le impostazioni predefinite delle opzioni di ricerca e non esegue la ricerca.

 /sel o /s Facoltativo. Cerca solo nella selezione corrente. Specificare solo uno degli ambiti di ricerca disponibili, `/doc`, `/proc`, `/open` o `/sel`.

 /up o/u Facoltativo. Esegue la ricerca dalla posizione corrente nel file verso l'inizio del file. Per impostazione predefinita, le ricerche iniziano in corrispondenza della posizione nel file e procedono verso la fine del file.

 /regex o /r Facoltativo. Usa caratteri speciali predefiniti nell'argomento `findwhat` come notazioni che rappresentano modelli di testo anziché i caratteri letterali. Per l'elenco completo dei caratteri espressione regolare, vedere [Espressioni regolari](../../ide/using-regular-expressions-in-visual-studio.md).

 /wild o /l Facoltativo. Usa caratteri speciali predefiniti nell'argomento `findwhat` come notazioni per rappresentare un carattere o una sequenza di caratteri.

 /word o /w Facoltativo. Cerca solo parole intere.

## <a name="example"></a>Esempio
 In questo esempio viene eseguita una ricerca con distinzione tra maiuscole e minuscole della parola "string" nella sezione di codice attualmente selezionata.

```
>Edit.Find somestring /sel /case
```

## <a name="see-also"></a>Vedere anche
 [Finestra di comando ](../../ide/reference/command-window.md) [Find/Command Box ](../../ide/find-command-box.md) comandi di [Visual Studio ](../../ide/reference/visual-studio-commands.md) alias di comando di [Visual Studio](../../ide/reference/visual-studio-command-aliases.md)
