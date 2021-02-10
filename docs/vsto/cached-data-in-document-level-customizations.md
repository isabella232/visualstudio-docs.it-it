---
title: Dati memorizzati nella cache nelle personalizzazioni a livello di documento
description: Informazioni sul modo in cui Visual Studio separa i dati dalla vista nelle personalizzazioni a livello di documento consentendo di incorporare i dati come cache di dati.
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
ms.workload:
- office
ms.openlocfilehash: f1c383b5367b2966b9fd082b2d47570264b4d191
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99955775"
---
# <a name="cached-data-in-document-level-customizations"></a>Dati memorizzati nella cache nelle personalizzazioni a livello di documento
  Uno degli obiettivi principali delle personalizzazioni a livello di documento consiste nel separare i dati dalla visualizzazione nei documenti di Office. I dati si riferiscono alle informazioni archiviate nel documento, inclusi i numeri e il testo. La vista fa riferimento all'interfaccia utente e al modello a oggetti di Microsoft Office Word e Microsoft Office Excel.

 Visual Studio separa i dati dalla vista nelle personalizzazioni a livello di documento consentendo di incorporare i dati come *isola di dati*, detta anche *cache dei dati*. È possibile leggere o modificare i dati direttamente senza avviare Word o Excel. Questa operazione è utile quando è necessario modificare i dati nei documenti in un server in cui non è installato Microsoft Office. Word ed Excel sono destinati all'uso negli ambienti client; non sono progettate per essere eseguite in un server.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 Per altre informazioni sulle personalizzazioni a livello di documento, vedere [Cenni preliminari sullo sviluppo di soluzioni Office &#40;&#41;VSTO ](../vsto/office-solutions-development-overview-vsto.md) e l' [architettura delle personalizzazioni a livello di documento](../vsto/architecture-of-document-level-customizations.md).

## <a name="understand-the-cached-data-programming-model"></a>Informazioni sul modello di programmazione dei dati memorizzato nella cache
 L'isola di dati può contenere qualsiasi oggetto della soluzione che soddisfi determinati requisiti. Questi oggetti includono <xref:System.Data.DataSet> oggetti, <xref:System.Data.DataTable> oggetti e qualsiasi altro oggetto che può essere serializzato dalla <xref:System.Xml.Serialization.XmlSerializer> classe. Per altre informazioni, vedere [memorizzare i dati nella cache](../vsto/caching-data.md).

 Per fornire la visualizzazione per i dati memorizzati nella cache, è possibile associare controlli Windows Form e *host* nel documento a oggetti nell'isola di dati. Il data binding tra l'isola di dati e i controlli associati a dati mantiene le due sincronizzate. È anche possibile aggiungere codice di convalida ai dati indipendenti dai controlli. Per altre informazioni, vedere [associare i dati ai controlli nelle soluzioni Office](../vsto/binding-data-to-controls-in-office-solutions.md).

 I controlli host sono versioni estese di oggetti nativi nei modelli a oggetti di Excel e Word. Diversamente dagli oggetti nativi, i controlli host possono essere associati direttamente a oggetti dati gestiti. Per altre informazioni, vedere Cenni [preliminari sugli elementi host e sui controlli host](../vsto/host-items-and-host-controls-overview.md) e [Windows Form sui controlli nei documenti di Office](../vsto/windows-forms-controls-on-office-documents-overview.md).

## <a name="access-cached-data-on-the-server"></a>Accesso ai dati memorizzati nella cache nel server
 Per accedere ai dati memorizzati nella cache in un documento, è possibile usare la <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> classe. Questa classe fa parte di [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] e può essere utilizzata in un server senza eseguire Excel o Word. Quando l'utente apre il documento dopo aver modificato i dati memorizzati nella cache, tutti i controlli associati ai dati vengono sincronizzati automaticamente con le modifiche e l'utente viene visualizzato con i dati aggiornati. Per ulteriori informazioni, vedere [accedere ai dati nei documenti sul server](../vsto/accessing-data-in-documents-on-the-server.md).

 Excel e Word non sono necessari per scrivere sui dati sul server, ma solo per visualizzarli nel client. Excel e Word non devono nemmeno essere installati nel server. In questo modo è possibile migliorare la scalabilità e la possibilità di eseguire l'elaborazione batch veloce di documenti che contengono isole di dati.

## <a name="data-caching-for-offline-use"></a>Memorizzazione dei dati nella cache per l'uso offline
 L'archiviazione dei dati nell'isola dati consente scenari offline. Quando un utente apre per la prima volta un documento o richiede il documento dal server, l'isola di dati viene riempita con i dati più recenti. L'isola di dati viene memorizzata nella cache del documento ed è quindi disponibile in modalità offline. L'utente (e il codice) può manipolare i dati, anche se non è disponibile alcuna connessione in tempo reale. Quando l'utente esegue la riconnessione, le modifiche ai dati possono essere propagate a un'origine dati del server.

## <a name="cached-data-and-custom-xml-parts-compared"></a>Confronto tra dati memorizzati nella cache e parti XML personalizzate
 Le parti XML personalizzate sono state introdotte nel sistema di Microsoft Office 2007 come modo per archiviare parti arbitrarie di XML in un documento. Sebbene le parti XML personalizzate siano utili in molti degli stessi scenari della cache dei dati, esistono alcune differenze tra l'isola di dati e le parti XML personalizzate. Per ulteriori informazioni sulle parti XML personalizzate, vedere [Cenni preliminari sulle parti XML personalizzate](../vsto/custom-xml-parts-overview.md).

 Nella tabella seguente sono elencate alcune differenze e analogie.

|Domanda/caratteristica|Cache dei dati|Parti XML personalizzate|
|-|----------------|----------------------|
|Quali applicazioni Office possono utilizzare?|Personalizzazioni a livello di documento per le applicazioni seguenti:<br /><br /> -Excel<br />-Word|Soluzioni a livello di documento e di applicazione per le applicazioni seguenti:<br /><br /> -Excel<br />-PowerPoint<br />-Word|
|Quali tipi di dati è possibile archiviare?|Qualsiasi oggetto pubblico nell'assembly di personalizzazione che soddisfi determinati requisiti. Per altre informazioni, vedere [memorizzare i dati nella cache](../vsto/caching-data.md).|Qualsiasi dato XML.|
|È possibile accedere ai dati senza avviare Microsoft Office applicazioni?|Sì, usando la <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> classe fornita da [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] .|Sì, usando le classi nello <xref:System.IO.Packaging> spazio dei nomi o usando Open XML Format SDK.|

## <a name="see-also"></a>Vedi anche
- [Dati nelle soluzioni Office](../vsto/data-in-office-solutions.md)
- [Architettura delle soluzioni Office in Visual Studio](../vsto/architecture-of-office-solutions-in-visual-studio.md)
