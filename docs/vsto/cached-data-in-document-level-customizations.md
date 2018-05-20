---
title: Dati memorizzati nella cache nelle personalizzazioni a livello di documento
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
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
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: bd93d985b72f945e7a1c70199d6ff3aacf5f0229
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/17/2018
---
# <a name="cached-data-in-document-level-customizations"></a>Dati memorizzati nella cache nelle personalizzazioni a livello di documento
  Un obiettivo principale di personalizzazioni a livello di documento è per separare i dati dalla visualizzazione nei documenti di Office. Dati fa riferimento alle informazioni archiviate nel documento, inclusi i numeri e testo. Vista fa riferimento per l'interfaccia utente e il modello a oggetti di Microsoft Office Word e Microsoft Office Excel.  
  
 Visual Studio separa i dati dalla visualizzazione nelle personalizzazioni a livello di documento consentendo di essere incorporati come dati un *isola di dati*, denominati anche il *cache dei dati*. È possibile leggere o modificare i dati direttamente senza avviare Word o Excel. Ciò è utile quando è necessario modificare i dati nei documenti in un server che non è installato Microsoft Office. Word ed Excel devono essere utilizzati in ambienti client; essi non sono progettati per essere eseguito su un server.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 Per ulteriori informazioni sulle personalizzazioni a livello di documento, vedere [Cenni preliminari sullo sviluppo di soluzioni Office &#40;VSTO&#41; ](../vsto/office-solutions-development-overview-vsto.md) e [architettura delle personalizzazioni a livello di documento](../vsto/architecture-of-document-level-customizations.md).  
  
## <a name="understand-the-cached-data-programming-model"></a>Comprendere il modello di programmazione dati memorizzati nella cache  
 L'isola di dati può contenere qualsiasi oggetto della soluzione che soddisfano determinati requisiti. Questi oggetti includono <xref:System.Data.DataSet> oggetti, <xref:System.Data.DataTable> oggetti e qualsiasi altro oggetto che può essere serializzato dalla <xref:System.Xml.Serialization.XmlSerializer> classe. Per altre informazioni, vedere vedere [memorizzare nella Cache dati](../vsto/caching-data.md).  
  
 Per garantire la visualizzazione di dati memorizzati nella cache, è possibile associare controlli Windows Form e *controlli host* sul documento per gli oggetti dell'isola di dati. Associazione dati tra l'isola di dati e i controlli con associazione a dati consente di garantire la sincronizzazione. È anche possibile aggiungere il codice di convalida per i dati che sono indipendenti dai controlli. Per altre informazioni, vedere [associare dati ai controlli nelle soluzioni Office](../vsto/binding-data-to-controls-in-office-solutions.md).  
  
 Controlli host sono versioni estese di oggetti nativi di modelli a oggetti di Excel e Word. A differenza degli oggetti nativi, controlli host possono essere associati direttamente a oggetti di dati gestiti. Per altre informazioni, vedere [elementi Host e host Cenni preliminari sui controlli](../vsto/host-items-and-host-controls-overview.md) e [controlli Windows Form nella panoramica di documenti di Office](../vsto/windows-forms-controls-on-office-documents-overview.md).  
  
## <a name="access-cached-data-on-the-server"></a>Accesso memorizzato nella cache i dati nel server  
 Per accedere a dati memorizzati nella cache in un documento, è possibile utilizzare la <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> classe. Questa classe fa parte di [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)], e può essere utilizzato in un server senza eseguire Excel o Word. Quando l'utente apre il documento dopo che si modificano i dati memorizzati nella cache, tutti i controlli associati ai dati vengono sincronizzati automaticamente con le modifiche e viene visualizzato l'utente con i dati aggiornati. Per altre informazioni, vedere [l'accesso ai dati dei documenti sul server](../vsto/accessing-data-in-documents-on-the-server.md).  
  
 Excel e Word non sono necessari per scrivere i dati nel server, ma solo per visualizzarli nel client. Excel e Word non è anche necessario installare nel server. Ciò offre una migliore scalabilità e la possibilità di eseguire una rapida elaborazione batch dei documenti che contengono isole di dati.  
  
## <a name="data-caching-for-offline-use"></a>Dati la memorizzazione nella cache per l'utilizzo offline  
 L'archiviazione dei dati nell'isola di dati consente scenari offline. Quando un utente prima di tutto apre un documento o richiede il documento dal server, l'isola di dati viene riempita con i dati più recenti. L'isola di dati verrà memorizzati nella cache del documento e sarà quindi disponibile offline. L'utente (e il codice) consente di modificare i dati, anche se è disponibile alcuna connessione in tempo reale. Quando l'utente si riconnette, le modifiche ai dati possono essere propagate a un'origine dati di server.  
  
## <a name="cached-data-and-custom-xml-parts-compared"></a>Dati memorizzati nella cache e confrontato confrontati Web part XML personalizzate  
 Parti XML personalizzate sono state introdotte in Microsoft Office system 2007 come un modo per l'archiviazione di elementi XML arbitrari in un documento. Anche se le parti XML personalizzate sono utili in molti degli stessi scenari di cache di dati, esistono alcune differenze tra l'isola di dati e le parti XML personalizzate. Per ulteriori informazioni sulle parti XML personalizzate, vedere [panoramica delle parti XML personalizzate](../vsto/custom-xml-parts-overview.md).  
  
 Nella tabella seguente sono elencate alcune delle analogie e differenze.  
  
||Cache dei dati|Parti XML personalizzate|  
|-|----------------|----------------------|  
|Applicazioni di Office possono usare questi?|Personalizzazioni a livello di documento per le applicazioni seguenti:<br /><br /> -Excel<br />-Word|Soluzioni a livello di documento e a livello di applicazione per le applicazioni seguenti:<br /><br /> -Excel<br />-PowerPoint<br />-Word|  
|I tipi di dati è possibile archiviare?|Qualsiasi oggetto pubblico nell'assembly di personalizzazione che soddisfano determinati requisiti. Per altre informazioni, vedere [memorizzare nella Cache dati](../vsto/caching-data.md).|Tutti i dati XML.|  
|È possibile accedere ai dati senza avviare applicazioni di Microsoft Office?|Sì, usando il <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> classe fornita dal [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)].|Sì, tramite le classi di <xref:System.IO.Packaging> dello spazio dei nomi, o con formato Open XML SDK.|  
  
## <a name="see-also"></a>Vedere anche  
 [Dati nelle soluzioni Office](../vsto/data-in-office-solutions.md)   
 [Architettura delle soluzioni Office in Visual Studio](../vsto/architecture-of-office-solutions-in-visual-studio.md)  
  
  