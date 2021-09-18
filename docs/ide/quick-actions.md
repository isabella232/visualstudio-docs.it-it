---
title: Azioni rapide, lampadine e cacciavite
description: Informazioni su come usare una singola azione rapida per eseguire il refactoring, generare o modificare in altro modo il codice.
ms.custom: SEO-VS-2020
ms.date: 09/15/2021
ms.topic: conceptual
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: a5c11391c0874d1a57aa3d9a05b6d8e7e55463ae
ms.sourcegitcommit: 59613afd06a8f184efab8e108410066824a2b712
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/18/2021
ms.locfileid: "127920081"
---
# <a name="quick-actions"></a>Azioni rapide

Le azioni rapide consentono di generare codice, effettuarne il refactoring o modificarlo in altro modo con facilità tramite un'unica azione. Sono disponibili azioni rapide per C#, [C++](/cpp/ide/writing-and-refactoring-code-cpp) e i file di codice Visual Basic. Alcune azioni sono specifiche per un linguaggio e altre si applicano a tutti i linguaggi.

È possibile usare le azioni rapide per:

- Applicare una correzione del codice per una violazione [della regola dell'analizzatore](../code-quality/roslyn-analyzers-overview.md) del codice

::: moniker range=">=vs-2019"

- [Eliminare una](../code-quality/use-roslyn-analyzers.md#suppress-violations) violazione della regola dell'analizzatore del codice [o configurarne](../code-quality/use-roslyn-analyzers.md#set-rule-severity-from-the-light-bulb-menu) la gravità

::: moniker-end

::: moniker range="vs-2017"

- [Eliminare una violazione](../code-quality/use-roslyn-analyzers.md#suppress-violations) della regola dell'analizzatore del codice

::: moniker-end

- Applicare un refactoring (ad esempio, [inline una variabile temporanea](../ide/reference/inline-temporary-variable.md))

- Generare codice (ad esempio, [introdurre una variabile locale](../ide/reference/introduce-local-variable.md))

> [!NOTE]
> Questo argomento si applica a Visual Studio in Windows. Per Visual Studio per Mac, vedere [Refactoring (Visual Studio per Mac)](/visualstudio/mac/refactoring).

Le azioni rapide possono essere applicate usando l'icona lampadina lampadina o l'icona a forma di cacciavite a forma di cacciavite ![ ](media/light-bulb-icon.png) oppure premendo ![ ](media/screwdriver-icon.png)  + **CTRL.** quando il cursore si trova su una riga di codice per la quale è disponibile un'azione. Si noterà una lampadina di errore ![icona lampadina errore](media/error-light-bulb-icon.png) se è presente una sottolineatura ondulata rossa che indica un errore e in Visual Studio è disponibile una correzione per tale errore.

È possibile che fornitori terzi offrano diagnostiche e suggerimenti personalizzati per qualsiasi linguaggio, ad esempio includendoli in SDK: le lampadine di Visual Studio compariranno in base a tali regole.

## <a name="icons"></a>Icone

L'icona visualizzata quando è disponibile un'azione rapida indica il tipo di correzione o refactoring disponibile. *L'icona a* forma di cacciavite icona a forma di cacciavite indica solo che sono disponibili azioni per modificare il codice, ma non è ![ necessario ](media/screwdriver-icon.png) usarle necessariamente. *L'icona lampadina* gialla icona lampadina indica che sono disponibili azioni da ![ eseguire per migliorare il ](media/light-bulb-icon.png) codice.  *L'icona a forma di* lampadina di errore icona lampadina indica che è disponibile ![ un'azione che corregge ](media/error-light-bulb-icon.png) un errore nel codice.

## <a name="to-see-a-light-bulb-or-screwdriver"></a>Per visualizzare una lampadina o un cacciavite

Se è disponibile una correzione, le lampadine compaiono:

- Quando si passa il puntatore del mouse sulla posizione di un errore

   ![Lampadina con passaggio del puntatore del mouse](../ide/media/vs2015_lightbulb_hover.png)

- Nel margine sinistro dell'editor quando si sposta il punto di inserimento (cursore) sulla riga di codice applicabile

È anche possibile premere + **CTRL.** in un punto qualsiasi di una riga per visualizzare un elenco di azioni rapide e refactoring disponibili.

Per vedere le potenziali correzioni, selezionare la freccia GIÙ accanto alla lampadina o il collegamento **Mostra correzioni potenziali**. Viene visualizzato un elenco delle azioni rapide disponibili.

![Lampadina espansa](../ide/media/vs2015_lightbulb_hover_expanded.png)

## <a name="see-also"></a>Vedi anche

- [Visual Studio IntelliCode](/visualstudio/intellicode/intellicode-visual-studio)
- [Generazione di codice in Visual Studio](../ide/code-generation-in-visual-studio.md)
- [Azioni rapide comuni](../ide/common-quick-actions.md)
- [Stili di codice e azioni rapide](../ide/code-styles-and-code-cleanup.md)
- [Codice di scrittura e refactoring (C++)](/cpp/ide/writing-and-refactoring-code-cpp)
- [Refactoring (Visual Studio per Mac)](/visualstudio/mac/refactoring)
