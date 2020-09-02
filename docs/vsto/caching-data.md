---
title: Dati cache
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: c6e0f6d7fcf9920ddb8861712b7c5f8bf04506fc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "62939415"
---
# <a name="cache-data"></a>Dati cache
  È possibile memorizzare nella cache gli oggetti dati in una personalizzazione a livello di documento in modo che sia possibile accedere ai dati offline o senza aprire Microsoft Office Word o Microsoft Office Excel. Per memorizzare nella cache un oggetto, l'oggetto deve avere un tipo di dati che soddisfi determinati requisiti. Molti tipi di dati comuni in .NET Framework soddisfano questi requisiti, tra cui <xref:System.String> , <xref:System.Data.DataSet> e <xref:System.Data.DataTable> .

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 Esistono due modi per aggiungere un oggetto alla cache dei dati:

- Per aggiungere un oggetto alla cache dei dati quando la soluzione viene compilata, applicare l' <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> attributo alla dichiarazione dell'oggetto. Per altre informazioni, vedere [procedura: memorizzare nella cache i dati per l'uso offline o in un server](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md).

- Per aggiungere a livello di codice un oggetto alla cache dei dati in fase di esecuzione, utilizzare il `StartCaching` metodo di un elemento host, ad esempio le `ThisDocument` `ThisWorkbook` classi o. Per altre informazioni, vedere [procedura: memorizzare nella cache a livello di codice un'origine dati in un documento di Office](../vsto/how-to-programmatically-cache-a-data-source-in-an-office-document.md).

  Dopo aver aggiunto un oggetto alla cache di dati, è possibile accedere e modificare i dati memorizzati nella cache senza avviare Word o Excel. Per ulteriori informazioni, vedere [accedere ai dati nei documenti sul server](../vsto/accessing-data-in-documents-on-the-server.md).

## <a name="requirements-for-data-objects-to-be-cached"></a>Requisiti per la memorizzazione nella cache degli oggetti dati
 Per memorizzare nella cache un oggetto dati nella soluzione, è necessario che l'oggetto soddisfi questi requisiti:

- Essere una proprietà o un campo pubblico di lettura/scrittura di un elemento host, ad esempio le `ThisDocument` `ThisWorkbook` classi o.

- Non è un indicizzatore o un'altra proprietà con parametri.

  Inoltre, l'oggetto dati deve essere serializzabile dalla <xref:System.Xml.Serialization.XmlSerializer> classe, il che significa che il tipo dell'oggetto deve avere queste caratteristiche:

- Essere un tipo pubblico.

- Avere un costruttore pubblico senza parametri.

- Non eseguire codice che richiede privilegi di sicurezza aggiuntivi.

- Esporre solo le proprietà pubbliche di lettura/scrittura (altre proprietà verranno ignorate).

- Non esporre matrici multidimensionali (sono accettate matrici annidate).

- Non restituiscono interfacce da proprietà e campi.

- Non implementare <xref:System.Collections.IDictionary> se una raccolta.

  Quando si memorizza nella cache un oggetto dati, il [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] serializza l'oggetto in una stringa XML archiviata in una *parte XML personalizzata* del documento. Per ulteriori informazioni, vedere [Cenni preliminari sulle parti XML personalizzate](../vsto/custom-xml-parts-overview.md).

## <a name="cached-data-size-limits"></a>Limiti per le dimensioni dei dati memorizzati nella cache
 Sono previsti alcuni limiti per la quantità totale di dati che è possibile aggiungere alla cache di dati in un documento e per le dimensioni di un singolo oggetto nella cache dei dati. Se si superano questi limiti, è possibile che l'applicazione si chiuda in modo imprevisto quando i dati vengono salvati nella cache dei dati.

 Per evitare questi limiti, attenersi alle seguenti linee guida:

- Non aggiungere alla cache dei dati alcun oggetto di dimensioni superiori a 10 MB.

- Non aggiungere più di 100 MB di dati totali alla cache dei dati in un singolo documento.

  Si tratta di valori approssimativi. I limiti esatti dipendono da diversi fattori, tra cui la RAM disponibile e il numero di processi in esecuzione.

## <a name="control-the-behavior-of-cached-objects"></a>Controllare il comportamento degli oggetti memorizzati nella cache
 Per ottenere un maggiore controllo sul comportamento di un oggetto memorizzato nella cache, è possibile implementare l' <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.ICachedType> interfaccia sul tipo di oggetto memorizzato nella cache. Ad esempio, è possibile implementare questa interfaccia se si desidera controllare la modalità con cui l'utente riceve una notifica quando l'oggetto è stato modificato. Per esempi di codice che illustrano come implementare <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.ICachedType> , vedere la classe nell'esempio relativo ai `ControlCollection` controlli dinamici di Excel e controlli dinamici di Word negli [esempi e nelle procedure dettagliate per lo sviluppo di Office](../vsto/office-development-samples-and-walkthroughs.md).

## <a name="persist-changes-to-cached-data-in-password-protected-documents"></a>Salvare in modo permanente le modifiche ai dati memorizzati nella cache nei documenti protetti da password
 Se si memorizzano nella cache oggetti dati in un documento protetto con una password, le modifiche apportate ai dati memorizzati nella cache non vengono salvate. È possibile salvare le modifiche apportate ai dati memorizzati nella cache eseguendo l'override di due metodi. Eseguire l'override di questi metodi per rimuovere temporaneamente la protezione quando il documento viene salvato e quindi riapplicare la protezione dopo che l'operazione di salvataggio è stata completata.

 Per altre informazioni, vedere [procedura: memorizzare nella cache i dati in un documento protetto da password](../vsto/how-to-cache-data-in-a-password-protected-document.md).

## <a name="prevent-data-loss-when-adding-null-values-to-the-data-cache"></a>Prevenire la perdita di dati durante l'aggiunta di valori null alla cache dei dati
 Quando si aggiungono oggetti alla cache dei dati, tutti gli oggetti memorizzati nella cache devono essere inizializzati su un valore non**null** prima che il documento venga salvato e chiuso. Se un oggetto memorizzato nella cache ha un valore **null** quando il documento viene salvato e chiuso, [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] rimuove automaticamente tutti gli oggetti memorizzati nella cache dalla cache dei dati.

 Se si aggiunge un oggetto con un valore **null** alla cache dei dati utilizzando l' <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> attributo in fase di progettazione, è possibile utilizzare la <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> classe per inizializzare gli oggetti dati memorizzati nella cache prima dell'apertura del documento. Questa opzione è utile se si desidera inizializzare i dati memorizzati nella cache in un server senza installazione di Word o Excel, prima che il documento venga aperto da un utente finale. Per ulteriori informazioni, vedere [accedere ai dati nei documenti sul server](../vsto/accessing-data-in-documents-on-the-server.md).

## <a name="see-also"></a>Vedere anche
- [Procedura: memorizzare nella cache i dati per l'uso offline o su un server](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md)
- [Procedura: memorizzare nella cache a livello di codice un'origine dati in un documento di Office](../vsto/how-to-programmatically-cache-a-data-source-in-an-office-document.md)
- [Procedura: memorizzare nella cache i dati in un documento protetto da password](../vsto/how-to-cache-data-in-a-password-protected-document.md)
- [Procedura dettagliata: creare una relazione di dettaglio master usando un set di dati memorizzato nella cache](../vsto/walkthrough-creating-a-master-detail-relation-using-a-cached-dataset.md)
