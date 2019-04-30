---
title: XMLNodes (controllo)
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- XMLNodes control, events
- XMLNodes control
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 9ad16165924a33a25dab2b1cfb49a0a7bbfe0875
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63421540"
---
# <a name="xmlnodes-control"></a>XMLNodes (controllo)
  **Importante** le informazioni definite in questo argomento relative a Microsoft Word sono presentati in modo esclusivo per il vantaggio e uso di singoli utenti e le organizzazioni che si trovano di fuori degli Stati Uniti e dei relativi territori o che usano o lo sviluppo i programmi eseguiti su, i prodotti di Microsoft Word che sono stati concessi in licenza da Microsoft prima di gennaio del 2010 quando Microsoft ha rimosso un'implementazione di una funzionalità specifica correlato a XML personalizzata da Microsoft Word. Queste informazioni relative a Microsoft Word non possono essere lette o utilizzate dagli singoli individui o organizzazioni negli Stati Uniti o relativo territori che usano o lo sviluppo di programmi in esecuzione in, i prodotti di Microsoft Word che sono stati concessi in licenza da Microsoft dopo il 10 gennaio 2010 ; tali prodotti non si comporterà come prodotti concessi in licenza prima di tale data o acquistati e concesso in licenza per l'utilizzo di fuori degli Stati Uniti.

 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]

 Il <xref:Microsoft.Office.Tools.Word.XMLNodes> controllo è una raccolta di oggetti con mapping del nodo XML che espone gli eventi. Il <xref:Microsoft.Office.Tools.Word.XMLNodes> controllo viene creato solo quando un elemento ripetuto dello schema viene mappato a un documento di Microsoft Office Word. Se l'elemento ripetuto contiene gli elementi figlio, ognuno degli elementi figlio viene creato come un <xref:Microsoft.Office.Tools.Word.XMLNodes> controllo.

 Dopo che Visual Studio ha creato la raccolta di nodi XML, è possibile programmare il controllo direttamente senza dover passare attraverso il modello a oggetti Word. Il <xref:Microsoft.Office.Tools.Word.XMLNodes> controllo può essere eliminato solo eliminando il mapping dell'elemento dal documento.

> [!NOTE]
> Se si accede a un elemento figlio del <xref:Microsoft.Office.Tools.Word.XMLNodes> controllare tramite il <xref:Microsoft.Office.Tools.Word.XMLNodes.Item%2A> proprietà, viene restituito un <xref:Microsoft.Office.Interop.Word.XMLNode> oggetto anziché un <xref:Microsoft.Office.Tools.Word.XMLNode> controllo. Per altre informazioni, vedere [limitazioni a livello di codice degli elementi host e controlli host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md).

## <a name="bind-data-to-the-control"></a>Associare dati al controllo
 Un <xref:Microsoft.Office.Tools.Word.XMLNodes> controllo supporta il data binding. Infatti il <xref:Microsoft.Office.Tools.Word.XMLNodes> controllo non dispone di funzionalità di associazione di dati complessi, e il data binding semplice non può rappresentare dati ripetuti.

## <a name="formatting"></a>Formattazione
 Qualsiasi formattazione che può essere applicato al testo all'interno del documento può essere applicata a un <xref:Microsoft.Office.Tools.Word.XMLNodes> controllo.

## <a name="events"></a>Eventi
 Gli eventi disponibili per il <xref:Microsoft.Office.Tools.Word.XMLNodes> controllo sono:

- <xref:Microsoft.Office.Tools.Word.XMLNodes.AfterInsert>

- <xref:Microsoft.Office.Tools.Word.XMLNodes.BeforeDelete>

- <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextEnter>

- <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextLeave>

- <xref:Microsoft.Office.Tools.Word.XMLNodes.Deselect>

- <xref:System.ComponentModel.IComponent.Disposed>

- <xref:Microsoft.Office.Tools.Word.XMLNodes.Select>

- <xref:Microsoft.Office.Tools.Word.XMLNodes.ValidationError>

## <a name="compare-events"></a>Confrontare gli eventi
 È possibile acquisire un evento quando l'utente sposta il cursore all'interno del contesto di un determinato <xref:Microsoft.Office.Tools.Word.XMLNodes> controllo. Ad esempio, potrebbe essere un' <xref:Microsoft.Office.Tools.Word.XMLNodes> controllo denominato `Customer` che ha un figlio <xref:Microsoft.Office.Tools.Word.XMLNodes> controllo denominato `Company`, e `Company` ha due figlio <xref:Microsoft.Office.Tools.Word.XMLNodes> controlli denominati `CompanyName` e `CompanyRegion` come indicato di seguito:

```xml
<Customer>
    <Company>
        <CompanyName>
        <CompanyRegion>
```

 Se si desidera visualizzare un controllo nel riquadro azioni ogni volta che il cursore viene spostato nel `Company` nodo, non è importante se il cursore viene posizionato `CompanyName` oppure `CompanyRegion` perché sono entrambe all'interno del contesto di `Company`. In questo caso, è possibile scrivere il codice <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextEnter> eventi di `Company`.

 Nella maggior parte dei casi, quando il cursore viene spostato un <xref:Microsoft.Office.Tools.Word.XMLNodes> controllare, entrambe le <xref:Microsoft.Office.Tools.Word.XMLNodes.Select> e <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextEnter> gli eventi vengono generati. La tabella seguente illustra le differenze tra questi eventi.

|Seleziona evento|Evento ContextEnter|
|------------------|------------------------|
|Si verifica quando il cursore viene posizionato all'interno di uno dei nodi del <xref:Microsoft.Office.Tools.Word.XMLNodes> raccolta.|Si verifica quando il cursore viene posizionato all'interno di uno dei nodi o dei relativi nodi discendenti del <xref:Microsoft.Office.Tools.Word.XMLNodes> insieme, da un'area all'esterno del contesto del nodo. In altre parole, viene generato solo quando il contesto di modifica e possono essere generati per più annidati <xref:Microsoft.Office.Tools.Word.XMLNodes> controlli.|

 Ad esempio, quando si sposta il cursore da fuori `Customer` in `CompanyName`, il <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextEnter> eventi per `Customer`, `Company`, e `CompanyName` vengono generati. Se poi si sposta il cursore a partire dal `CompanyName` al `CompanyRegion`, il <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextEnter> eventi solo per `CompanyRegion` viene generato, perché il contesto è lo stesso per entrambi `Company` e `Customer`. È possibile avere più `Company` nodi presenti nel documento. Se si sposta il cursore dal `CompanyName` nodo di uno `Company` per il `CompanyName` nodo di un altro `Company`, il contesto è lo stesso, in modo che solo il <xref:Microsoft.Office.Tools.Word.XMLNodes.Select> viene generato l'evento.

 Le stesse differenze esistono tra i <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextLeave> eventi e <xref:Microsoft.Office.Tools.Word.XMLNodes.Deselect> evento.

## <a name="see-also"></a>Vedere anche
- [Cenni preliminari sui controlli host e gli elementi host](../vsto/host-items-and-host-controls-overview.md)
- [Automazione di Word usando oggetti estesi](../vsto/automating-word-by-using-extended-objects.md)
- [Controllo XMLNode](../vsto/xmlnode-control.md)
- [Procedura: Aggiungere controlli XMLNodes ai documenti di Word](../vsto/how-to-add-xmlnodes-controls-to-word-documents.md)
- [Procedura: Mappare schemi a documenti di Word in Visual Studio](../vsto/how-to-map-schemas-to-word-documents-inside-visual-studio.md)
- [Limitazioni a livello di codice degli elementi host e controlli host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
