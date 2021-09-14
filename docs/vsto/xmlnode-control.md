---
title: XMLNode (controllo)
description: Si apprenderà che il controllo XMLNode è un oggetto nodo XML mappato che espone eventi e può essere associato ai dati.
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
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 8b3c67526ac00f9cc7266f6bb93992505d3b70ad
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126710579"
---
# <a name="xmlnode-control"></a>XMLNode (controllo)
  **Importante** Le informazioni contenute in questo argomento relative a Microsoft Word vengono presentate esclusivamente a vantaggio e all'uso di singoli utenti e organizzazioni che si trovano all'esterno del Stati Uniti e dei relativi territori o che usano o sviluppano programmi eseguiti su prodotti Microsoft Word concessi in licenza da Microsoft prima di gennaio 2010, quando Microsoft ha rimosso un'implementazione di funzionalità specifiche correlate al codice XML personalizzato da Microsoft Word. Queste informazioni relative Microsoft Word non possono essere lette o usate da singoli utenti o organizzazioni nel Stati Uniti o nei relativi territori che usano o sviluppano programmi eseguiti su prodotti Microsoft Word concessi in licenza da Microsoft dopo il 10 gennaio 2010; Tali prodotti non si comporteranno come i prodotti concessi in licenza prima di tale data o acquistati e concessi in licenza per l'uso al di fuori del Stati Uniti.

 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]

 Il <xref:Microsoft.Office.Tools.Word.XMLNode> controllo è un oggetto nodo XML mappato che espone eventi e può essere associato ai dati. Il controllo viene creato solo quando viene eseguito il mapping di un elemento dello schema non ripetuto <xref:Microsoft.Office.Tools.Word.XMLNode> a un Microsoft Office documento di Word. Dopo Visual Studio il nodo XML, è possibile programmarlo direttamente senza dover attraversare il modello a oggetti di Word.

 Il <xref:Microsoft.Office.Tools.Word.XMLNode> controllo può essere eliminato solo rimuovendo il mapping degli elementi in Word.

## <a name="bind-data-to-the-control"></a>Associare dati al controllo
 Un <xref:Microsoft.Office.Tools.Word.XMLNode> controllo supporta l'data binding. Il nodo XML deve essere associato a un'origine dati tramite la <xref:System.Windows.Forms.IBindableComponent.DataBindings%2A> proprietà . Se i dati nel set di dati associato vengono aggiornati, il controllo <xref:Microsoft.Office.Tools.Word.XMLNode> riflette tali modifiche.

## <a name="formatting"></a>Formattazione
 La formattazione che può essere applicata a <xref:Microsoft.Office.Interop.Word.XMLNode> un oggetto può essere applicata a un controllo <xref:Microsoft.Office.Tools.Word.XMLNode> . Sono inclusi i tipi di carattere, gli stili di sottolineatura e gli stili di carattere.

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
 È possibile acquisire un evento quando l'utente sposta il cursore all'interno del contesto di un determinato <xref:Microsoft.Office.Tools.Word.XMLNode> controllo. Ad esempio, si potrebbe avere un controllo denominato con un controllo figlio denominato e con due <xref:Microsoft.Office.Tools.Word.XMLNode> controlli figlio denominati e , come indicato `Customer` di <xref:Microsoft.Office.Tools.Word.XMLNode> `Company` `Company` <xref:Microsoft.Office.Tools.Word.XMLNode> `CompanyName` `CompanyRegion` seguito:

```xml
<Customer>
    <Company>
        <CompanyName>
        <CompanyRegion>
```

 Se si desidera visualizzare un controllo nel riquadro azioni ogni volta che il cursore viene spostato nel nodo, non è importante se il cursore è posizionato in o perché entrambi si trova all'interno del `Company` `CompanyName` contesto di `CompanyRegion` `Company` . In questo caso, è possibile scrivere il codice in <xref:Microsoft.Office.Tools.Word.XMLNode.ContextEnter> caso di `Company` .

 Nella maggior parte dei casi, quando il cursore entra in <xref:Microsoft.Office.Tools.Word.XMLNode> un controllo, vengono generati <xref:Microsoft.Office.Tools.Word.XMLNode.Select> entrambi gli eventi e <xref:Microsoft.Office.Tools.Word.XMLNode.ContextEnter> . La tabella seguente illustra le differenze tra questi eventi.

|Selezionare l'evento|Evento ContextEnter|
|------------------|------------------------|
|Si verifica quando il cursore viene posizionato all'interno di un oggetto <xref:Microsoft.Office.Tools.Word.XMLNode> .|Viene generato quando il cursore viene posizionato in un nodo <xref:Microsoft.Office.Tools.Word.XMLNode> o in uno dei nodi figlio, da un'area esterna dal contesto del nodo. In altre parole, viene generato solo quando cambia il contesto.|

 Ad esempio, quando si sposta il cursore dall'esterno di in , viene `Customer` `CompanyName` generato <xref:Microsoft.Office.Tools.Word.XMLNode.ContextEnter> l'evento per `Customer` , e `Company` `CompanyName` . Se quindi si sposta il cursore da a , viene generato solo l'evento per perché ci si trova ancora `CompanyName` nel contesto di e `CompanyRegion` <xref:Microsoft.Office.Tools.Word.XMLNode.ContextEnter> `CompanyRegion` `Company` `Customer` .

 Esistono le stesse differenze tra <xref:Microsoft.Office.Tools.Word.XMLNode.ContextLeave> l'evento e <xref:Microsoft.Office.Tools.Word.XMLNode.Deselect> l'evento .

## <a name="see-also"></a>Vedi anche
- [Panoramica degli elementi host e dei controlli host](../vsto/host-items-and-host-controls-overview.md)
- [Automatizzare Word usando oggetti estesi](../vsto/automating-word-by-using-extended-objects.md)
- [Controllo XMLNodes](../vsto/xmlnodes-control.md)
- [Procedura: Aggiungere controlli XMLNode a documenti di Word](../vsto/how-to-add-xmlnode-controls-to-word-documents.md)
- [Procedura: Eseguire il mapping di schemi a documenti di Word all'interno Visual Studio](../vsto/how-to-map-schemas-to-word-documents-inside-visual-studio.md)
- [Limitazioni a livello di codice di elementi host e controlli host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
