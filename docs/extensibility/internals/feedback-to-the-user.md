---
title: Commenti e suggerimenti per l'utente | Microsoft Docs
description: Informazioni su come fornire un feedback visivo all'utente sulle funzionalità disponibili in Visual Studio Integrated Development Environment (IDE).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- user model feedback
- environment, context
- IDE, context
- IDE, user feedback
ms.assetid: 2d472a24-3813-4f5f-9783-b491ad8a71ad
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 4d40ca34ea8d579e85ee56170f621b98a10b89f2
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105069634"
---
# <a name="feedback-to-the-user"></a>Commenti e suggerimenti per l'utente
Nel [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Integrated Development Environment (IDE), il feedback visivo relativo alla funzionalità disponibile si basa sulla selezione corrente dell'utente e sul contesto di selezione globale. Nella tabella seguente sono elencate le funzionalità disponibili in diversi contesti di selezione.

|Contesto di selezione|Funzionalità disponibili|
|-----------------------|-----------------------------|
|IDE|Globale|
|Set di prodotti corrente|Specifico del prodotto|
|Gerarchia attiva|Specifico del tipo di gerarchia|
|Elemento della gerarchia attiva|Specifico del tipo di elemento della gerarchia|
|Documento attivo|Specifico del tipo di documento|
|Finestra interfaccia a documenti multipli (MDI) in primo piano|Specifico del tipo di finestra|
|Contesto di selezione corrente|Specifico del contesto di selezione|

 Se si rilevano solo le funzionalità necessarie agli utenti e si forniscono continuamente Commenti coerenti per la selezione e il contesto dell'ambiente, è possibile ridurre la complessità nell'IDE. Le regole seguenti si applicano ogni volta che una finestra viene aperta nell'IDE:

- Se la finestra cambia il contesto di selezione, il feedback della selezione è chiaramente indicato nella finestra e la finestra **Guida dinamica** , se visualizzata, viene aggiornata per riflettere il contesto corrente.

- Se la finestra modifica il contesto di selezione globale, tutti i menu specifici del contesto, la finestra gerarchia attiva e la barra del titolo dell'applicazione vengono aggiornati per riflettere il contesto corrente.

- La finestra deve visualizzare le proprietà della selezione corrente nella finestra **Proprietà** e, facoltativamente, se visualizzata, la finestra di dialogo **pagine delle proprietà** .

- Se la finestra non è visibile o modifica il contesto di selezione globale, il feedback della selezione non deve rimanere nella finestra quando non è più la finestra attiva nell'IDE.

- Tutte le finestre degli strumenti specifiche del documento dovrebbero riflettere continuamente il documento attivo.

- I menu, le barre degli strumenti e la barra del titolo dell'applicazione devono riflettere la finestra del client di interfaccia a documenti multipli (MDI) più in alto.

  Ad esempio, quando viene aperta la visualizzazione HTML di un **Web Form** all'interno di un progetto di applicazione Web Visual Basic e l'utente seleziona un `<td>` tag, il feedback viene fornito nel modo seguente:

- La selezione è indicata nella finestra attiva e viene riflessa nella finestra **Proprietà** .

- La **casella degli strumenti** specifica del documento viene aggiornata per riflettere il documento attivo.

- Vengono visualizzati la barra degli strumenti dell' **Editor** e il menu **tabella** e la barra del titolo viene aggiornata per riflettere la finestra del modulo Web.

- La finestra gerarchia attiva, che in genere si **Esplora soluzioni**, e l'aggiornamento della relativa barra del titolo per riflettere il contesto corrente e i comandi di menu del **progetto** sensibili al contesto sono ora applicabili al progetto di applicazione Web attivo.

## <a name="see-also"></a>Vedi anche
- [Selezione e valuta nell'IDE](../../extensibility/internals/selection-and-currency-in-the-ide.md)
- [Oggetti contesto selezione](../../extensibility/internals/selection-context-objects.md)
- [Gerarchie e selezione](../../extensibility/internals/hierarchies-and-selection.md)
