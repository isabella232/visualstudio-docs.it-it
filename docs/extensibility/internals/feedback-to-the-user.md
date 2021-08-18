---
title: Commenti e suggerimenti per l'| Microsoft Docs
description: Informazioni su come fornire un feedback visivo all'utente sulle funzionalità disponibili nell Visual Studio di sviluppo integrato (IDE).
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
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: be19f6bb9b1879746542d73e67f6b77b0d28d792
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122102721"
---
# <a name="feedback-to-the-user"></a>Commenti e suggerimenti per l'utente
Nell'ambiente di sviluppo integrato (IDE) il feedback visivo relativo alle funzionalità disponibili si basa sulla selezione corrente dell'utente e sul contesto [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] di selezione globale. Nella tabella seguente sono elencate le funzionalità disponibili in contesti di selezione diversi.

|Contesto di selezione|Funzionalità disponibili|
|-----------------------|-----------------------------|
|IDE|Globale|
|Set di prodotti corrente|Specifico del prodotto|
|Gerarchia attiva|Specifico del tipo di gerarchia|
|Elemento della gerarchia attivo|Tipo di elemento gerarchia specifico|
|Documento attivo|Tipo di documento specifico|
|Finestra dell'interfaccia a documenti multipli (MDI) in primo piano|Tipo di finestra specifico|
|Contesto di selezione corrente|Specifico del contesto di selezione|

 Se si esercitono solo le funzionalità necessarie agli utenti e si forniscono continuamente una selezione coerente e un feedback del contesto dell'ambiente, si riduce la complessità nell'IDE. Le regole seguenti si applicano ogni volta che una finestra viene aperta nell'IDE:

- Se la finestra modifica il contesto di selezione, il feedback  sulla selezione è chiaramente indicato nella finestra e la finestra Guida dinamica, se visualizzata, viene aggiornata per riflettere il contesto corrente.

- Se la finestra cambia contesto di selezione globale, tutti i menu specifici del contesto, la finestra della gerarchia attiva e la barra del titolo dell'applicazione vengono aggiornati per riflettere il contesto corrente.

- La finestra deve visualizzare le proprietà per la selezione corrente **nella** finestra Proprietà e, facoltativamente, la finestra di **dialogo Pagine** delle proprietà.

- Se la finestra non esegue la superficie delle proprietà o modifica il contesto di selezione globale, il feedback sulla selezione non deve rimanere nella finestra quando non è più la finestra attiva nell'IDE.

- Tutte le finestre degli strumenti specifiche del documento devono riflettere continuamente il documento attivo.

- I menu, le barre degli strumenti e la barra del titolo dell'applicazione devono riflettere la finestra del client dell'interfaccia a documenti multipli (MDI) in primo piano.

  Ad esempio, quando viene aperta la visualizzazione HTML di un **Web Form** all'interno di un progetto applicazione Web Visual Basic e l'utente seleziona un tag, i commenti vengono forniti nel `<td>` modo seguente:

- La selezione è indicata nella finestra attiva e riflessa nella **finestra** Proprietà.

- La casella degli strumenti **specifica del** documento viene aggiornata per riflettere il documento attivo.

- Vengono **visualizzati la** barra degli **strumenti** Editor e il menu Tabella e la barra del titolo viene aggiornata per riflettere la finestra Web Form.

- La finestra della gerarchia attiva, in genere **Esplora soluzioni**, e la relativa barra del titolo vengono aggiornate per riflettere il contesto corrente e i comandi di menu di **Project** sensibili al contesto si applicano ora al progetto applicazione Web attivo.

## <a name="see-also"></a>Vedi anche
- [Selezione e valuta nell'IDE](../../extensibility/internals/selection-and-currency-in-the-ide.md)
- [Oggetti del contesto di selezione](../../extensibility/internals/selection-context-objects.md)
- [Gerarchie e selezione](../../extensibility/internals/hierarchies-and-selection.md)
