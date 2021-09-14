---
title: Risposta alle modifiche e propagazione delle modifiche
description: Quando un elemento viene creato, eliminato o aggiornato, è possibile scrivere codice che propaga la modifica ad altre parti del modello o a risorse esterne.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, events
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.technology: vs-ide-modeling
ms.workload:
- multiple
ms.openlocfilehash: 8027b1fa5a2b050a0bb40160d44063857cc76927
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126637508"
---
# <a name="respond-to-and-propagate-changes"></a>Rispondere e propagare le modifiche

Quando un elemento viene creato, eliminato o aggiornato, è possibile scrivere codice che propaga la modifica ad altre parti del modello o a risorse esterne, ad esempio file, database o altri componenti.

## <a name="reference"></a>Riferimento

Come linea guida, prendere in considerazione queste tecniche nell'ordine seguente:

|Tecnica|Scenari|Per ulteriori informazioni|
|-|-|-|
|Definire una proprietà di dominio Calcolata.|Proprietà di dominio il cui valore viene calcolato da altre proprietà nel modello. Ad esempio, un prezzo che rappresenta la somma dei prezzi degli elementi correlati.|[Proprietà di archiviazione calcolate e personalizzate](../modeling/calculated-and-custom-storage-properties.md)|
|Definire una proprietà Archiviazione dominio personalizzato.|Proprietà di dominio archiviata in altre parti del modello o esternamente. Ad esempio, è possibile analizzare una stringa di espressione in un albero del modello.|[Proprietà di archiviazione calcolate e personalizzate](../modeling/calculated-and-custom-storage-properties.md)|
|Eseguire l'override di gestori di modifiche come OnValueChanging e OnDeleting|Mantenere sincronizzati elementi diversi e mantenere i valori esterni sincronizzati con il modello.<br /><br /> Vincola i valori agli intervalli definiti.<br /><br /> Chiamato immediatamente prima e dopo il valore della proprietà e altre modifiche. È possibile terminare la modifica generando un'eccezione.|[Gestori di modifica del valore delle proprietà del dominio](../modeling/domain-property-value-change-handlers.md)|
|Regole|È possibile definire regole che vengono accodati per l'esecuzione subito prima della fine di una transazione in cui si è verificata una modifica. Non vengono eseguiti in caso di annullamento o di annullamento. Usarli per mantenere sincronizzata una parte dell'archivio con un'altra.|[Le regole propagano le modifiche all'interno del modello](../modeling/rules-propagate-changes-within-the-model.md)|
|Archiviare eventi|L'archivio di modellazione fornisce notifiche di eventi, ad esempio l'aggiunta o l'eliminazione di un elemento o di un collegamento o la modifica del valore di una proprietà. L'evento viene eseguito anche in caso di annullamento e di annullamento. Usare gli eventi dell'archivio per aggiornare i valori non presenti nell'archivio.|[I gestori eventi propagano le modifiche al di fuori del modello](../modeling/event-handlers-propagate-changes-outside-the-model.md)|
|Eventi .NET|Le forme hanno gestori eventi che rispondono ai clic del mouse e ad altri movimenti. È necessario registrarsi per questi eventi per ogni oggetto. La registrazione viene in genere eseguita in un override di InitializeInstanceResources e deve essere eseguita per ogni elemento.<br /><br /> Questi eventi si verificano in genere all'esterno di una transazione.|[Procedura: Intercettare un clic su una forma o su un elemento Decorator](../modeling/how-to-intercept-a-click-on-a-shape-or-decorator.md)|
|Regole relative ai limiti|Una regola dei limiti viene usata in modo specifico per vincolare i limiti di una forma.|[Le regole associate (BoundsRules) vincolano posizione e dimensione delle forme](/previous-versions/visualstudio/visual-studio-2015/modeling/boundsrules-constrain-shape-location-and-size?preserve-view=true&view=vs-2015)|
|Regole di selezione|Le regole di selezione vincolano in modo specifico ciò che l'utente può selezionare.|[Procedura: Accedere e vincolare la selezione corrente](../modeling/how-to-access-and-constrain-the-current-selection.md)|
|OnAssocatedPropertyChanged|Indicare gli stati degli elementi del modello usando caratteristiche di forme e connettori, ad esempio ombreggiatura, frecce, colore, larghezza e stile delle linee.|[Aggiornamento di forme e di connettori per riflettere il modello](../modeling/updating-shapes-and-connectors-to-reflect-the-model.md)|

## <a name="compare-rules-and-store-events"></a>Confrontare regole e archiviare eventi

I notificatori di modifica, le regole e gli eventi vengono eseguiti quando si verificano modifiche in un modello.

Le regole vengono in genere applicate alla transazione finale in cui si è verificata la modifica e gli eventi vengono applicati dopo il commit delle modifiche in una transazione.

Usare gli eventi dell'archivio per sincronizzare il modello con gli oggetti esterni all'archivio e le regole per mantenere la coerenza all'interno dell'archivio.

- **Creazione di regole personalizzate** Si crea una regola personalizzata come classe derivata da una regola astratta. È inoltre necessario notificare al framework la regola personalizzata. Per altre informazioni, vedere [Regole di propagazione delle modifiche all'interno del modello.](../modeling/rules-propagate-changes-within-the-model.md)

- **Sottoscrizione di eventi** Prima di poter sottoscrivere un evento, creare un gestore eventi e un delegato. Usare quindi la <xref:Microsoft.VisualStudio.Modeling.Store.EventManagerDirectory%2A> proprietà per sottoscrivere l'evento . Per altre informazioni, vedere [Propagare modifiche all'esterno del modello da parte dei gestori eventi.](../modeling/event-handlers-propagate-changes-outside-the-model.md)

- **Annullamento delle modifiche** Quando si annulla una transazione, vengono generati eventi, ma le regole non vengono applicate. Se una regola modifica un valore e si annulla tale modifica, il valore viene reimpostato sul valore originale durante l'azione di annullamento. Quando viene generato un evento, è necessario modificare manualmente il valore nel valore originale. Per altre informazioni sulle transazioni e sull'annullamento, [vedere Procedura: Usare le transazioni per aggiornare il modello.](../modeling/how-to-use-transactions-to-update-the-model.md)

- **Passaggio di argomenti di evento a regole ed eventi** Sia agli eventi che alle regole viene passato `EventArgs` un parametro che contiene informazioni sulla modalità di modifica del modello.

## <a name="see-also"></a>Vedi anche

- [Procedura: Intercettare un clic su una forma o su un elemento Decorator](../modeling/how-to-intercept-a-click-on-a-shape-or-decorator.md)
- [Scrittura di codice per personalizzare un linguaggio Domain-Specific personalizzato](../modeling/writing-code-to-customise-a-domain-specific-language.md)