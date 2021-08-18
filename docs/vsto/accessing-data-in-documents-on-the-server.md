---
title: Accedere ai dati nei documenti nel server
description: Informazioni su come programmare in base ai dati in una personalizzazione a livello di documento senza dover usare il modello a oggetti di Microsoft Office Word o Microsoft Office Excel.
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
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 21723deada493dd5e3d6ab6a16c6dc6366829bbb
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122135572"
---
# <a name="access-data-in-documents-on-the-server"></a>Accedere ai dati nei documenti nel server
  È possibile programmare in base ai dati in una personalizzazione a livello di documento senza dover usare il modello a oggetti di Microsoft Office Word o Microsoft Office Excel. Ciò significa che è possibile accedere ai dati contenuti in un documento in un server in cui non è installato Word Excel. Ad esempio, il codice in un server (ad esempio, in una pagina) può personalizzare i dati in un documento e inviare il documento personalizzato a [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] un utente finale. Quando l'utente finale apre il documento, data binding codice nell'assembly della soluzione associa i dati personalizzati al documento. Ciò è possibile perché i dati nel documento sono separati dall'interfaccia utente. Per altre informazioni, vedere [Dati memorizzati nella cache nelle personalizzazioni a livello di documento.](../vsto/cached-data-in-document-level-customizations.md)

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

## <a name="cache-data-for-use-on-a-server"></a>Memorizzare nella cache i dati da usare in un server
 Per memorizzare nella cache un oggetto dati in un documento, contrassegnarlo con l'attributo in fase di progettazione oppure usare il metodo di un elemento <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> host in fase di `StartCaching` esecuzione. Quando si memorizza nella cache un oggetto dati in un documento, serializza l'oggetto in una [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] stringa XML archiviata nel documento. Gli oggetti devono soddisfare determinati requisiti per essere idonei per la memorizzazione nella cache. Per altre informazioni, vedere [Memorizzare i dati nella cache.](../vsto/caching-data.md)

 Il codice lato server può modificare qualsiasi oggetto dati nella cache dei dati. I controlli associati a istanze di dati memorizzati nella cache vengono sincronizzati con l'interfaccia utente, in modo che tutte le modifiche sul lato server apportate ai dati vengono automaticamente mostrate all'apertura del documento nel client.

## <a name="access-data-in-the-cache"></a>Accedere ai dati nella cache
 È possibile accedere ai dati nella cache da applicazioni esterne Office, ad esempio da un'applicazione console, da un'applicazione Windows Forms o da una pagina Web. L'applicazione che accede ai dati memorizzati nella cache deve avere attendibilità totale. Un'applicazione Web con attendibilità parziale non può inserire, recuperare o modificare i dati memorizzati nella cache in un Office documento.

 La cache dei dati è accessibile tramite una gerarchia di raccolte esposte dalla <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.CachedData%2A> proprietà della <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> classe :

- La <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.CachedData%2A> proprietà restituisce un oggetto che contiene tutti i dati <xref:Microsoft.VisualStudio.Tools.Applications.CachedData> memorizzati nella cache in una personalizzazione a livello di documento.

- Ogni raccolta <xref:Microsoft.VisualStudio.Tools.Applications.CachedData> include uno o più oggetti <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataHostItem>. Un oggetto contiene tutti gli oggetti dati memorizzati nella <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataHostItem> cache definiti all'interno di una singola classe.

- Ogni raccolta <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataHostItem> include uno o più oggetti <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem>. Un <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem> oggetto rappresenta un singolo oggetto dati memorizzato nella cache.

  Nell'esempio di codice seguente viene illustrato come accedere a una stringa memorizzata nella cache nella classe di un `Sheet1` progetto Excel cartella di lavoro. Questo esempio fa parte di un esempio più ampio fornito per il <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.Save%2A> metodo .

  :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_ServerDocument/Form1.cs" id="Snippet12":::
  :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_ServerDocument/Form1.vb" id="Snippet12":::

## <a name="modify-data-in-the-cache"></a>Modificare i dati nella cache
 Per modificare un oggetto dati memorizzato nella cache, in genere si esegue la procedura seguente:

1. Deserializzare la rappresentazione XML dell'oggetto memorizzato nella cache in una nuova istanza dell'oggetto . È possibile accedere al codice XML usando la <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem.Xml%2A> proprietà dell'oggetto <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem> che rappresenta l'oggetto dati memorizzato nella cache.

2. Apportare le modifiche a questa copia.

3. Serializzare nuovamente l'oggetto modificato nella cache dei dati usando una delle opzioni seguenti:

    - Se si desidera serializzare automaticamente le modifiche, usare il <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem.SerializeDataInstance%2A> metodo . Questo metodo usa il **formato DiffGram** per serializzare gli oggetti set di dati <xref:System.Data.DataSet> <xref:System.Data.DataTable> tipizzati , e nella cache dei dati. Il **formato DiffGram** garantisce che le modifiche apportate alla cache dei dati in un documento offline vengano inviate correttamente al server.

    - Se si desidera eseguire la serializzazione personalizzata per le modifiche ai dati memorizzati nella cache, è possibile scrivere direttamente nella <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem.Xml%2A> proprietà . Specificare il **formato DiffGram** se si usa un oggetto per aggiornare un database con le modifiche apportate ai dati in un set di <xref:System.Data.Common.DataAdapter> dati <xref:System.Data.DataSet> <xref:System.Data.DataTable> tipizzato , o . In caso contrario, <xref:System.Data.Common.DataAdapter> aggiornerà il database aggiungendo nuove righe anziché modificando le righe esistenti.

### <a name="modify-data-without-deserializing-the-current-value"></a>Modificare i dati senza deserializzare il valore corrente
 In alcuni casi, potrebbe essere necessario modificare il valore dell'oggetto memorizzato nella cache senza prima deserializzare il valore corrente. Ad esempio, è possibile eseguire questa operazione se si modifica il valore di un oggetto con un tipo semplice, ad esempio una stringa o un numero intero, o se si sta inizializzando un oggetto memorizzato nella cache in un documento in un <xref:System.Data.DataSet> server. In questi casi, è possibile usare il <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem.SerializeDataInstance%2A> metodo senza prima deserializzare il valore corrente dell'oggetto memorizzato nella cache.

 Nell'esempio di codice seguente viene illustrato come modificare il valore di una stringa memorizzata nella cache nella classe di un `Sheet1` progetto Excel cartella di lavoro. Questo esempio fa parte di un esempio più ampio fornito per il <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.Save%2A> metodo .

 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_ServerDocument/Form1.cs" id="Snippet11":::
 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_ServerDocument/Form1.vb" id="Snippet11":::

### <a name="modify-null-values-in-the-data-cache"></a>Modificare i valori Null nella cache dei dati
 La cache dei dati non archivia gli oggetti con valore **Null** quando il documento viene salvato e chiuso. Questa limitazione ha diverse conseguenze quando si modificano i dati memorizzati nella cache:

- Se si imposta un oggetto nella cache dei dati sul valore **null**, tutti gli oggetti nella cache di dati verranno automaticamente impostati su **Null** all'apertura del documento e l'intera cache dei dati verrà cancellata quando il documento viene salvato e chiuso. Ciò significa che tutti gli oggetti memorizzati nella cache verranno rimossi dalla cache dei dati e la <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.CachedData%2A> raccolta sarà vuota.

- Se si compila una soluzione con oggetti **Null** nella cache dei dati e si desidera inizializzare questi oggetti usando la classe prima che il documento venga aperto per la prima volta, è necessario assicurarsi di inizializzare tutti gli oggetti nella cache dei <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> dati. Se si inizializzano solo alcuni oggetti , tutti gli oggetti verranno impostati su **Null** all'apertura del documento e l'intera cache dei dati verrà cancellata quando il documento viene salvato e chiuso.

## <a name="access-typed-datasets-in-the-cache"></a>Accedere ai set di dati tipizzati nella cache
 Se si desidera accedere ai dati in un set di dati tipizzato sia da una soluzione Office che da un'applicazione esterna a Office, ad esempio un'applicazione Windows Forms o un progetto, è necessario definire il set di dati tipizzato in un assembly separato a cui viene fatto riferimento in entrambi i [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] progetti. Se si aggiunge il set di dati  tipizzato a ogni progetto usando la Configurazione guidata origine dati o **Progettazione DataSet**, il .NET Framework tratterà i set di dati tipizzati nei due progetti come tipi diversi. Per altre informazioni sulla creazione di set di dati tipizzati, vedere Creare e configurare set di [dati in Visual Studio](../data-tools/create-and-configure-datasets-in-visual-studio.md).

## <a name="see-also"></a>Vedi anche

- [Accedere ai dati nei documenti nel server](../vsto/accessing-data-in-documents-on-the-server.md)
- [Dati memorizzati nella cache nelle personalizzazioni a livello di documento](../vsto/cached-data-in-document-level-customizations.md)