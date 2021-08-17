---
title: Commenti e suggerimenti per l'| Microsoft Docs
description: Informazioni su come fornire un feedback visivo all'utente sulle funzionalità disponibili nell'ambiente Visual Studio di sviluppo integrato (IDE).
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
ms.openlocfilehash: 1b4794dcf4293b340390695afa02bb49e552ada8918e9a3184c74f16b987432e
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121388734"
---
# <a name="feedback-to-the-user"></a>Commenti e suggerimenti per l'utente
Nell'ambiente di sviluppo integrato (IDE), il feedback visivo relativo alle funzionalità disponibili si basa sulla selezione corrente dell'utente e sul [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] contesto di selezione globale. Nella tabella seguente sono elencate le funzionalità disponibili in contesti di selezione diversi.

|Contesto di selezione|Funzionalità disponibili|
|-----------------------|-----------------------------|
|IDE|Globale|
|Set di prodotti corrente|Specifico del prodotto|
|Gerarchia attiva|Tipo di gerarchia specifico|
|Elemento della gerarchia attivo|Tipo di elemento della gerarchia specifico|
|Documento attivo|Tipo di documento specifico|
|Finestra MDI (Multiple Document Interface) in primo piano|Tipo di finestra specifico|
|Contesto di selezione corrente|Specifico del contesto di selezione|

 Se si eserciteranno solo le funzionalità necessarie agli utenti e si forniranno continuamente feedback coerenti sulla selezione e sul contesto dell'ambiente, si riduce la complessità nell'IDE. Le regole seguenti si applicano ogni volta che viene aperta una finestra nell'IDE:

- Se la finestra cambia il contesto di selezione, il feedback sulla selezione viene indicato chiaramente nella finestra e la **finestra** Guida dinamica, se visualizzata, viene aggiornata per riflettere il contesto corrente.

- Se la finestra cambia contesto di selezione globale, tutti i menu specifici del contesto, la finestra della gerarchia attiva e la barra del titolo dell'applicazione vengono aggiornati per riflettere il contesto corrente.

- La finestra deve visualizzare le proprietà per la selezione corrente **nella** finestra Proprietà e, facoltativamente, la finestra di dialogo **Pagine** delle proprietà.

- Se la finestra non esercite le proprietà o modifica il contesto di selezione globale, i commenti e suggerimenti sulla selezione non devono rimanere nella finestra quando non è più la finestra attiva nell'IDE.

- Tutte le finestre degli strumenti specifiche del documento devono riflettere continuamente il documento attivo.

- I menu, le barre degli strumenti e la barra del titolo dell'applicazione devono riflettere la finestra client MDI (Multiple Document Interface) più in alto.

  Ad esempio, quando viene aperta la visualizzazione HTML di un **Web Form** all'interno di un progetto applicazione Web Visual Basic e l'utente seleziona un tag, vengono forniti commenti e suggerimenti nel `<td>` modo seguente:

- La selezione viene indicata nella finestra attiva e riflessa nella **finestra** Proprietà.

- La casella degli strumenti specifica **del** documento viene aggiornata per riflettere il documento attivo.

- Vengono **visualizzati la barra** degli **strumenti** Editor e il menu Tabella e la barra del titolo viene aggiornata per riflettere la finestra Web Form.

- La finestra della gerarchia attiva, in genere **Esplora soluzioni**, e la relativa barra del titolo vengono aggiornate in modo da riflettere il contesto corrente e i comandi di menu Project sensibili **al** contesto si applicano ora al progetto applicazione Web attivo.

## <a name="see-also"></a>Vedi anche
- [Selezione e valuta nell'IDE](../../extensibility/internals/selection-and-currency-in-the-ide.md)
- [Oggetti del contesto di selezione](../../extensibility/internals/selection-context-objects.md)
- [Gerarchie e selezione](../../extensibility/internals/hierarchies-and-selection.md)
