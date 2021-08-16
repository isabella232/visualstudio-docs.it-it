---
title: Dati cache
description: Informazioni su come memorizzare nella cache gli oggetti dati in una personalizzazione a livello di documento in modo che sia possibile accedere ai dati offline o senza aprire Microsoft Office Word o Excel.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 547c2be11a2c52baf7d5d2c7d3ac1be4b06ed5999d3bb16e3e626c37ba3eed9b
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121384548"
---
# <a name="cache-data"></a>Dati cache
  È possibile memorizzare nella cache gli oggetti dati in una personalizzazione a livello di documento in modo che sia possibile accedere ai dati offline o senza aprire Microsoft Office Word o Microsoft Office Excel. Per memorizzare nella cache un oggetto, l'oggetto deve avere un tipo di dati che soddisfi determinati requisiti. Molti tipi di dati comuni nel .NET Framework soddisfano questi requisiti, tra cui <xref:System.String> <xref:System.Data.DataSet> , e <xref:System.Data.DataTable> .

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 Esistono due modi per aggiungere un oggetto alla cache dei dati:

- Per aggiungere un oggetto alla cache dei dati quando viene compilata la soluzione, applicare <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> l'attributo alla dichiarazione dell'oggetto. Per altre informazioni, vedere [Procedura: Memorizzare nella cache i dati per l'uso offline o in un server](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md).

- Per aggiungere un oggetto alla cache dei dati a livello di codice in fase di esecuzione, usare il metodo di un elemento host, ad esempio `StartCaching` le `ThisDocument` classi o `ThisWorkbook` . Per altre informazioni, vedere [Procedura: Memorizzare](../vsto/how-to-programmatically-cache-a-data-source-in-an-office-document.md)nella cache a livello di codice un'origine dati in un Office documento .

  Dopo aver aggiunto un oggetto alla cache dei dati, è possibile accedere ai dati memorizzati nella cache e modificarli senza avviare Word o Excel. Per altre informazioni, vedere [Accedere ai dati nei documenti nel server](../vsto/accessing-data-in-documents-on-the-server.md).

## <a name="requirements-for-data-objects-to-be-cached"></a>Requisiti per la memorizzazione nella cache degli oggetti dati
 Per memorizzare nella cache un oggetto dati nella soluzione, l'oggetto deve soddisfare i requisiti seguenti:

- Essere un campo pubblico di lettura/scrittura o una proprietà di un elemento host, ad esempio le `ThisDocument` classi o `ThisWorkbook` .

- Non essere un indicizzatore o un'altra proprietà con parametri.

  Inoltre, l'oggetto dati deve essere serializzabile dalla classe , ovvero il tipo dell'oggetto <xref:System.Xml.Serialization.XmlSerializer> deve avere le caratteristiche seguenti:

- Essere un tipo pubblico.

- Avere un costruttore pubblico senza parametri.

- Non eseguire codice che richiede privilegi di sicurezza aggiuntivi.

- Esporre solo proprietà pubbliche di lettura/scrittura (altre proprietà verranno ignorate).

- Non esporre matrici multidimensionali (le matrici annidate sono accettate).

- Non restituiscono interfacce da proprietà e campi.

- Non implementare <xref:System.Collections.IDictionary> se una raccolta.

  Quando si memorizza nella cache un oggetto dati, serializza l'oggetto in una stringa XML archiviata in una [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] *parte XML* personalizzata del documento. Per altre informazioni, vedere [Panoramica delle parti XML personalizzate.](../vsto/custom-xml-parts-overview.md)

## <a name="cached-data-size-limits"></a>Limiti delle dimensioni dei dati memorizzati nella cache
 Esistono alcuni limiti alla quantità totale di dati che è possibile aggiungere alla cache dei dati in un documento e alle dimensioni di qualsiasi singolo oggetto nella cache dei dati. Se si superano questi limiti, l'applicazione potrebbe chiudersi in modo imprevisto quando i dati vengono salvati nella cache dei dati.

 Per evitare questi limiti, seguire queste linee guida:

- Non aggiungere oggetti di dimensioni superiori a 10 MB alla cache dei dati.

- Non aggiungere più di 100 MB di dati totali alla cache dei dati in un singolo documento.

  Si tratta di valori approssimativi. I limiti esatti dipendono da diversi fattori, tra cui la RAM disponibile e il numero di processi in esecuzione.

## <a name="control-the-behavior-of-cached-objects"></a>Controllare il comportamento degli oggetti memorizzati nella cache
 Per ottenere un maggiore controllo sul comportamento di un oggetto memorizzato nella cache, è possibile implementare l'interfaccia <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.ICachedType> sul tipo dell'oggetto memorizzato nella cache. Ad esempio, è possibile implementare questa interfaccia se si vuole controllare la modalità di notifica all'utente quando l'oggetto è stato modificato. Per esempi di codice che illustrano come implementare , vedere la classe nell'esempio di controlli dinamici di Excel e nell'esempio di controlli dinamici di Word in Office di sviluppo e <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.ICachedType> `ControlCollection` procedure [dettagliate](../vsto/office-development-samples-and-walkthroughs.md).

## <a name="persist-changes-to-cached-data-in-password-protected-documents"></a>Rendere persistenti le modifiche ai dati memorizzati nella cache nei documenti protetti da password
 Se si memorizzano nella cache oggetti dati in un documento protetto con una password, le modifiche ai dati memorizzati nella cache non vengono salvate. È possibile salvare le modifiche ai dati memorizzati nella cache eseguendo l'override di due metodi. Eseguire l'override di questi metodi per rimuovere temporaneamente la protezione quando il documento viene salvato e quindi riapplicare la protezione al termine dell'operazione di salvataggio.

 Per altre informazioni, vedere [Procedura: Memorizzare nella cache i dati in un documento protetto da password.](../vsto/how-to-cache-data-in-a-password-protected-document.md)

## <a name="prevent-data-loss-when-adding-null-values-to-the-data-cache"></a>Evitare la perdita di dati quando si aggiungono valori Null alla cache dei dati
 Quando si aggiungono oggetti alla cache dei dati, tutti gli oggetti memorizzati nella cache devono essere inizializzati su un valore diverso da **Null** prima che il documento venga salvato e chiuso. Se un oggetto memorizzato nella cache ha un valore **Null** quando il documento viene salvato e chiuso, rimuoverà automaticamente tutti gli oggetti memorizzati nella [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] cache dei dati.

 Se si aggiunge un oggetto con un valore **Null** alla cache dei dati usando l'attributo in fase di progettazione, è possibile usare la classe per inizializzare gli oggetti dati memorizzati nella cache prima dell'apertura <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> del <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> documento. Ciò è utile se si vogliono inizializzare i dati memorizzati nella cache in un server senza Word o Excel installato, prima che il documento venga aperto da un utente finale. Per altre informazioni, vedere [Accedere ai dati nei documenti nel server](../vsto/accessing-data-in-documents-on-the-server.md).

## <a name="see-also"></a>Vedi anche
- [Procedura: Memorizzare nella cache i dati da usare offline o in un server](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md)
- [Procedura: Memorizzare nella cache un'origine dati in un documento Office codice](../vsto/how-to-programmatically-cache-a-data-source-in-an-office-document.md)
- [Procedura: Memorizzare nella cache i dati in un documento protetto da password](../vsto/how-to-cache-data-in-a-password-protected-document.md)
- [Procedura dettagliata: Creare una relazione master dettagliata usando un set di dati memorizzato nella cache](../vsto/walkthrough-creating-a-master-detail-relation-using-a-cached-dataset.md)
