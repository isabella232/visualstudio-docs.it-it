---
title: Accedere ai dati nei documenti sul server
description: Informazioni su come è possibile programmare i dati in una personalizzazione a livello di documento senza dover usare il modello a oggetti di Microsoft Office Word o Microsoft Office Excel.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data [Office development in Visual Studio], accessing on server
- data access [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 1c610bdc33564e3e211d1ec5aab943af4eec49d1
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99965798"
---
# <a name="access-data-in-documents-on-the-server"></a>Accedere ai dati nei documenti sul server
  È possibile programmare in base ai dati in una personalizzazione a livello di documento senza dover usare il modello a oggetti di Microsoft Office Word o Microsoft Office Excel. Ciò significa che è possibile accedere ai dati contenuti in un documento in un server in cui non è installato Word o Excel. Ad esempio, il codice in un server, ad esempio in una [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] pagina, può personalizzare i dati in un documento e inviare il documento personalizzato a un utente finale. Quando l'utente finale apre il documento, data binding codice nell'assembly della soluzione associa i dati personalizzati al documento. Questa operazione è possibile perché i dati nel documento sono separati dall'interfaccia utente. Per ulteriori informazioni, vedere la pagina relativa ai [dati memorizzati nella cache nelle personalizzazioni a livello di documento](../vsto/cached-data-in-document-level-customizations.md).

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

## <a name="cache-data-for-use-on-a-server"></a>Memorizzare nella cache i dati da utilizzare in un server
 Per memorizzare nella cache un oggetto dati in un documento, contrassegnarlo con l' <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> attributo in fase di progettazione oppure utilizzare il `StartCaching` metodo di un elemento host in fase di esecuzione. Quando si memorizza nella cache un oggetto dati in un documento, l' [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] oggetto viene serializzato in una stringa XML archiviata nel documento. Gli oggetti devono soddisfare determinati requisiti per essere idonei per la memorizzazione nella cache. Per altre informazioni, vedere [memorizzare i dati nella cache](../vsto/caching-data.md).

 Il codice lato server può modificare qualsiasi oggetto dati nella cache dei dati. I controlli associati alle istanze di dati memorizzate nella cache vengono sincronizzati con l'interfaccia utente, in modo che tutte le modifiche sul lato server apportate ai dati vengano visualizzate automaticamente quando il documento viene aperto nel client.

## <a name="access-data-in-the-cache"></a>Accedere ai dati nella cache
 È possibile accedere ai dati nella cache da applicazioni esterne a Office, ad esempio da un'applicazione console, da un Windows Forms Application o da una pagina Web. L'applicazione che accede ai dati memorizzati nella cache deve avere l'attendibilità totale; un'applicazione Web con attendibilità parziale non è in grado di inserire, recuperare o modificare i dati memorizzati nella cache di un documento di Office.

 La cache dei dati è accessibile tramite una gerarchia di raccolte esposte dalla <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.CachedData%2A> proprietà della <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> classe:

- La <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.CachedData%2A> proprietà restituisce un oggetto <xref:Microsoft.VisualStudio.Tools.Applications.CachedData> che contiene tutti i dati memorizzati nella cache in una personalizzazione a livello di documento.

- Ogni raccolta <xref:Microsoft.VisualStudio.Tools.Applications.CachedData> include uno o più oggetti <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataHostItem>. Un oggetto <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataHostItem> contiene tutti gli oggetti dati memorizzati nella cache che sono definiti all'interno di una singola classe.

- Ogni raccolta <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataHostItem> include uno o più oggetti <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem>. Un <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem> oggetto rappresenta un singolo oggetto dati memorizzato nella cache.

  Nell'esempio di codice seguente viene illustrato come accedere a una stringa memorizzata nella cache nella `Sheet1` classe di un progetto di cartella di lavoro di Excel. Questo esempio fa parte di un esempio più ampio fornito per il <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.Save%2A> metodo.

  [!code-csharp[Trin_ServerDocument#12](../vsto/codesnippet/CSharp/Trin_ServerDocument/Form1.cs#12)]
  [!code-vb[Trin_ServerDocument#12](../vsto/codesnippet/VisualBasic/Trin_ServerDocument/Form1.vb#12)]

## <a name="modify-data-in-the-cache"></a>Modificare i dati nella cache
 Per modificare un oggetto dati memorizzato nella cache, in genere si eseguono i passaggi seguenti:

1. Deserializzare la rappresentazione XML dell'oggetto memorizzato nella cache in una nuova istanza dell'oggetto. È possibile accedere al codice XML utilizzando la <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem.Xml%2A> proprietà dell' <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem> oggetto che rappresenta l'oggetto dati memorizzato nella cache.

2. Apportare le modifiche a questa copia.

3. Serializzare nuovamente l'oggetto modificato nella cache dei dati utilizzando una delle opzioni seguenti:

    - Se si desidera serializzare automaticamente le modifiche, utilizzare il <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem.SerializeDataInstance%2A> metodo. Questo metodo utilizza il formato **DiffGram** per la serializzazione di <xref:System.Data.DataSet> <xref:System.Data.DataTable> oggetti DataSet tipizzati, e nella cache dei dati. Il formato **DiffGram** garantisce che le modifiche apportate alla cache dei dati in un documento offline vengano inviate al server in modo corretto.

    - Se si desidera eseguire la serializzazione personalizzata per le modifiche ai dati memorizzati nella cache, è possibile scrivere direttamente nella <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem.Xml%2A> Proprietà. Specificare il formato **DiffGram** se si utilizza un <xref:System.Data.Common.DataAdapter> per aggiornare un database con le modifiche apportate ai dati in un <xref:System.Data.DataSet> <xref:System.Data.DataTable> DataSet tipizzato, o. In caso contrario, <xref:System.Data.Common.DataAdapter> aggiornerà il database aggiungendo nuove righe anziché modificare quelle esistenti.

### <a name="modify-data-without-deserializing-the-current-value"></a>Modificare i dati senza deserializzare il valore corrente
 In alcuni casi, potrebbe essere necessario modificare il valore dell'oggetto memorizzato nella cache senza prima deserializzare il valore corrente. Questa operazione può essere eseguita, ad esempio, se si modifica il valore di un oggetto che dispone di un tipo semplice, ad esempio una stringa o un Integer, oppure se si Inizializza un oggetto memorizzato nella cache <xref:System.Data.DataSet> di un documento in un server. In questi casi, è possibile usare il <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem.SerializeDataInstance%2A> metodo senza prima deserializzare il valore corrente dell'oggetto memorizzato nella cache.

 Nell'esempio di codice riportato di seguito viene illustrato come modificare il valore di una stringa memorizzata nella cache nella `Sheet1` classe di un progetto di cartella di lavoro di Excel. Questo esempio fa parte di un esempio più ampio fornito per il <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.Save%2A> metodo.

 [!code-csharp[Trin_ServerDocument#11](../vsto/codesnippet/CSharp/Trin_ServerDocument/Form1.cs#11)]
 [!code-vb[Trin_ServerDocument#11](../vsto/codesnippet/VisualBasic/Trin_ServerDocument/Form1.vb#11)]

### <a name="modify-null-values-in-the-data-cache"></a>Modificare i valori null nella cache dei dati
 La cache dei dati non archivia oggetti con valore **null** quando il documento viene salvato e chiuso. Questa limitazione presenta diverse conseguenze quando si modificano i dati memorizzati nella cache:

- Se si imposta un oggetto nella cache dei dati sul valore **null**, tutti gli oggetti nella cache dei dati verranno impostati automaticamente su **null** quando il documento viene aperto e l'intera cache dei dati verrà cancellata quando il documento viene salvato e chiuso. Ovvero, tutti gli oggetti memorizzati nella cache verranno rimossi dalla cache dei dati e la <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.CachedData%2A> raccolta sarà vuota.

- Se si compila una soluzione con oggetti **null** nella cache dei dati e si desidera inizializzare questi oggetti utilizzando la <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> classe prima che il documento venga aperto per la prima volta, è necessario assicurarsi di inizializzare tutti gli oggetti nella cache dei dati. Se si inizializzano solo alcuni oggetti, tutti gli oggetti verranno impostati su **null** quando il documento viene aperto e l'intera cache dei dati verrà cancellata quando il documento viene salvato e chiuso.

## <a name="access-typed-datasets-in-the-cache"></a>Accedere a DataSet tipizzati nella cache
 Se si desidera accedere ai dati in un DataSet tipizzato da una soluzione Office e da un'applicazione esterna a Office, ad esempio un Windows Forms Application o un [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] progetto, è necessario definire il set di dati tipizzato in un assembly separato a cui si fa riferimento in entrambi i progetti. Se si aggiunge il set di dati tipizzato a ogni progetto usando la **Configurazione guidata origine dati** o la **Progettazione DataSet**, il .NET Framework considererà i set di dati tipizzati nei due progetti come tipi diversi. Per altre informazioni sulla creazione di DataSet tipizzati, vedere [creare e configurare set di dati in Visual Studio](../data-tools/create-and-configure-datasets-in-visual-studio.md).

## <a name="see-also"></a>Vedi anche

- [Accedere ai dati nei documenti sul server](../vsto/accessing-data-in-documents-on-the-server.md)
- [Dati memorizzati nella cache nelle personalizzazioni a livello di documento](../vsto/cached-data-in-document-level-customizations.md)