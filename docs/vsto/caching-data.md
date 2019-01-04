---
title: Dati della cache
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data caching [Office development in Visual Studio], about caching data
- data [Office development in Visual Studio], caching
- data caching [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: 66113dae824397f46829a539a016f452cedc0383
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53967255"
---
# <a name="cache-data"></a>Dati della cache
  È possibile memorizzare nella cache di oggetti dati in una personalizzazione a livello di documento in modo che i dati siano accessibili in modalità offline o senza l'apertura di Microsoft Office Word o Microsoft Office Excel. Per memorizzare nella cache un oggetto, l'oggetto deve avere un tipo di dati che soddisfano determinati requisiti. Molti tipi di dati comune in .NET Framework soddisfano questi requisiti, incluse <xref:System.String>, <xref:System.Data.DataSet>, e <xref:System.Data.DataTable>.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 Esistono due modi per aggiungere un oggetto alla cache dei dati:  
  
- Per aggiungere un oggetto alla cache dei dati durante la compilazione della soluzione, applicare il <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> dell'attributo di dichiarazione dell'oggetto. Per altre informazioni, vedere [Procedura: Memorizzare nella cache i dati per l'uso offline o in un server](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md).  
  
- Per aggiungere a livello di codice un oggetto alla cache dei dati in fase di esecuzione, usare il `StartCaching` metodo di un host di elemento, ad esempio il `ThisDocument` o `ThisWorkbook` classi. Per altre informazioni, vedere [Procedura: Memorizzare nella cache a livello di codice di un'origine dati in un documento di Office](../vsto/how-to-programmatically-cache-a-data-source-in-an-office-document.md).  
  
  Dopo aver aggiunto un oggetto alla cache dei dati, è possibile accedere e modificare i dati memorizzati nella cache senza avviare Word o Excel. Per altre informazioni, vedere [accedere ai dati dei documenti sul server](../vsto/accessing-data-in-documents-on-the-server.md).  
  
## <a name="requirements-for-data-objects-to-be-cached"></a>Requisiti per gli oggetti dati da memorizzare nella cache  
 Per memorizzare nella cache un oggetto dati nella soluzione, l'oggetto deve soddisfare questi requisiti:  
  
- Essere un campo pubblico in lettura/scrittura o una proprietà di un elemento host, ad esempio la `ThisDocument` o `ThisWorkbook` classi.  
  
- Non essere un indicizzatore o altra proprietà con parametri.  
  
  Inoltre, l'oggetto dati deve essere serializzabile dal <xref:System.Xml.Serialization.XmlSerializer> (classe), ovvero il tipo dell'oggetto deve avere le seguenti caratteristiche:  
  
- Essere un tipo pubblico.  
  
- Avere un costruttore pubblico senza parametri.  
  
- Non eseguire il codice che richiede privilegi di sicurezza aggiuntive.  
  
- Esporre solo lettura/scrittura proprietà pubbliche (le altre proprietà verranno ignorate).  
  
- Non esporre le matrici multidimensionali (matrici annidate sono accettate).  
  
- Interfacce non restituite dalla proprietà e campi.  
  
- Non implementare <xref:System.Collections.IDictionary> se una raccolta.  
  
  Quando si memorizza nella cache un oggetto dati, il [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] serializza l'oggetto in una stringa XML che viene archiviata in un *parte XML personalizzata* nel documento. Per altre informazioni, vedere [panoramica delle parti XML personalizzate](../vsto/custom-xml-parts-overview.md).  
  
## <a name="cached-data-size-limits"></a>Limiti delle dimensioni dei dati memorizzati nella cache  
 Esistono alcuni limiti alla quantità totale di dati che è possibile aggiungere alla cache dei dati in un documento e per le dimensioni di qualsiasi singolo oggetto nella cache dei dati. Se si superano questi limiti, l'applicazione potrebbe chiudersi inaspettatamente quando i dati vengono salvati nella cache dei dati.  
  
 Per evitare questi limiti, seguire queste linee guida:  
  
- Non aggiungere alcun oggetto superiore a 10 MB per la cache dei dati.  
  
- Non aggiungere più di 100 MB di dati totali alla cache dei dati in un unico documento.  
  
  Questi sono valori approssimati. I limiti esatti dipendono da diversi fattori, tra cui la quantità di RAM disponibile e il numero di processi in esecuzione.  
  
## <a name="control-the-behavior-of-cached-objects"></a>Controllare il comportamento degli oggetti memorizzati nella cache  
 Per ottenere un maggiore controllo sul comportamento di un oggetto memorizzato nella cache, è possibile implementare il <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.ICachedType> interfaccia del tipo di oggetto memorizzato nella cache. Ad esempio, è possibile implementare questa interfaccia se si desidera controllare come l'utente viene informato quando l'oggetto è stato modificato. Per esempi di codice che illustrano come implementare <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.ICachedType>, vedere la `ControlCollection` classe nell'esempio di controlli dinamici Excel e Word esempio di controlli dinamici nel [procedure dettagliate ed esempi di sviluppo per Office](../vsto/office-development-samples-and-walkthroughs.md).  
  
## <a name="persist-changes-to-cached-data-in-password-protected-documents"></a>Rendere persistenti le modifiche ai dati memorizzati nella cache i documenti protetti da password  
 Se si memorizza nella cache gli oggetti dati in un documento protetto con una password, non vengono salvate le modifiche ai dati memorizzati nella cache. È possibile salvare le modifiche apportate ai dati memorizzati nella cache eseguendo l'override di due metodi. Eseguire l'override di questi metodi per rimuovere temporaneamente la protezione quando il documento viene salvato e quindi riapplicare la protezione dopo il salvataggio operazione è stata completata.  
  
 Per altre informazioni, vedere [Procedura: Memorizzare nella cache i dati in un documento protetto da password](../vsto/how-to-cache-data-in-a-password-protected-document.md).  
  
## <a name="prevent-data-loss-when-adding-null-values-to-the-data-cache"></a>Evitare perdite di dati durante l'aggiunta di valori null per la cache dei dati  
 Quando si aggiungono oggetti alla cache dei dati, tutti gli oggetti memorizzati nella cache deve essere inizializzati a non -**null** valore prima che il documento viene salvato e chiuso. Se un oggetto memorizzato nella cache contiene un **null** valore quando il documento viene salvato e chiuso, il [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] rimuoverà automaticamente tutti gli oggetti memorizzati nella cache dalla cache dei dati.  
  
 Se si aggiunge un oggetto con un **null** valore alla cache dei dati tramite il <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> attributo in fase di progettazione, è possibile usare il <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> gli oggetti classe per inizializzare i dati memorizzati nella cache prima che il documento viene aperto. Ciò è utile se si desidera inizializzare i dati memorizzati nella cache in un server senza Word o Excel, prima che il documento viene aperto da un utente finale. Per altre informazioni, vedere [accedere ai dati dei documenti sul server](../vsto/accessing-data-in-documents-on-the-server.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura: Memorizzare nella cache i dati per l'uso offline o in un server](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md)   
 [Procedura: Memorizzare nella cache a livello di codice di un'origine dati in un documento di Office](../vsto/how-to-programmatically-cache-a-data-source-in-an-office-document.md)   
 [Procedura: Dati della cache in un documento protetto da password](../vsto/how-to-cache-data-in-a-password-protected-document.md)   
 [Procedura dettagliata: Creare una relazione master/dettaglio mediante un dataset memorizzato nella cache](../vsto/walkthrough-creating-a-master-detail-relation-using-a-cached-dataset.md)  
