---
title: Accedere ai dati dei documenti sul server
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
ms.openlocfilehash: ecfebda02096d1a36a5de84919aad65482a25ec0
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/17/2018
ms.locfileid: "34268390"
---
# <a name="access-data-in-documents-on-the-server"></a>Accedere ai dati dei documenti sul server
  È possibile programmare i dati in una personalizzazione a livello di documento senza la necessità di utilizzare il modello a oggetti di Microsoft Office Word o Microsoft Office Excel. Ciò significa che è possibile accedere ai dati contenuti in un documento in un server che non dispone di Word o Excel installato. Esempio di codice in un server (ad esempio, in un [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] pagina) possono personalizzare i dati in un documento e inviare il documento personalizzato a un utente finale. Quando l'utente finale apre il documento, il codice di associazione di dati nell'assembly della soluzione Associa dati personalizzati nel documento. Questo è possibile perché i dati nel documento sono separatati dall'interfaccia utente. Per altre informazioni, vedere [memorizzato nella cache i dati nelle personalizzazioni a livello di documento](../vsto/cached-data-in-document-level-customizations.md).  

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  

## <a name="cache-data-for-use-on-a-server"></a>Memorizzare nella cache i dati da utilizzare in un server  
 Per memorizzare nella cache un oggetto dati in un documento, contrassegnarlo con il <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> dell'attributo in fase di progettazione oppure utilizzare il `StartCaching` metodo di un elemento host in fase di esecuzione. Quando si memorizza nella cache un oggetto dati in un documento, il [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] serializza l'oggetto in una stringa XML che viene archiviata nel documento. Gli oggetti devono soddisfare determinati requisiti per essere idoneo per la memorizzazione nella cache. Per altre informazioni, vedere [memorizzare nella Cache dati](../vsto/caching-data.md).  

 Il codice lato server è possibile modificare tutti gli oggetti dati nella cache dei dati. Controlli associati a dati memorizzati nella cache istanze sono sincronizzati con l'interfaccia utente, in modo che le modifiche sul lato server effettuate per i dati vengono visualizzate automaticamente quando il documento viene aperto nel client.  

## <a name="access-data-in-the-cache"></a>Accedere ai dati nella cache  
 È possibile accedere a dati memorizzati nella cache dalle applicazioni all'esterno dell'ufficio, ad esempio da un'applicazione console, un'applicazione Windows Form o una pagina Web. L'applicazione che accede ai dati memorizzati nella cache deve avere l'attendibilità totale; un'applicazione Web con attendibilità parziale non può inserire, recuperare o modificare i dati memorizzati nella cache in un documento di Office.  

 La cache dei dati è accessibile tramite una gerarchia delle raccolte esposte dal <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.CachedData%2A> proprietà la <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> classe:  

-   Il <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.CachedData%2A> proprietà restituisce un <xref:Microsoft.VisualStudio.Tools.Applications.CachedData>, che contiene tutti i dati memorizzati nella cache in una personalizzazione a livello di documento.  

-   Ogni <xref:Microsoft.VisualStudio.Tools.Applications.CachedData> contiene uno o più <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataHostItem> oggetti. Oggetto <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataHostItem> contiene tutti gli oggetti dati memorizzati nella cache definiti all'interno di una singola classe.  

-   Ogni <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataHostItem> contiene uno o più <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem> oggetti. Oggetto <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem> rappresenta un oggetto solo dati memorizzati nella cache.  

 Esempio di codice riportato di seguito viene illustrato come accedere a una stringa memorizzata nella cache il `Sheet1` classe di un progetto cartella di lavoro di Excel. Questo esempio fa parte di un esempio più ampio fornito per il <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.Save%2A> metodo.  

 [!code-csharp[Trin_ServerDocument#12](../vsto/codesnippet/CSharp/Trin_ServerDocument/Form1.cs#12)]
 [!code-vb[Trin_ServerDocument#12](../vsto/codesnippet/VisualBasic/Trin_ServerDocument/Form1.vb#12)]  

## <a name="modify-data-in-the-cache"></a>Modificare i dati nella cache  
 Per modificare un oggetto dati memorizzati nella cache, è in genere necessario eseguire i passaggi seguenti:  

1.  Deserializzare la rappresentazione XML dell'oggetto memorizzato nella cache in una nuova istanza dell'oggetto. È possibile accedere al codice XML tramite il <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem.Xml%2A> proprietà del <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem> che rappresenta l'oggetto dati memorizzati nella cache.  

2.  Apportare le modifiche a tale copia.  

3.  Serializzare l'oggetto modificato nuovamente nella cache di dati utilizzando una delle opzioni seguenti:  

    -   Se si desidera serializzare automaticamente le modifiche, utilizzare il <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem.SerializeDataInstance%2A> metodo. Questo metodo Usa il **DiffGram** formato per la serializzazione <xref:System.Data.DataSet>, <xref:System.Data.DataTable>e gli oggetti dataset tipizzati nella cache dei dati. Il **DiffGram** formato garantisce che le modifiche apportate alla cache di dati in un documento non in linea vengono inviate correttamente al server.  

    -   Se si desidera eseguire la serializzazione personalizzata per le modifiche ai dati memorizzati nella cache, è possibile scrivere direttamente il <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem.Xml%2A> proprietà. Specificare il **DiffGram** formattare se si utilizza un <xref:System.Data.Common.DataAdapter> per aggiornare un database con le modifiche apportate ai dati in un <xref:System.Data.DataSet>, <xref:System.Data.DataTable>, o un dataset tipizzato. In caso contrario, il <xref:System.Data.Common.DataAdapter> aggiornerà il database tramite l'aggiunta di nuove righe anziché modificare le righe esistenti.  

### <a name="modify-data-without-deserializing-the-current-value"></a>Modificare i dati senza deserializzare il valore corrente  
 In alcuni casi, si potrebbe voler modificare il valore dell'oggetto memorizzato nella cache senza prima deserializzare il valore corrente. Ad esempio, è possibile farlo se si modifica il valore di un oggetto che presenta un tipo semplice, ad esempio una stringa o un numero intero, o se si inizializza un oggetto nella cache <xref:System.Data.DataSet> in un documento in un server. In questi casi, è possibile utilizzare il <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem.SerializeDataInstance%2A> metodo senza prima deserializzare il valore corrente dell'oggetto memorizzato nella cache.  

 Esempio di codice riportato di seguito viene illustrato come modificare il valore di una stringa memorizzata nella cache il `Sheet1` classe di un progetto cartella di lavoro di Excel. Questo esempio fa parte di un esempio più ampio fornito per il <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.Save%2A> metodo.  

 [!code-csharp[Trin_ServerDocument#11](../vsto/codesnippet/CSharp/Trin_ServerDocument/Form1.cs#11)]
 [!code-vb[Trin_ServerDocument#11](../vsto/codesnippet/VisualBasic/Trin_ServerDocument/Form1.vb#11)]  

### <a name="modify-null-values-in-the-data-cache"></a>Modificare i valori null nella cache dei dati  
 La cache dei dati non archivia gli oggetti che hanno il valore **null** quando il documento viene salvato e chiuso. Questa limitazione ha diverse conseguenze quando si modificano i dati memorizzati nella cache:  

-   Se è impostare qualsiasi oggetto nella cache dei dati per il valore **null**, tutti gli oggetti nella cache dei dati verrà automaticamente impostati su **null** quando il documento viene aperto e verrà cancellata l'intera cache di dati quando il documento viene salvato e chiuso. Vale a dire tutti gli oggetti memorizzati nella cache verranno rimossi dalla cache dei dati e <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.CachedData%2A> raccolta sarà vuota.  

-   Se si compila una soluzione con **null** oggetti nella cache dei dati e si desidera inizializzare questi oggetti utilizzando il <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> classe prima che il documento viene aperto per la prima volta, è necessario assicurarsi di inizializzare tutti gli oggetti nella cache dei dati. Se si inizializza solo alcuni degli oggetti, tutti gli oggetti verrà impostati su **null** quando il documento viene aperto e verrà cancellata la cache di dati quando il documento viene salvato e chiuso.  

## <a name="access-typed-datasets-in-the-cache"></a>L'accesso di dataset tipizzati nella cache  
 Se si desidera accedere ai dati in un dataset tipizzato da una soluzione Office e da un'applicazione all'esterno dell'ufficio, ad esempio un'applicazione Windows Form o un [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] progetto, è necessario definire il dataset tipizzato in un assembly separato a cui fa riferimento in entrambi progetti. Se aggiungere il dataset tipizzato per ogni progetto utilizzando il **configurazione guidata origine dati** procedura guidata o il **Progettazione Dataset**, .NET Framework considererà i dataset tipizzati in due progetti come tipi diversi . Per ulteriori informazioni sulla creazione di dataset tipizzati, vedere [creare e configurare i set di dati in Visual Studio](/visualstudio/data-tools/create-and-configure-datasets-in-visual-studio).  

## <a name="see-also"></a>Vedere anche  
 [Accedere ai dati dei documenti sul server](../vsto/accessing-data-in-documents-on-the-server.md)   
 [Dati memorizzati nella cache nelle personalizzazioni a livello di documento](../vsto/cached-data-in-document-level-customizations.md)  
