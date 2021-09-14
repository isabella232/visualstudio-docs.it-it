---
title: XMLNodes (controllo)
description: Informazioni sul fatto che il controllo XMLNodes viene creato solo quando viene eseguito il mapping di un elemento dello schema ripetuto a un Microsoft Word documento.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: cad5ca717f5e996fcc32c4806c6ab86afc7cc241
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126710575"
---
# <a name="xmlnodes-control"></a>XMLNodes (controllo)
  **Importante** Le informazioni contenute in questo argomento relative a Microsoft Word vengono presentate esclusivamente a vantaggio e all'uso di utenti e organizzazioni che si trovano al di fuori del Stati Uniti e dei relativi territori o che usano o sviluppano programmi che vengono eseguiti su prodotti Microsoft Word concessi in licenza da Microsoft prima di gennaio 2010, quando Microsoft ha rimosso un'implementazione di funzionalità specifiche correlate al codice XML personalizzato da Microsoft Word. Queste informazioni relative Microsoft Word non possono essere lette o usate da singoli utenti o organizzazioni nel Stati Uniti o nei relativi territori che usano o sviluppano programmi in esecuzione su prodotti Microsoft Word concessi in licenza da Microsoft dopo il 10 gennaio 2010; tali prodotti non si comporteranno come i prodotti concessi in licenza prima di tale data o acquistati e concessi in licenza per l'uso al di fuori del Stati Uniti.

 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]

 Il <xref:Microsoft.Office.Tools.Word.XMLNodes> controllo è una raccolta di oggetti nodo XML mappati che espone eventi. Il controllo viene creato solo quando viene eseguito il mapping di un elemento dello schema ripetuto a un <xref:Microsoft.Office.Tools.Word.XMLNodes> Microsoft Office documento di Word. Se l'elemento ripetuto contiene elementi figlio, ogni elemento figlio viene creato anche come <xref:Microsoft.Office.Tools.Word.XMLNodes> controllo .

 Dopo Visual Studio crea la raccolta di nodi XML, è possibile eseguire la programmazione direttamente sul controllo senza dover attraversare il modello a oggetti di Word. Il <xref:Microsoft.Office.Tools.Word.XMLNodes> controllo può essere eliminato solo rimuovendo il mapping degli elementi dal documento.

> [!NOTE]
> Se si accede a un elemento figlio del controllo tramite la proprietà , viene restituito un <xref:Microsoft.Office.Tools.Word.XMLNodes> oggetto anziché un controllo <xref:Microsoft.Office.Tools.Word.XMLNodes.Item%2A> <xref:Microsoft.Office.Interop.Word.XMLNode> <xref:Microsoft.Office.Tools.Word.XMLNode> . Per altre informazioni, vedere [Limitazioni a livello di codice degli elementi host e dei controlli host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md).

## <a name="bind-data-to-the-control"></a>Associare dati al controllo
 Un <xref:Microsoft.Office.Tools.Word.XMLNodes> controllo non supporta la data binding. Ciò è dovuto al fatto che il controllo non dispone di data binding complesse e <xref:Microsoft.Office.Tools.Word.XMLNodes> data binding non può rappresentare dati ripetuti.

## <a name="formatting"></a>Formattazione
 Qualsiasi formattazione che può essere applicata al testo all'interno del documento può essere applicata a un <xref:Microsoft.Office.Tools.Word.XMLNodes> controllo .

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
 È possibile acquisire un evento quando l'utente sposta il cursore all'interno del contesto di un determinato <xref:Microsoft.Office.Tools.Word.XMLNodes> controllo. Ad esempio, è possibile avere un controllo denominato con un controllo figlio denominato e con <xref:Microsoft.Office.Tools.Word.XMLNodes> due controlli figlio denominati e come indicato `Customer` di <xref:Microsoft.Office.Tools.Word.XMLNodes> `Company` `Company` <xref:Microsoft.Office.Tools.Word.XMLNodes> `CompanyName` `CompanyRegion` seguito:

```xml
<Customer>
    <Company>
        <CompanyName>
        <CompanyRegion>
```

 Se si desidera visualizzare un controllo nel riquadro azioni ogni volta che il cursore viene spostato nel nodo, non deve essere importante se il cursore è posizionato in o perché si trova entrambi all'interno del `Company` `CompanyName` contesto di `CompanyRegion` `Company` . In questo caso, è possibile scrivere il codice in <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextEnter> caso di `Company` .

 Nella maggior parte dei casi, quando il cursore entra in un controllo , vengono generati entrambi <xref:Microsoft.Office.Tools.Word.XMLNodes> <xref:Microsoft.Office.Tools.Word.XMLNodes.Select> gli eventi e <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextEnter> . La tabella seguente illustra le differenze tra questi eventi.

|Selezionare l'evento|Evento ContextEnter|
|------------------|------------------------|
|Viene generato quando il cursore viene posizionato all'interno di uno dei nodi della raccolta <xref:Microsoft.Office.Tools.Word.XMLNodes>.|Viene generato quando il cursore viene posizionato in uno dei nodi o dei nodi di discendente della raccolta <xref:Microsoft.Office.Tools.Word.XMLNodes>, da un'area esterna del contesto del nodo. In altre parole, viene generato solo quando il contesto cambia e può essere generato per più controlli <xref:Microsoft.Office.Tools.Word.XMLNodes> annidati.|

 Ad esempio, quando si sposta il cursore dall'esterno di in , vengono generati `Customer` gli eventi per , e `CompanyName` <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextEnter> `Customer` `Company` `CompanyName` . Se quindi si sposta il cursore da a , viene generato l'evento solo per , perché il contesto è lo `CompanyName` stesso sia per che per `CompanyRegion` <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextEnter> `CompanyRegion` `Company` `Customer` . È possibile avere `Company` più nodi nel documento. Se si sposta il cursore dal nodo di uno al nodo di un altro , il contesto è lo stesso, quindi viene generato `CompanyName` `Company` solo `CompanyName` `Company` <xref:Microsoft.Office.Tools.Word.XMLNodes.Select> l'evento .

 Esistono le stesse differenze tra <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextLeave> l'evento e <xref:Microsoft.Office.Tools.Word.XMLNodes.Deselect> l'evento .

## <a name="see-also"></a>Vedi anche
- [Panoramica degli elementi host e dei controlli host](../vsto/host-items-and-host-controls-overview.md)
- [Automatizzare Word usando oggetti estesi](../vsto/automating-word-by-using-extended-objects.md)
- [Controllo XMLNode](../vsto/xmlnode-control.md)
- [Procedura: Aggiungere controlli XMLNodes ai documenti di Word](../vsto/how-to-add-xmlnodes-controls-to-word-documents.md)
- [Procedura: Eseguire il mapping degli schemi ai documenti di Word all'interno Visual Studio](../vsto/how-to-map-schemas-to-word-documents-inside-visual-studio.md)
- [Limitazioni a livello di codice di elementi host e controlli host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
