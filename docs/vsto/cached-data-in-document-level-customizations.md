---
title: Dati memorizzati nella cache nelle personalizzazioni a livello di documento
description: Informazioni su Visual Studio i dati dalla visualizzazione nelle personalizzazioni a livello di documento abilitando l'incorporazione dei dati come cache dei dati.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data islands [Office development in Visual Studio]
- view [Office development in Visual Studio]
- caching data [Office development in Visual Studio], about caching data
- data caching [Office development in Visual Studio], about data caching
- data [Office development in Visual Studio], cache
- data [Office development in Visual Studio], document-level solutions
- document-level customizations [Office development in Visual Studio], data model
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 528e452142bbac81654a6f55878265ee544ddb39
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122083737"
---
# <a name="cached-data-in-document-level-customizations"></a>Dati memorizzati nella cache nelle personalizzazioni a livello di documento
  L'obiettivo principale delle personalizzazioni a livello di documento è separare i dati dalla visualizzazione Office documenti. I dati si riferiscono alle informazioni archiviate nel documento, inclusi numeri e testo. View fa riferimento all'interfaccia utente e al modello a oggetti Microsoft Office Word e Microsoft Office Excel.

 Visual Studio separa i dati dalla visualizzazione nelle personalizzazioni *a* livello di documento consentendo l'incorporazione dei dati come isola di dati , denominata anche cache *dei dati*. È possibile leggere o modificare i dati direttamente senza avviare Word o Excel. Ciò è utile quando è necessario modificare i dati nei documenti in un server in cui non Microsoft Office installati. Word e Excel sono destinati all'uso negli ambienti client; non sono progettati per essere eseguiti in un server.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 Per altre informazioni sulle personalizzazioni [](../vsto/office-solutions-development-overview-vsto.md) a livello di documento, vedere Office panoramica dello sviluppo di soluzioni &#40;VSTO&#41;[e Architettura delle personalizzazioni](../vsto/architecture-of-document-level-customizations.md)a livello di documento .

## <a name="understand-the-cached-data-programming-model"></a>Informazioni sul modello di programmazione dei dati memorizzati nella cache
 L'isola dati può contenere qualsiasi oggetto nella soluzione che soddisfi determinati requisiti. Questi oggetti includono oggetti , oggetti e qualsiasi altro oggetto che <xref:System.Data.DataSet> <xref:System.Data.DataTable> può essere serializzato dalla classe <xref:System.Xml.Serialization.XmlSerializer> . Per altre informazioni, vedere [Memorizzare nella cache i dati](../vsto/caching-data.md).

 Per fornire la visualizzazione per i dati memorizzati nella cache, è possibile associare Windows form e controlli *host* nel documento agli oggetti nell'isola di dati. Il data binding tra l'isola di dati e i controlli associati a dati mantiene sincronizzati i due elementi. È anche possibile aggiungere codice di convalida ai dati indipendenti dai controlli. Per altre informazioni, vedere [Associare dati ai controlli in Office soluzioni](../vsto/binding-data-to-controls-in-office-solutions.md).

 I controlli host sono versioni estese degli oggetti nativi nei modelli a oggetti Excel e Word. A differenza degli oggetti nativi, i controlli host possono essere associati direttamente agli oggetti dati gestiti. Per altre informazioni, vedere Panoramica degli [elementi host](../vsto/host-items-and-host-controls-overview.md) e dei controlli host e Windows dei form Office [documenti.](../vsto/windows-forms-controls-on-office-documents-overview.md)

## <a name="access-cached-data-on-the-server"></a>Accedere ai dati memorizzati nella cache nel server
 Per accedere ai dati memorizzati nella cache in un documento, è possibile usare la <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> classe . Questa classe fa parte di e può essere usata in un server senza eseguire Excel [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] o Word. Quando l'utente apre il documento dopo aver modificato i dati memorizzati nella cache, tutti i controlli associati ai dati vengono sincronizzati automaticamente con le modifiche e all'utente vengono presentati i dati aggiornati. Per altre informazioni, vedere [Accedere ai dati nei documenti nel server](../vsto/accessing-data-in-documents-on-the-server.md).

 Excel e Word non sono necessari per scrivere nei dati nel server, ma solo per visualizzarli nel client. Excel e Word non devono neanche essere installati nel server. Ciò offre una scalabilità migliorata e la possibilità di eseguire un'elaborazione batch veloce di documenti che contengono isole di dati.

## <a name="data-caching-for-offline-use"></a>Memorizzazione nella cache dei dati per l'uso offline
 L'archiviazione dei dati nell'isola di dati consente scenari offline. Quando un utente apre per la prima volta un documento o richiede il documento dal server, l'isola di dati viene riempita con i dati più recenti. L'isola di dati viene memorizzata nella cache del documento e quindi è disponibile offline. L'utente (e il codice) possono modificare i dati, anche se non è disponibile alcuna connessione attiva. Quando l'utente si riconnette, le modifiche ai dati possono essere propagate nuovamente a un'origine dati del server.

## <a name="cached-data-and-custom-xml-parts-compared"></a>Dati memorizzati nella cache e parti XML personalizzate confrontate
 Le parti XML personalizzate sono state introdotte nel sistema Microsoft Office 2007 come modo per archiviare parti arbitrarie di XML in un documento. Sebbene le parti XML personalizzate siano utili in molti degli stessi scenari della cache dei dati, esistono alcune differenze tra l'isola di dati e le parti XML personalizzate. Per altre informazioni sulle parti XML personalizzate, vedere [Panoramica delle parti XML personalizzate](../vsto/custom-xml-parts-overview.md).

 Nella tabella seguente sono elencate alcune differenze e analogie.

|Domanda/caratteristica|Cache dei dati|Parti XML personalizzate|
|-|----------------|----------------------|
|Quali Office applicazioni possono usarle?|Personalizzazioni a livello di documento per le applicazioni seguenti:<br /><br /> - Excel<br />- Parola|Soluzioni a livello di documento e a livello di applicazione per le applicazioni seguenti:<br /><br /> - Excel<br />- PowerPoint<br />- Parola|
|Quali tipi di dati è possibile archiviare?|Qualsiasi oggetto pubblico nell'assembly di personalizzazione che soddisfi determinati requisiti. Per altre informazioni, vedere [Memorizzare nella cache i dati](../vsto/caching-data.md).|Tutti i dati XML.|
|È possibile accedere ai dati senza avviare Microsoft Office applicazioni?|Sì, usando la <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> classe fornita da [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] .|Sì, usando le classi nello spazio <xref:System.IO.Packaging> dei nomi o usando Open XML Format SDK.|

## <a name="see-also"></a>Vedi anche
- [Dati nelle soluzioni Office dati](../vsto/data-in-office-solutions.md)
- [Architettura delle Office in Visual Studio](../vsto/architecture-of-office-solutions-in-visual-studio.md)
