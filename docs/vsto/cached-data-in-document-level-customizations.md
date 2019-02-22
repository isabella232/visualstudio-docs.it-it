---
title: Dati memorizzati nella cache nelle personalizzazioni a livello di documento
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 62b0d04e37072af1f0053a6e395edcb856a115c1
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/21/2019
ms.locfileid: "56645381"
---
# <a name="cached-data-in-document-level-customizations"></a>Dati memorizzati nella cache nelle personalizzazioni a livello di documento
  Degli obiettivi principali di personalizzazioni a livello di documento consiste nel separare i dati dalla visualizzazione nei documenti di Office. I dati fanno riferimento alle informazioni che vengono archiviate nel documento, inclusi i numeri e testo. Visualizzazione si intende l'interfaccia utente e il modello a oggetti di Microsoft Office Word e Microsoft Office Excel.

 Visual Studio separa i dati dalla vista nelle personalizzazioni a livello di documento, consentendo di dati incorporati come un *isola di dati*, definita anche la *cache dei dati*. È possibile leggere o modificare i dati direttamente senza avviare Word o Excel. Ciò è utile quando è necessario modificare i dati nei documenti in un server che non è installato Microsoft Office. Word ed Excel devono essere utilizzati in ambienti client; non sono progettate per essere eseguiti in un server.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 Per altre informazioni sulle personalizzazioni a livello di documento, vedere [Cenni preliminari sullo sviluppo di soluzioni Office &#40;VSTO&#41; ](../vsto/office-solutions-development-overview-vsto.md) e [architettura delle personalizzazioni a livello di documento](../vsto/architecture-of-document-level-customizations.md).

## <a name="understand-the-cached-data-programming-model"></a>Comprendere il modello di programmazione dati memorizzati nella cache
 Isola di dati può contenere qualsiasi oggetto nella soluzione che soddisfi determinati requisiti. Questi oggetti includono <xref:System.Data.DataSet> oggetti <xref:System.Data.DataTable> oggetti e qualsiasi altro oggetto che può essere serializzato dal <xref:System.Xml.Serialization.XmlSerializer> classe. Per altre informazioni, vedere [memorizzare nella Cache dati](../vsto/caching-data.md).

 Per garantire la visualizzazione per i dati memorizzati nella cache, è possibile associare controlli Windows Form e *ospitare controlli* sul documento per gli oggetti nell'isola di dati. Data binding tra l'isola di dati e i controlli con associazione a dati consente di garantire la sincronizzazione. È anche possibile aggiungere il codice di convalida per i dati che sono indipendenti dei controlli. Per altre informazioni, vedere [associare dati a controlli nelle soluzioni Office](../vsto/binding-data-to-controls-in-office-solutions.md).

 Controlli host sono versioni estese di oggetti nativi di modelli a oggetti di Excel e Word. A differenza di oggetti nativi, i controlli host possono essere associati direttamente a oggetti di dati gestiti. Per altre informazioni, vedere [elementi Host e host Cenni preliminari sui controlli](../vsto/host-items-and-host-controls-overview.md) e [controlli Windows Form nella panoramica di documenti Office](../vsto/windows-forms-controls-on-office-documents-overview.md).

## <a name="access-cached-data-on-the-server"></a>Accesso memorizzato nella cache i dati nel server
 Per accedere ai dati memorizzati nella cache in un documento, è possibile usare il <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> classe. Questa classe fa parte di [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)], e può essere usato in un server non in esecuzione Excel o Word. Quando l'utente apre il documento dopo che è modificare i dati memorizzati nella cache, tutti i controlli associati ai dati verranno sincronizzati automaticamente le modifiche e viene visualizzato con i dati aggiornati. Per altre informazioni, vedere [accedere ai dati dei documenti sul server](../vsto/accessing-data-in-documents-on-the-server.md).

 Excel e Word non sono necessarie per scrivere i dati nel server, solo per la visualizzazione nel client. Excel e Word non è neanche necessario venga installato nel server. Ciò offre una migliore scalabilità e la possibilità di eseguire velocizzare l'elaborazione batch di documenti che contengono le isole di dati.

## <a name="data-caching-for-offline-use"></a>Dati la memorizzazione nella cache per l'uso offline
 L'archiviazione dei dati nell'isola di dati consente gli scenari non in linea. Quando un utente apre un documento prima di tutto o richiede il documento al server, l'isola di dati viene riempita con i dati più recenti. Isola di dati viene memorizzato nella cache del documento ed è quindi disponibile offline. L'utente (e il codice) consente di modificare i dati, anche se è disponibile alcuna connessione in tempo reale. Quando l'utente viene riconnessa, le modifiche ai dati possono essere propagate a un'origine dati server.

## <a name="cached-data-and-custom-xml-parts-compared"></a>Dati memorizzati nella cache e le parti XML personalizzate rispetto
 Parti XML personalizzate sono stati introdotti in Microsoft Office system 2007 consentono di archiviare di elementi XML arbitrari in un documento. Anche se le parti XML personalizzate sono utili in molti degli stessi scenari come la cache dei dati, esistono alcune differenze tra l'isola di dati e parti XML personalizzate. Per altre informazioni sulle parti XML personalizzate, vedere [panoramica delle parti XML personalizzate](../vsto/custom-xml-parts-overview.md).

 La tabella seguente elenca alcune delle differenze e analogie.

||Cache dei dati|Parti XML personalizzate|
|-|----------------|----------------------|
|Applicazioni di Office che è possono usare questi?|Personalizzazioni a livello di documento per le applicazioni seguenti:<br /><br /> -   Excel<br />-   Word|Soluzioni a livello di documento e a livello di applicazione per le applicazioni seguenti:<br /><br /> -   Excel<br />-   PowerPoint<br />-   Word|
|Quali tipi di dati è possibile archiviare?|Qualsiasi oggetto pubblica nell'assembly di personalizzazione che soddisfi determinati requisiti. Per altre informazioni, vedere [memorizzare nella Cache dati](../vsto/caching-data.md).|Tutti i dati XML.|
|È possibile accedere ai dati senza avviare le applicazioni Microsoft Office?|Sì, tramite il <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> classe fornita dal [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)].|Sì, tramite le classi di <xref:System.IO.Packaging> dello spazio dei nomi, oppure usando il formato SDK per Open XML.|

## <a name="see-also"></a>Vedere anche
- [Dati nelle soluzioni Office](../vsto/data-in-office-solutions.md)
- [Architettura delle soluzioni Office in Visual Studio](../vsto/architecture-of-office-solutions-in-visual-studio.md)
