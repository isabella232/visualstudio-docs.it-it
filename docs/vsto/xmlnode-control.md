---
title: XMLNode (controllo)
description: Informazioni sul controllo XMLNode è un oggetto nodo XML mappato che espone gli eventi e può essere associato ai dati.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 58f9c5db883f55c00236bc202797dcf2ec3003f6
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/15/2020
ms.locfileid: "97528342"
---
# <a name="xmlnode-control"></a>XMLNode (controllo)
  **Importante** Le informazioni contenute in questo argomento riguardanti Microsoft Word sono presentate esclusivamente per il vantaggio e l'utilizzo di singoli utenti e organizzazioni che si trovano al di fuori del Stati Uniti e dei suoi territori o che utilizzano o sviluppano programmi eseguiti in Microsoft Word, che sono stati concessi in licenza da Microsoft prima del gennaio 2010, quando Microsoft ha rimosso un'implementazione di particolari funzionalità correlate a XML personalizzato da Microsoft Word. Queste informazioni relative a Microsoft Word non possono essere lette o usate da singoli utenti o organizzazioni nel Stati Uniti o nei suoi territori che usano o sviluppano programmi eseguiti in Microsoft Word prodotti concessi in licenza da Microsoft dopo il 10 gennaio 2010; tali prodotti non si comporteranno come prodotti concessi in licenza prima di tale data o acquistati e concessi in licenza per l'utilizzo al di fuori del Stati Uniti.

 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]

 Il <xref:Microsoft.Office.Tools.Word.XMLNode> controllo è un oggetto nodo XML mappato che espone gli eventi e può essere associato ai dati. Il <xref:Microsoft.Office.Tools.Word.XMLNode> controllo viene creato solo quando viene eseguito il mapping di un elemento dello schema non ripetuto a un documento di Word Microsoft Office. Dopo che Visual Studio ha creato il nodo XML, è possibile programmare direttamente su di esso senza dover attraversare il modello a oggetti di Word.

 Il <xref:Microsoft.Office.Tools.Word.XMLNode> controllo può essere eliminato solo rimuovendo il mapping degli elementi in Word.

## <a name="bind-data-to-the-control"></a>Associare dati al controllo
 Un <xref:Microsoft.Office.Tools.Word.XMLNode> controllo supporta data binding semplici. Il nodo XML deve essere associato a un'origine dati tramite la <xref:System.Windows.Forms.IBindableComponent.DataBindings%2A> Proprietà. Se i dati nel set di dati associato vengono aggiornati, il controllo <xref:Microsoft.Office.Tools.Word.XMLNode> riflette tali modifiche.

## <a name="formatting"></a>Formattazione
 La formattazione che può essere applicata a un <xref:Microsoft.Office.Interop.Word.XMLNode> oggetto può essere applicata a un <xref:Microsoft.Office.Tools.Word.XMLNode> controllo. Sono inclusi tipi di carattere, stili di sottolineatura e stili di carattere.

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

## <a name="compare-events"></a>Confronta eventi
 È possibile acquisire un evento quando l'utente sposta il cursore all'interno del contesto di un determinato <xref:Microsoft.Office.Tools.Word.XMLNode> controllo. È ad esempio possibile disporre di un <xref:Microsoft.Office.Tools.Word.XMLNode> controllo denominato `Customer` con un controllo figlio <xref:Microsoft.Office.Tools.Word.XMLNode> denominato `Company` e di `Company` due controlli figlio <xref:Microsoft.Office.Tools.Word.XMLNode> denominati `CompanyName` e `CompanyRegion` come indicato di seguito:

```xml
<Customer>
    <Company>
        <CompanyName>
        <CompanyRegion>
```

 Se si desidera visualizzare un controllo nel riquadro azioni ogni volta che il cursore viene spostato nel `Company` nodo, non è importante se il cursore viene posizionato in `CompanyName` o `CompanyRegion` perché si trovano entrambi all'interno del contesto di `Company` . In questo caso, è possibile scrivere il codice nell' <xref:Microsoft.Office.Tools.Word.XMLNode.ContextEnter> evento di `Company` .

 Nella maggior parte dei casi, quando il cursore entra in un <xref:Microsoft.Office.Tools.Word.XMLNode> controllo <xref:Microsoft.Office.Tools.Word.XMLNode.Select> , <xref:Microsoft.Office.Tools.Word.XMLNode.ContextEnter> vengono generati entrambi gli eventi e. Nella tabella seguente vengono illustrate le differenze tra questi eventi.

|Seleziona evento|Evento ContextEnter|
|------------------|------------------------|
|Si verifica quando il cursore si trova all'interno di un oggetto <xref:Microsoft.Office.Tools.Word.XMLNode> .|Viene generato quando il cursore viene posizionato in un nodo <xref:Microsoft.Office.Tools.Word.XMLNode> o in uno dei nodi figlio, da un'area esterna dal contesto del nodo. In altre parole, viene generato solo quando il contesto viene modificato.|

 Ad esempio, quando si sposta il cursore dall'esterno di `Customer` in `CompanyName` , <xref:Microsoft.Office.Tools.Word.XMLNode.ContextEnter> viene generato l'evento per `Customer` , `Company` e `CompanyName` . Se quindi si sposta il cursore da `CompanyName` a `CompanyRegion` , <xref:Microsoft.Office.Tools.Word.XMLNode.ContextEnter> viene generato solo l'evento per `CompanyRegion` perché si è ancora all'interno del contesto sia di `Company` che di `Customer` .

 Esistono le stesse differenze tra l' <xref:Microsoft.Office.Tools.Word.XMLNode.ContextLeave> evento e l' <xref:Microsoft.Office.Tools.Word.XMLNode.Deselect> evento.

## <a name="see-also"></a>Vedere anche
- [Cenni preliminari sugli elementi e sui controlli host](../vsto/host-items-and-host-controls-overview.md)
- [Automatizzare Word usando oggetti estesi](../vsto/automating-word-by-using-extended-objects.md)
- [Controllo XMLNodes](../vsto/xmlnodes-control.md)
- [Procedura: aggiungere controlli XMLNode ai documenti di Word](../vsto/how-to-add-xmlnode-controls-to-word-documents.md)
- [Procedura: eseguire il mapping degli schemi a documenti di Word in Visual Studio](../vsto/how-to-map-schemas-to-word-documents-inside-visual-studio.md)
- [Limitazioni a livello di codice degli elementi e dei controlli host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
