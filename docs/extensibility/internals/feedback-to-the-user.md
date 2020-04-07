---
title: Feedback all'utente Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- user model feedback
- environment, context
- IDE, context
- IDE, user feedback
ms.assetid: 2d472a24-3813-4f5f-9783-b491ad8a71ad
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 46b9190b16b9aa444384847bf209ccca50c7f768
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708405"
---
# <a name="feedback-to-the-user"></a>Feedback all'utente
Nell'ambiente di sviluppo integrato (IDE), il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] feedback visivo relativo alle funzionalità disponibili si basa sulla selezione corrente dell'utente e sul contesto di selezione globale. Nella tabella seguente sono elencate le funzionalità disponibili in diversi contesti di selezione.

|Contesto di selezione|Funzionalità disponibili|
|-----------------------|-----------------------------|
|IDE|Global|
|Set di prodotti corrente|Specifico del prodotto|
|Gerarchia attiva|Tipo di gerarchia specifico|
|Elemento gerarchia attiva|Tipo di elemento della gerarchia specifico|
|Documento attivo|Specifico del tipo di documento|
|Finestra interfaccia a documenti multipli (MDI) in primo piano|Specifico del tipo di finestra|
|Contesto di selezione corrente|Contesto di selezione specifico|

 Se si estrae solo la funzionalità di cui gli utenti hanno bisogno e si forniscono continuamente un feedback coerente sul contesto dell'ambiente e sulla selezione, si riduce la complessità dell'IDE. Le regole seguenti si applicano ogni volta che viene aperta una finestra nell'IDE:

- Se la finestra cambia il contesto di selezione, il feedback della selezione viene indicato chiaramente nella finestra e la finestra **Guida dinamica,** se visualizzata, viene aggiornata per riflettere il contesto corrente.

- Se la finestra cambia il contesto di selezione globale, tutti i menu specifici del contesto, la finestra della gerarchia attiva e la barra del titolo dell'applicazione vengono aggiornati per riflettere il contesto corrente.

- La finestra deve esporre le proprietà per la selezione corrente nel **proprietà** finestra e, facoltativamente, se illustrato, il **pagine delle proprietà** finestra di dialogo.

- Se la finestra non superficie proprietà o modificare il contesto di selezione globale, feedback di selezione non deve rimanere nella finestra quando non è più la finestra attiva nell'IDE.

- Tutte le finestre degli strumenti specifiche del documento devono riflettere continuamente il documento attivo.

- Menu, barre degli strumenti e la barra del titolo dell'applicazione devono riflettere la finestra client di interfaccia a documenti multipli (MDI) in primo piano.

  Ad esempio, quando viene aperta la visualizzazione HTML di un **Web Form** all'interno di un progetto di applicazione Web di Visual Basic e l'utente seleziona un `<td>` tag, viene fornito un feedback nel modo seguente:

- La selezione viene indicata nella finestra attiva e riflessa nella finestra **Proprietà.**

- La casella **degli strumenti** specifica del documento viene aggiornata per riflettere il documento attivo.

- Vengono visualizzati la barra degli strumenti **Editor** e il menu **Tabella** e la barra del titolo viene aggiornata per riflettere la finestra del Web Form.

- La finestra della gerarchia attiva, che in genere è **Esplora soluzioni,** e la relativa barra del titolo vengono aggiornati per riflettere il contesto corrente e i comandi del menu **Progetto** sensibili al contesto ora si applicano al progetto di applicazione Web attivo.

## <a name="see-also"></a>Vedere anche
- [Selezione e valuta nell'IDE](../../extensibility/internals/selection-and-currency-in-the-ide.md)
- [Oggetti di contesto di selezione](../../extensibility/internals/selection-context-objects.md)
- [Gerarchie e selezione](../../extensibility/internals/hierarchies-and-selection.md)
