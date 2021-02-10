---
title: IntelliSense per codice R
description: Visual Studio IntelliSense visualizza informazioni sulle funzioni, i membri dell'oggetto, frammenti di codice e i completamenti durante la digitazione di codice R.
ms.date: 01/24/2018
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: jmartens
ms.workload:
- data-science
ms.openlocfilehash: de6a8ffbaa0fb10929d013a351ebffa8e3f4b529
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99939435"
---
# <a name="intellisense"></a>IntelliSense

Visual Studio IntelliSense visualizza informazioni sulle funzioni che è possibile chiamare, sui membri di oggetti, sugli argomenti della funzione e sui [frammenti di codice](code-snippets-for-r.md) direttamente durante la scrittura del codice. Visualizza anche i possibili completamenti durante la digitazione e viene completata quando si preme la **scheda** o si **immettono** i tasti (vedere le [Opzioni dell'editor](editing-r-code-in-visual-studio.md#editor-options) per la scheda **Avanzate** ). Intellisense è disponibile sia nell'editor che nella[ finestra interattiva](interactive-repl-for-r-in-visual-studio.md).

![Visualizzazione di una firma della funzione di IntelliSense](media/intellisense-function-signature.png)

Durante la digitazione di una funzione o di un'altra istruzione, IntelliSense offre menu di completamento automatico (con distinzione tra maiuscole e minuscole) filtrato in base ai valori che sono già stati immessi:

![Menu di completamento automatico di IntelliSense](media/intellisense-auto-complete-menu.png)

Premendo **Tab** (o **invio** o **spazio**, a seconda della modalità di impostazione delle opzioni), inserisce l'elemento selezionato nell'elenco a discesa. È possibile modificare la selezione con i tasti di direzione.

IntelliSense offre anche suggerimenti per i membri di oggetti R:

![Suggerimenti di IntelliSense per i membri di un oggetto](media/intellisense-auto-complete-r-objects.png)

Se si preme **ESC** , il menu viene eliminato completamente. È possibile riportare il backup con + **lo spazio** CTRL.

Se si digita il segno di `(` aperta per una chiamata di funzione viene inserito il segno di `)` chiusa e viene ripristinato il supporto per la firma come illustrato in precedenza:

![Supporto per la firma per una funzione di IntelliSense](media/intellisense-function-signature.png)

Anche in questo caso, **ESC Annulla** il popup; per le firme delle funzioni, è possibile riportarle con +  + **lo spazio** CTRL.

> [!Tip]
> Se il parametro consente di nascondere il testo sottostante, tenere premuto il tasto **CTRL** per rendere il testo della guida del parametro trasparente.

## <a name="intellisense-for-user-defined-functions-and-variables"></a>IntelliSense per variabili e funzioni definite dall'utente

IntelliSense viene applicato anche per il completamento del parametro "name" di funzioni definite dall'utente nello stesso file:

![IntelliSense per funzioni definite dall'utente](media/intellisense-same-file-functions.png)

![Completamento parametri di IntelliSense per funzioni definite dall'utente](media/intellisense-parameter-completion.png)

IntelliSense viene applicato anche a variabili nello stesso file e nella sessione corrente:

![Completamento variabili di IntelliSense](media/intellisense-variable-completion.png)

> [!Note]
> Nella finestra interattiva IntelliSense prende in considerazione solo i nomi nella sessione corrente di R e ignora i file nel progetto.

## <a name="code-suggestions"></a>Suggerimenti di codice

Quando al margine viene visualizzata una lampadina, detta smart tag, significa che Visual Studio sta suggerendo un collegamento per una delle azioni più usate. Ad esempio, passare il puntatore su una riga che contiene un'istruzione `library` nell'editor per visualizzare una lampadina. Selezionando la lampadina, verranno visualizzate le opzioni disponibili:

![Smart tag per R nell'editor](media/intellisense-smart-tags.png)
