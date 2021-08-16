---
title: Comando Trova
description: Informazioni sul comando Trova e su come cerca i file usando un subset delle opzioni disponibili nella scheda Trova nei file della finestra Trova e sostituisci.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- edit.find
helpviewer_keywords:
- Find command
- Edit.Find command
ms.assetid: f0c705dc-2b97-423d-abbf-5584d4827208
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: ca8096ae79885377ed2976934f181ff5ce1203f55245fab6baebe0d695430ab4
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121387486"
---
# <a name="find-command"></a>Comando Trova
Esegue la ricerca di testo nei file usando un subset delle opzioni disponibili nella scheda **Cerca nei file** della finestra **Trova e sostituisci**.

## <a name="syntax"></a>Sintassi

```cmd
Edit.Find findwhat [/case] [/doc | /proc | /open | /sel]
[/markall] [/options] [/reset] [/up] [/wild | /regex] [/word]
```

## <a name="arguments"></a>Argomenti
`findwhat` Obbligatorio. Testo da cercare.

## <a name="switches"></a>Commutatori
/case o /c\
facoltativo. Vengono rilevate corrispondenze solo se i caratteri maiuscoli e minuscoli corrispondono esattamente a quelli specificati nell'argomento `findwhat`.

/doc o /d\
facoltativo. Cerca solo nel documento corrente. Specificare solo uno degli ambiti di ricerca disponibili, `/doc`, `/proc`, `/open` o `/sel`.

/markall o /m\
facoltativo. Inserisce un grafo per ogni riga che contiene una corrispondenza della ricerca all'interno del documento corrente.

/open o /o\
facoltativo. Cerca in tutti i documenti aperti come se fossero un unico documento. Specificare solo uno degli ambiti di ricerca disponibili, `/doc`, `/proc`, `/open` o `/sel`.

/options o /t\
facoltativo. Visualizza l'elenco delle impostazioni correnti dell'opzione di ricerca e non esegue una ricerca.

/proc o /p\
facoltativo. Cerca solo nella routine corrente. Specificare solo uno degli ambiti di ricerca disponibili, `/doc`, `/proc`, `/open` o `/sel`.

/reset o /e\
facoltativo. Ripristina le impostazioni predefinite delle opzioni di ricerca e non esegue la ricerca.

/sel o /s\
facoltativo. Cerca solo nella selezione corrente. Specificare solo uno degli ambiti di ricerca disponibili, `/doc`, `/proc`, `/open` o `/sel`.

/up o /u\
facoltativo. Esegue la ricerca dalla posizione corrente nel file verso l'inizio del file. Per impostazione predefinita, le ricerche iniziano in corrispondenza della posizione nel file e procedono verso la fine del file.

/regex o /r\
facoltativo. Usa caratteri speciali predefiniti nell'argomento `findwhat` come notazioni che rappresentano modelli di testo anziché i caratteri letterali. Per l'elenco completo dei caratteri espressione regolare, vedere [Espressioni regolari](../../ide/using-regular-expressions-in-visual-studio.md).

/wild o /l\
facoltativo. Usa caratteri speciali predefiniti nell'argomento `findwhat` come notazioni per rappresentare un carattere o una sequenza di caratteri.

/word o /w\
facoltativo. Cerca solo parole intere.

## <a name="example"></a>Esempio
In questo esempio viene eseguita una ricerca con distinzione tra maiuscole e minuscole della parola "string" nella sezione di codice attualmente selezionata.

```cmd
>Edit.Find somestring /sel /case
```

## <a name="see-also"></a>Vedi anche

- [Finestra di comando](../../ide/reference/command-window.md)
- [Casella di ricerca/comando](../../ide/find-command-box.md)
- [Visual Studio Comandi](../../ide/reference/visual-studio-commands.md)
- [Visual Studio Alias dei comandi](../../ide/reference/visual-studio-command-aliases.md)
