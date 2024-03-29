---
title: Messaggi di errore in Progettazione flussi di lavoro
description: Informazioni sui tipi di messaggi di errore che è possibile riscontrare quando si lavora con Progettazione flussi di lavoro.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- WFDErrorMessages.UI
- System.Activities.Presentation.ErrorActivity.UI
- System.Activities.Presentation.View.ErrorView.UI
ms.assetid: 4d8bbc2e-34fc-477f-9140-4adfd70c34a0
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-workflow-designer
ms.workload:
- multiple
ms.openlocfilehash: 63cdfa5e371f67db2faffa7b18c0eacf4e2db411
ms.sourcegitcommit: 0841d3f610bd2af4af1cf07dd9d31d1e0629b193
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/09/2021
ms.locfileid: "123963440"
---
# <a name="error-messages-in-workflow-designer"></a>Messaggi di errore in Progettazione flussi di lavoro

In questo argomento vengono descritti i tipi di messaggi di errore che possono essere rilevati quando si lavora con Progettazione flussi di lavoro.

## <a name="situations-in-which-errors-in-the-workflow-designer-occur"></a>Situazioni nelle quali si verificano gli errori in Progettazione flussi di lavoro

Gli errori Progettazione flussi di lavoro si verificano nelle situazioni seguenti:

1. È presente un errore in un'espressione.

2. Non sono stati soddisfatti i vincoli di convalida di un'attività.

3. Sono presenti errori nel file XAML che impediscono il caricamento di un'attività.

4. Sono presenti errori nel file XAML che impediscono il caricamento del flusso di lavoro.

Espressioni non valide e vincoli di convalida non possono impedire la compilazione del flusso di lavoro. La compilazione del flusso di lavoro ha esito positivo, <xref:System.Activities.InvalidWorkflowException> ma viene generata un'eccezione in fase di esecuzione. In presenza di errori nel file XAML, la compilazione non riesce.

All Visual Studio, quando viene caricato un flusso di lavoro, i relativi errori vengono visualizzati in **Elenco errori**. Per passare all'attività che rappresenta l'origine dell'errore, fare doppio clic sull'errore in **Elenco errori**.

### <a name="expression-errors"></a>Errori nelle espressioni
 Un'espressione non valida viene segnalata da un cerchio rosso con un punto esclamativo bianco accanto a essa. Se si posiziona il mouse su questa icona, viene visualizzata una descrizione comandi relativa all'origine dell'errore. In Visual Studio fare clic sull'espressione per visualizzare la riga che sottolinea l'origine dell'errore. Se si posiziona il mouse sul testo sottolineato, viene visualizzata una descrizione comandi relativa all'origine dell'errore.

### <a name="activity-validation-errors"></a>Errori di convalida delle attività
 Una volta soddisfatti i vincoli di convalida di un'attività, viene visualizzato un cerchio rosso con un punto esclamativo bianco nell'angolo superiore destro dell'attività. Se si posiziona il mouse su questa icona, viene visualizzata una descrizione comandi relativa all'origine dell'errore.

### <a name="xaml-load-errors"></a>Errori di caricamento di XAML
 Quando un'attività non viene caricata, viene visualizzata una casella rossa con il testo "Impossibile caricare l'attività a causa di errori nel codice XAML". Ciò si verifica in genere quando il tipo dell'attività non può essere risolto. L'attività non valida può essere eliminata nella finestra di progettazione selezionando ed eliminando la casella rossa.

### <a name="workflow-load-errors"></a>Errori di caricamento del flusso di lavoro
 Quando un flusso di lavoro non viene caricato, nell'area di progettazione viene visualizzato il testo "Progettazione flussi di lavoro encountered problems with your document" (Si sono verificati problemi con il documento), insieme alle informazioni sull'eccezione che hanno causato l'errore di caricamento del flusso di lavoro. Ciò si verifica in genere quando non è possibile analizzare il file XAML.
