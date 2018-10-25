---
title: Accedere ai dati in documenti sul server
ms.custom: ''
ms.date: 02/02/2017
ms.technology: office-development
ms.prod: visual-studio-dev15
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data [Office development in Visual Studio], accessing on server
- data access [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 3d894c033d466d84409c46a2d2849650bf32a119
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49870302"
---
# <a name="access-data-in-documents-on-the-server"></a>Accedere ai dati in documenti sul server
  È possibile programmare i dati in una personalizzazione a livello di documento senza dover usare il modello a oggetti di Microsoft Office Word o Microsoft Office Excel. Ciò significa che è possibile accedere ai dati contenuti in un documento in un server che è privo di Word o Excel installato. Esempio di codice in un server (ad esempio, in un [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] pagina) possono personalizzare i dati in un documento e inviare il documento personalizzato per un utente finale. Quando l'utente finale apre il documento, il codice di associazione dati nell'assembly della soluzione associa i dati personalizzati nel documento. Ciò è possibile perché i dati del documento sono separati dall'interfaccia utente. Per altre informazioni, vedere [memorizzato nella cache i dati nelle personalizzazioni a livello di documento](../vsto/cached-data-in-document-level-customizations.md).  

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  

## <a name="cache-data-for-use-on-a-server"></a>Memorizzare nella cache i dati da usare in un server  
 Per memorizzare nella cache un oggetto dati in un documento, contrassegnarlo con il <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> dell'attributo in fase di progettazione oppure usare il `StartCaching` metodo di un elemento host in fase di esecuzione. Quando si memorizza nella cache un oggetto dati in un documento, il [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] serializza l'oggetto in una stringa XML che viene archiviata nel documento. Gli oggetti devono soddisfare determinati requisiti per essere idoneo per la memorizzazione nella cache. Per altre informazioni, vedere [memorizzare nella Cache dati](../vsto/caching-data.md).  

 Il codice lato server può modificare tutti gli oggetti dati nella cache dei dati. Controlli associati alle istanze di dati memorizzati nella cache vengono sincronizzati con l'interfaccia utente, in modo che eventuali modifiche sul lato server che vengono apportate ai dati vengono visualizzate automaticamente quando il documento viene aperto nel client.  

## <a name="access-data-in-the-cache"></a>Accedere ai dati nella cache  
 È possibile accedere a dati memorizzati nella cache dalle applicazioni all'esterno dell'ufficio, ad esempio da un'applicazione console, un'applicazione Windows Forms o una pagina Web. L'applicazione che accede ai dati memorizzati nella cache deve avere l'attendibilità totale; un'applicazione Web con attendibilità parziale non può inserire, recuperare o modificare i dati memorizzati nella cache in un documento di Office.  

 La cache dei dati è accessibile tramite una gerarchia delle raccolte esposte dal <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.CachedData%2A> proprietà del <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> classe:  

- Il <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.CachedData%2A> proprietà restituisce un <xref:Microsoft.VisualStudio.Tools.Applications.CachedData>, che contiene tutti i dati memorizzati in una personalizzazione a livello di documento.  

- Ciascuna <xref:Microsoft.VisualStudio.Tools.Applications.CachedData> contiene uno o più <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataHostItem> oggetti. Oggetto <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataHostItem> contiene tutti gli oggetti dati memorizzati nella cache che vengono definiti all'interno di una singola classe.  

- Ciascuna <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataHostItem> contiene uno o più <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem> oggetti. Oggetto <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem> rappresenta un singolo oggetto dati memorizzato.  

  Esempio di codice seguente viene illustrato come accedere a una stringa memorizzata nella cache il `Sheet1` classe di un progetto cartella di lavoro di Excel. Questo esempio fa parte di un esempio più esaustivo fornito per il <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.Save%2A> (metodo).  

  [!code-csharp[Trin_ServerDocument#12](../vsto/codesnippet/CSharp/Trin_ServerDocument/Form1.cs#12)]
  [!code-vb[Trin_ServerDocument#12](../vsto/codesnippet/VisualBasic/Trin_ServerDocument/Form1.vb#12)]  

## <a name="modify-data-in-the-cache"></a>Modificare i dati nella cache  
 Per modificare un oggetto dati memorizzati nella cache, è in genere necessario eseguire i passaggi seguenti:  

1.  Deserializzare la rappresentazione XML dell'oggetto memorizzato nella cache in una nuova istanza dell'oggetto. È possibile accedere al codice XML tramite il <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem.Xml%2A> proprietà del <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem> che rappresenta l'oggetto dati memorizzati nella cache.  

2.  Apportare le modifiche apportate a tale copia.  

3.  Serializzare l'oggetto modificato nuovamente nella cache i dati usando una delle opzioni seguenti:  

    -   Se si vuole serializzare automaticamente le modifiche, usare il <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem.SerializeDataInstance%2A> (metodo). Questo metodo Usa il **DiffGram** formato per la serializzazione <xref:System.Data.DataSet>, <xref:System.Data.DataTable>e gli oggetti dataset tipizzati nella cache dei dati. Il **DiffGram** formato garantisce che le modifiche alla cache dei dati in un documento non in linea vengono inviate correttamente al server.  

    -   Se si desidera eseguire la serializzazione personalizzata per le modifiche ai dati memorizzati nella cache, è possibile scrivere direttamente i <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem.Xml%2A> proprietà. Specificare il **DiffGram** formattare se si usa un <xref:System.Data.Common.DataAdapter> per aggiornare un database con le modifiche apportate ai dati in un <xref:System.Data.DataSet>, <xref:System.Data.DataTable>, o un dataset tipizzato. In caso contrario, il <xref:System.Data.Common.DataAdapter> aggiornerà il database mediante l'aggiunta di nuove righe invece di modificare le righe esistenti.  

### <a name="modify-data-without-deserializing-the-current-value"></a>Modificare i dati senza deserializzare il valore corrente  
 In alcuni casi, si potrebbe voler modificare il valore dell'oggetto memorizzato nella cache senza prima di deserializzare il valore corrente. Ad esempio, è possibile eseguire questa operazione se si modifica il valore di un oggetto che ha un tipo semplice, ad esempio una stringa o numero intero, o se si inizializza un oggetto nella cache <xref:System.Data.DataSet> in un documento in un server. In questi casi, è possibile usare il <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem.SerializeDataInstance%2A> metodo senza prima di deserializzare il valore corrente dell'oggetto memorizzato nella cache.  

 Esempio di codice seguente viene illustrato come modificare il valore di una stringa memorizzata nella cache il `Sheet1` classe di un progetto cartella di lavoro di Excel. Questo esempio fa parte di un esempio più esaustivo fornito per il <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.Save%2A> (metodo).  

 [!code-csharp[Trin_ServerDocument#11](../vsto/codesnippet/CSharp/Trin_ServerDocument/Form1.cs#11)]
 [!code-vb[Trin_ServerDocument#11](../vsto/codesnippet/VisualBasic/Trin_ServerDocument/Form1.vb#11)]  

### <a name="modify-null-values-in-the-data-cache"></a>Modificare i valori null nella cache dei dati  
 La cache dei dati non archivia gli oggetti che dispongono del valore **null** quando il documento viene salvato e chiuso. Quando si modificano i dati memorizzati nella cache, questa limitazione ha diverse conseguenze:  

-   Se è impostato alcun oggetto nella cache dei dati per il valore **null**, tutti gli oggetti nella cache dei dati verrà automaticamente impostati su **null** quando il documento viene aperto e la cache di tutti i dati verrà cancellata quando il documento viene salvato e chiuso. Vale a dire tutti gli oggetti memorizzati nella cache verrà rimosso dalla cache dei dati e il <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.CachedData%2A> raccolta sarà vuota.  

-   Se si compila una soluzione con **null** gli oggetti nella cache dei dati e si desidera inizializzare questi oggetti usando il <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> classe prima che il documento viene aperto per la prima volta, è necessario assicurarsi che si inizializza tutti gli oggetti nella cache dei dati. Se si inizializza solo alcuni degli oggetti, tutti gli oggetti verrà impostati su **null** quando il documento viene aperto e verrà cancellata la cache di tutti i dati quando il documento viene salvato e chiuso.  

## <a name="access-typed-datasets-in-the-cache"></a>Set di dati tipizzati di accesso nella cache  
 Se si desidera accedere ai dati in un dataset tipizzato da una soluzione Office e da un'applicazione all'esterno dell'ufficio, ad esempio un'applicazione Windows Forms o un [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] progetto, è necessario definire il set di dati tipizzato in un assembly separato a cui viene fatto riferimento in entrambi progetti. Se aggiungere a ogni progetto dataset tipizzato utilizzando il **configurazione dell'origine dati** guidata o nella **Progettazione Dataset**, .NET Framework considera i dataset tipizzati nei due progetti come tipi diversi . Per altre informazioni sulla creazione di dataset tipizzati, vedere [creare e configurare i set di dati in Visual Studio](/visualstudio/data-tools/create-and-configure-datasets-in-visual-studio).  

## <a name="see-also"></a>Vedere anche  
 [Accedere ai dati in documenti sul server](../vsto/accessing-data-in-documents-on-the-server.md)   
 [Dati memorizzati nella cache nelle personalizzazioni a livello di documento](../vsto/cached-data-in-document-level-customizations.md)  
