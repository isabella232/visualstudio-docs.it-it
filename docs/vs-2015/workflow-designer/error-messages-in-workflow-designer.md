---
title: Messaggi di errore in Progettazione flussi di lavoro | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- WFDErrorMessages.UI
- System.Activities.Presentation.ErrorActivity.UI
- System.Activities.Presentation.View.ErrorView.UI
ms.assetid: 4d8bbc2e-34fc-477f-9140-4adfd70c34a0
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: d89c0dcad23a91ec6057311b9afde7d6d4702772
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "72656760"
---
# <a name="error-messages-in-workflow-designer"></a>Messaggi di errore in Progettazione flussi di lavoro
In questo argomento vengono descritti i tipi dei messaggi di errore che possono verificarsi durante l'uso di [!INCLUDE[wfd1](../includes/wfd1-md.md)].

## <a name="situations-in-which-errors-in-the-workflow-designer-occur"></a>Situazioni nelle quali si verificano gli errori in Progettazione flussi di lavoro
 Gli errori in [!INCLUDE[wfd2](../includes/wfd2-md.md)] si verificano nelle situazioni seguenti:

1. È presente un errore in un'espressione.

2. Non sono stati soddisfatti i vincoli di convalida di un'attività.

3. Sono presenti errori nel file XAML che impediscono il caricamento di un'attività.

4. Sono presenti errori nel file XAML che impediscono il caricamento del flusso di lavoro.

   Espressioni non valide e vincoli di convalida non possono impedire la compilazione del flusso di lavoro. La compilazione del flusso di lavoro infatti riesce, ma viene generato un oggetto <xref:System.Activities.InvalidWorkflowException> in fase di esecuzione. In presenza di errori nel file XAML, la compilazione non riesce.

   All'interno di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , quando viene caricato un flusso di lavoro, gli errori vengono visualizzati nel **Elenco errori**. Per passare all'attività che rappresenta l'origine dell'errore, fare doppio clic sull'errore nel **Elenco errori**.

### <a name="expression-errors"></a>Errori nelle espressioni
 Un'espressione non valida viene segnalata da un cerchio rosso con un punto esclamativo bianco accanto a essa. Se si posiziona il mouse su questa icona, viene visualizzata una descrizione comandi relativa all'origine dell'errore. In [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] fare clic sull'espressione per visualizzare la riga che sottolinea l'origine dell'errore. Se si posiziona il mouse sul testo sottolineato, viene visualizzata una descrizione comandi relativa all'origine dell'errore.

### <a name="activity-validation-errors"></a>Errori di convalida delle attività
 Una volta soddisfatti i vincoli di convalida di un'attività, viene visualizzato un cerchio rosso con un punto esclamativo bianco nell'angolo superiore destro dell'attività. Se si posiziona il mouse su questa icona, viene visualizzata una descrizione comandi relativa all'origine dell'errore.

### <a name="xaml-load-errors"></a>Errori di caricamento di XAML
 Quando non è possibile caricare un'attività, viene visualizzata una casella rossa contenente il testo "Impossibile caricare l'attività a causa di errori nell'XAML". Ciò si verifica in genere quando non è possibile risolvere il tipo dell'attività. L'attività non valida può essere eliminata nella finestra di progettazione selezionando ed eliminando la casella rossa.

### <a name="workflow-load-errors"></a>Errori di caricamento del flusso di lavoro
 Quando non è possibile caricare un flusso di lavoro, nell'area della finestra di progettazione viene visualizzato il testo "Progettazione flussi di lavoro ha riscontrato problemi con il documento", insieme alle informazioni sull'eccezione che ha causato l'errore di caricamento del flusso di lavoro. Ciò si verifica in genere quando non è possibile analizzare il file XAML.