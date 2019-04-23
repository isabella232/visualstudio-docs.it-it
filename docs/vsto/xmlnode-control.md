---
title: XMLNode (controllo)
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- XMLNode control
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: a8bd5c4612b59f909ae623eb4092a209798f98c5
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60085272"
---
# <a name="xmlnode-control"></a>XMLNode (controllo)
  **Importante** le informazioni definite in questo argomento relative a Microsoft Word sono presentati in modo esclusivo per il vantaggio e uso di singoli utenti e le organizzazioni che si trovano di fuori degli Stati Uniti e dei relativi territori o che usano o lo sviluppo i programmi eseguiti su, i prodotti di Microsoft Word che sono stati concessi in licenza da Microsoft prima di gennaio del 2010 quando Microsoft ha rimosso un'implementazione di una funzionalità specifica correlato a XML personalizzata da Microsoft Word. Queste informazioni relative a Microsoft Word non possono essere lette o utilizzate dagli singoli individui o organizzazioni negli Stati Uniti o relativo territori che usano o lo sviluppo di programmi in esecuzione in, i prodotti di Microsoft Word che sono stati concessi in licenza da Microsoft dopo il 10 gennaio 2010 ; tali prodotti non si comporterà come prodotti concessi in licenza prima di tale data o acquistati e concesso in licenza per l'utilizzo di fuori degli Stati Uniti.

 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]

 Il <xref:Microsoft.Office.Tools.Word.XMLNode> controllo rappresenta un nodo XML mappato che espone gli eventi e può essere associato a dati. Il <xref:Microsoft.Office.Tools.Word.XMLNode> controllo viene creato solo quando viene eseguito il mapping di un elemento dello schema non ripetuto nel documento di Microsoft Office Word. Dopo che Visual Studio ha creato il nodo XML, è possibile programmare contrastarla direttamente senza dover passare attraverso il modello a oggetti Word.

 Il <xref:Microsoft.Office.Tools.Word.XMLNode> controllo può essere eliminato solo eliminando il mapping dell'elemento in Word.

## <a name="bind-data-to-the-control"></a>Associare dati al controllo
 Un <xref:Microsoft.Office.Tools.Word.XMLNode> controllo supporta il data binding semplice. Il nodo XML deve essere associato a un'origine dati tramite il <xref:System.Windows.Forms.IBindableComponent.DataBindings%2A> proprietà. Se i dati nel set di dati associato vengono aggiornati, il controllo <xref:Microsoft.Office.Tools.Word.XMLNode> riflette tali modifiche.

## <a name="formatting"></a>Formattazione
 La formattazione che può essere applicato a un <xref:Microsoft.Office.Interop.Word.XMLNode> oggetto può essere applicato a un <xref:Microsoft.Office.Tools.Word.XMLNode> controllo. Questo include i tipi di carattere, stili di carattere di sottolineatura e gli stili di carattere.

## <a name="events"></a>Eventi
 Gli eventi seguenti sono disponibili per il controllo <xref:Microsoft.Office.Tools.Word.XMLNode> :

- <xref:Microsoft.Office.Tools.Word.XMLNode.AfterInsert>

- <xref:Microsoft.Office.Tools.Word.XMLNode.BeforeDelete>

- <xref:Microsoft.Office.Tools.Word.XMLNode.BindingContextChanged>

- <xref:Microsoft.Office.Tools.Word.XMLNode.ContextEnter>

- <xref:Microsoft.Office.Tools.Word.XMLNode.ContextLeave>

- <xref:Microsoft.Office.Tools.Word.XMLNode.Deselect>

- <xref:System.ComponentModel.IComponent.Disposed>

- <xref:Microsoft.Office.Tools.Word.XMLNode.Select>

- <xref:Microsoft.Office.Tools.Word.XMLNode.ValidationError>

## <a name="compare-events"></a>Confrontare gli eventi
 È possibile acquisire un evento quando l'utente sposta il cursore all'interno del contesto di un determinato <xref:Microsoft.Office.Tools.Word.XMLNode> controllo. Ad esempio, potrebbe essere un' <xref:Microsoft.Office.Tools.Word.XMLNode> controllo denominato `Customer` che ha un figlio <xref:Microsoft.Office.Tools.Word.XMLNode> controllo denominato `Company`, e `Company` ha due figlio <xref:Microsoft.Office.Tools.Word.XMLNode> controlli denominati `CompanyName` e `CompanyRegion` come indicato di seguito:

```xml
<Customer>
    <Company>
        <CompanyName>
        <CompanyRegion>
```

 Se si desidera visualizzare un controllo nel riquadro azioni ogni volta che il cursore viene spostato nel `Company` nodo, non è importante se il cursore viene posizionato `CompanyName` oppure `CompanyRegion` perché sono entrambe all'interno del contesto di `Company`. In questo caso, è possibile scrivere il codice <xref:Microsoft.Office.Tools.Word.XMLNode.ContextEnter> eventi di `Company`.

 Nella maggior parte dei casi, quando il cursore viene spostato un <xref:Microsoft.Office.Tools.Word.XMLNode> controllare, entrambe le <xref:Microsoft.Office.Tools.Word.XMLNode.Select> e <xref:Microsoft.Office.Tools.Word.XMLNode.ContextEnter> gli eventi vengono generati. Nella tabella seguente illustra le differenze tra questi eventi.

|Seleziona evento|Evento ContextEnter|
|------------------|------------------------|
|Si verifica quando il cursore viene posizionato all'interno di un <xref:Microsoft.Office.Tools.Word.XMLNode>.|Si verifica quando il cursore viene posizionato all'interno di un <xref:Microsoft.Office.Tools.Word.XMLNode> o uno dei relativi nodi figlio, da un'area all'esterno del contesto del nodo. In altre parole, si viene generato solo quando cambia il contesto.|

 Ad esempio, quando si sposta il cursore da fuori `Customer` in `CompanyName`, il <xref:Microsoft.Office.Tools.Word.XMLNode.ContextEnter> evento per `Customer`, `Company`, e `CompanyName` viene generato. Se poi si sposta il cursore a partire dal `CompanyName` al `CompanyRegion`, solo le <xref:Microsoft.Office.Tools.Word.XMLNode.ContextEnter> evento per `CompanyRegion` viene generato perché si è ancora all'interno del contesto di entrambi `Company` e `Customer`.

 Le stesse differenze esistono tra i <xref:Microsoft.Office.Tools.Word.XMLNode.ContextLeave> eventi e <xref:Microsoft.Office.Tools.Word.XMLNode.Deselect> evento.

## <a name="see-also"></a>Vedere anche
- [Cenni preliminari sui controlli host e gli elementi host](../vsto/host-items-and-host-controls-overview.md)
- [Automazione di Word usando oggetti estesi](../vsto/automating-word-by-using-extended-objects.md)
- [Controllo XMLNodes](../vsto/xmlnodes-control.md)
- [Procedura: Aggiungere controlli XMLNode ai documenti di Word](../vsto/how-to-add-xmlnode-controls-to-word-documents.md)
- [Procedura: Mappare schemi a documenti di Word in Visual Studio](../vsto/how-to-map-schemas-to-word-documents-inside-visual-studio.md)
- [Limitazioni a livello di codice degli elementi host e controlli host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
