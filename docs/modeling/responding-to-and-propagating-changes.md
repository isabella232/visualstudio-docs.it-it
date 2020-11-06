---
title: Risposta alle modifiche e propagazione delle modifiche
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, events
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7c51aeea4a1637e5b1b9d2de0d8b92920334e2fc
ms.sourcegitcommit: ba966327498a0f67d2df2291c60b62312f40d1d3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/06/2020
ms.locfileid: "93414516"
---
# <a name="respond-to-and-propagate-changes"></a>Risposta e propagazione delle modifiche

Quando viene creato, eliminato o aggiornato un elemento, è possibile scrivere codice che propaga la modifica ad altre parti del modello o a risorse esterne, ad esempio file, database o altri componenti.

## <a name="reference"></a>Informazioni di riferimento

Come linea guida, prendere in considerazione queste tecniche nell'ordine seguente:

|Tecnica|Scenari|Per ulteriori informazioni|
|-|-|-|
|Definire una proprietà del dominio calcolato.|Proprietà di dominio il cui valore viene calcolato da altre proprietà nel modello. Ad esempio, un prezzo che corrisponde alla somma dei prezzi degli elementi correlati.|[Proprietà di archiviazione calcolate e personalizzate](../modeling/calculated-and-custom-storage-properties.md)|
|Definire una proprietà del dominio di archiviazione personalizzato.|Proprietà di dominio archiviata in altre parti del modello o esternamente. Ad esempio, è possibile analizzare una stringa di espressione in un albero del modello.|[Proprietà di archiviazione calcolate e personalizzate](../modeling/calculated-and-custom-storage-properties.md)|
|Eseguire l'override di gestori di modifiche, ad esempio OnValueChanging e ondeletion|Mantieni diversi elementi sincronizzati e Mantieni sincronizzati i valori esterni con il modello.<br /><br /> Vincolare i valori agli intervalli definiti.<br /><br /> Chiamato immediatamente prima e dopo il valore della proprietà e altre modifiche. È possibile terminare la modifica generando un'eccezione.|[Gestori di modifica del valore delle proprietà del dominio](../modeling/domain-property-value-change-handlers.md)|
|Regole|È possibile definire regole accodate per l'esecuzione immediatamente prima della fine di una transazione in cui si è verificata una modifica. Non vengono eseguite in caso di annullamento o ripetizione. Utilizzarli per tenere una parte dell'archivio sincronizzata con un'altra.|[Le regole propagano le modifiche all'interno del modello](../modeling/rules-propagate-changes-within-the-model.md)|
|Archivia eventi|L'archivio di modellazione fornisce notifiche di eventi quali l'aggiunta o l'eliminazione di un elemento o un collegamento o la modifica del valore di una proprietà. L'evento viene inoltre eseguito in fase di annullamento e ripristino. Utilizzare gli eventi di archiviazione per aggiornare i valori non inclusi nell'archivio.|[I gestori eventi propagano le modifiche al di fuori del modello](../modeling/event-handlers-propagate-changes-outside-the-model.md)|
|Eventi .NET|Le forme hanno gestori eventi che rispondono ai clic del mouse e ad altri movimenti. È necessario registrarsi per questi eventi per ogni oggetto. La registrazione viene in genere eseguita in un override di InitializeInstanceResources e deve essere eseguita per ogni elemento.<br /><br /> Questi eventi si verificano in genere all'esterno di una transazione.|[Procedura: Intercettare un clic su una forma o su un elemento Decorator](../modeling/how-to-intercept-a-click-on-a-shape-or-decorator.md)|
|Regole dei limiti|Una regola dei limiti viene utilizzata in modo specifico per vincolare i limiti di una forma.|[Le regole associate (BoundsRules) vincolano posizione e dimensione delle forme](/previous-versions/visualstudio/visual-studio-2015/modeling/boundsrules-constrain-shape-location-and-size?preserve-view=true&view=vs-2015)|
|Regole di selezione|Le regole di selezione vincolano in modo specifico ciò che l'utente può selezionare.|[Procedura: Accedere e vincolare la selezione corrente](../modeling/how-to-access-and-constrain-the-current-selection.md)|
|OnAssocatedPropertyChanged|Indicare gli Stati degli elementi del modello usando le funzionalità di forme e connettori, ad esempio ombreggiatura, frecce, colore e spessore di linea e stile.|[Aggiornamento di forme e di connettori per riflettere il modello](../modeling/updating-shapes-and-connectors-to-reflect-the-model.md)|

## <a name="compare-rules-and-store-events"></a>Confrontare le regole e archiviare gli eventi

I notificatori, le regole e gli eventi di modifica vengono eseguiti quando si verificano modifiche in un modello.

Le regole vengono in genere applicate alla transazione finale in cui si è verificata la modifica e vengono applicati gli eventi dopo il commit delle modifiche in una transazione.

Utilizzare gli eventi di archiviazione per sincronizzare il modello con gli oggetti all'esterno dell'archivio e le regole per mantenere la coerenza all'interno dell'archivio.

- **Creazione di regole personalizzate** Si crea una regola personalizzata come classe derivata da una regola astratta. È inoltre necessario inviare una notifica al Framework sulla regola personalizzata. Per ulteriori informazioni, vedere la pagina relativa alla [propagazione delle modifiche all'interno del modello](../modeling/rules-propagate-changes-within-the-model.md).

- **Sottoscrizione di eventi** Prima di poter sottoscrivere un evento, creare un gestore eventi e un delegato. Usare quindi la <xref:Microsoft.VisualStudio.Modeling.Store.EventManagerDirectory%2A> proprietà per sottoscrivere l'evento. Per ulteriori informazioni, vedere [i gestori eventi propagano le modifiche al di fuori del modello](../modeling/event-handlers-propagate-changes-outside-the-model.md).

- **Anmutazione delle modifiche** Quando si annulla una transazione, vengono generati gli eventi, ma le regole non vengono applicate. Se una regola modifica un valore e si annulla tale modifica, il valore viene reimpostato sul valore originale durante l'operazione di annullamento. Quando viene generato un evento, è necessario modificare manualmente il valore con il valore originale. Per ulteriori informazioni sulle transazioni e sull'annullamento, vedere [procedura: utilizzare le transazioni per aggiornare il modello](../modeling/how-to-use-transactions-to-update-the-model.md).

- **Passaggio di argomenti di evento a regole ed eventi** A entrambi gli eventi e le regole viene passato un `EventArgs` parametro con informazioni sul modo in cui il modello è stato modificato.

## <a name="see-also"></a>Vedere anche

- [Procedura: Intercettare un clic su una forma o su un elemento Decorator](../modeling/how-to-intercept-a-click-on-a-shape-or-decorator.md)
- [Scrittura di codice per personalizzare un linguaggio Domain-Specific](../modeling/writing-code-to-customise-a-domain-specific-language.md)