---
title: XMLNodes (controllo)
description: Informazioni sul fatto che il controllo XMLNodes viene creato solo quando viene eseguito il mapping di un elemento dello schema ripetuto su un documento di Microsoft Word.
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
ms.workload:
- office
ms.openlocfilehash: d920df609c8172b6329cac537d10868e5795be12
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99894387"
---
# <a name="xmlnodes-control"></a>XMLNodes (controllo)
  **Importante** Le informazioni contenute in questo argomento riguardanti Microsoft Word sono presentate esclusivamente per il vantaggio e l'utilizzo di singoli utenti e organizzazioni che si trovano al di fuori del Stati Uniti e dei suoi territori o che utilizzano o sviluppano programmi eseguiti in Microsoft Word, che sono stati concessi in licenza da Microsoft prima del gennaio 2010, quando Microsoft ha rimosso un'implementazione di particolari funzionalità correlate a XML personalizzato da Microsoft Word. Queste informazioni relative a Microsoft Word non possono essere lette o usate da singoli utenti o organizzazioni nel Stati Uniti o nei suoi territori che usano o sviluppano programmi eseguiti in Microsoft Word prodotti concessi in licenza da Microsoft dopo il 10 gennaio 2010; tali prodotti non si comporteranno come prodotti concessi in licenza prima di tale data o acquistati e concessi in licenza per l'utilizzo al di fuori del Stati Uniti.

 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]

 Il <xref:Microsoft.Office.Tools.Word.XMLNodes> controllo è una raccolta di oggetti nodo XML mappati che espone gli eventi. Il <xref:Microsoft.Office.Tools.Word.XMLNodes> controllo viene creato solo quando viene eseguito il mapping di un elemento dello schema ripetuto su un documento di Microsoft Office Word. Se l'elemento ripetuto contiene elementi figlio, viene creato anche ogni elemento figlio come <xref:Microsoft.Office.Tools.Word.XMLNodes> controllo.

 Dopo la creazione della raccolta di nodi XML in Visual Studio, è possibile programmare direttamente sul controllo senza dover attraversare il modello a oggetti di Word. Il <xref:Microsoft.Office.Tools.Word.XMLNodes> controllo può essere eliminato solo rimuovendo il mapping degli elementi dal documento.

> [!NOTE]
> Se si accede a un elemento figlio del <xref:Microsoft.Office.Tools.Word.XMLNodes> controllo tramite la <xref:Microsoft.Office.Tools.Word.XMLNodes.Item%2A> proprietà, viene restituito un <xref:Microsoft.Office.Interop.Word.XMLNode> oggetto anziché un <xref:Microsoft.Office.Tools.Word.XMLNode> controllo. Per ulteriori informazioni, vedere [limitazioni a livello di codice di elementi host e controlli host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md).

## <a name="bind-data-to-the-control"></a>Associare dati al controllo
 Un <xref:Microsoft.Office.Tools.Word.XMLNodes> controllo non supporta data binding. Questo è dovuto al fatto <xref:Microsoft.Office.Tools.Word.XMLNodes> che il controllo non dispone di funzionalità di data binding complesse e data binding semplici non possono rappresentare dati ripetuti.

## <a name="formatting"></a>Formattazione
 Qualsiasi formattazione che può essere applicata al testo all'interno del documento può essere applicata a un <xref:Microsoft.Office.Tools.Word.XMLNodes> controllo.

## <a name="events"></a>Eventi
 Gli eventi disponibili per il <xref:Microsoft.Office.Tools.Word.XMLNodes> controllo sono i seguenti:

- <xref:Microsoft.Office.Tools.Word.XMLNodes.AfterInsert>

- <xref:Microsoft.Office.Tools.Word.XMLNodes.BeforeDelete>

- <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextEnter>

- <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextLeave>

- <xref:Microsoft.Office.Tools.Word.XMLNodes.Deselect>

- <xref:System.ComponentModel.IComponent.Disposed>

- <xref:Microsoft.Office.Tools.Word.XMLNodes.Select>

- <xref:Microsoft.Office.Tools.Word.XMLNodes.ValidationError>

## <a name="compare-events"></a>Confronta eventi
 È possibile acquisire un evento quando l'utente sposta il cursore all'interno del contesto di un determinato <xref:Microsoft.Office.Tools.Word.XMLNodes> controllo. È ad esempio possibile disporre di un <xref:Microsoft.Office.Tools.Word.XMLNodes> controllo denominato `Customer` con un controllo figlio <xref:Microsoft.Office.Tools.Word.XMLNodes> denominato `Company` e di `Company` due controlli figlio <xref:Microsoft.Office.Tools.Word.XMLNodes> denominati `CompanyName` e `CompanyRegion` come indicato di seguito:

```xml
<Customer>
    <Company>
        <CompanyName>
        <CompanyRegion>
```

 Se si desidera visualizzare un controllo nel riquadro azioni ogni volta che il cursore viene spostato nel `Company` nodo, non è importante se il cursore viene posizionato in `CompanyName` o `CompanyRegion` perché si trovano entrambi all'interno del contesto di `Company` . In questo caso, è possibile scrivere il codice nell' <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextEnter> evento di `Company` .

 Nella maggior parte dei casi, quando il cursore entra in un <xref:Microsoft.Office.Tools.Word.XMLNodes> controllo <xref:Microsoft.Office.Tools.Word.XMLNodes.Select> , <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextEnter> vengono generati entrambi gli eventi e. Nella tabella seguente vengono illustrate le differenze tra questi eventi.

|Seleziona evento|Evento ContextEnter|
|------------------|------------------------|
|Viene generato quando il cursore viene posizionato all'interno di uno dei nodi della raccolta <xref:Microsoft.Office.Tools.Word.XMLNodes>.|Viene generato quando il cursore viene posizionato in uno dei nodi o dei nodi di discendente della raccolta <xref:Microsoft.Office.Tools.Word.XMLNodes>, da un'area esterna del contesto del nodo. In altre parole, viene generato solo quando il contesto viene modificato e può essere generato per più controlli annidati <xref:Microsoft.Office.Tools.Word.XMLNodes> .|

 Ad esempio, quando si sposta il cursore dall'esterno di `Customer` in `CompanyName` , <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextEnter> vengono generati gli eventi per `Customer` , `Company` e `CompanyName` . Se quindi si sposta il cursore da `CompanyName` a `CompanyRegion` , <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextEnter> viene generato l'evento solo per `CompanyRegion` , perché il contesto è lo stesso sia per `Company` che per `Customer` . È possibile avere più `Company` nodi nel documento. Se si sposta il cursore dal `CompanyName` nodo di uno `Company` al `CompanyName` nodo di un altro `Company` , il contesto è lo stesso, in modo che venga generato solo l' <xref:Microsoft.Office.Tools.Word.XMLNodes.Select> evento.

 Esistono le stesse differenze tra l' <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextLeave> evento e l' <xref:Microsoft.Office.Tools.Word.XMLNodes.Deselect> evento.

## <a name="see-also"></a>Vedi anche
- [Cenni preliminari sugli elementi e sui controlli host](../vsto/host-items-and-host-controls-overview.md)
- [Automatizzare Word usando oggetti estesi](../vsto/automating-word-by-using-extended-objects.md)
- [XMLNode (controllo)](../vsto/xmlnode-control.md)
- [Procedura: aggiungere controlli XMLNodes ai documenti di Word](../vsto/how-to-add-xmlnodes-controls-to-word-documents.md)
- [Procedura: eseguire il mapping degli schemi a documenti di Word in Visual Studio](../vsto/how-to-map-schemas-to-word-documents-inside-visual-studio.md)
- [Limitazioni a livello di codice degli elementi e dei controlli host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
