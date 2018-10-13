---
title: "Procedura: creare ed eseguire un'istruzione SQL che non restituisce alcun valore | Microsoft Docs"
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- method calls, examples
- calling methods, examples
- SQL statements, executing
- SQL statements, creating
ms.assetid: 612d3046-0cfa-4d90-be6e-c4d6bcbd5aee
caps.latest.revision: 23
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 1768db097d2555726b17862c9c4a4b82a3e2a6a8
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49188604"
---
# <a name="how-to-create-and-execute-an-sql-statement-that-returns-no-value"></a>Procedura: creare ed eseguire un'istruzione SQL che non restituisce valori
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Per eseguire un'istruzione SQL che non restituisce alcun valore, è possibile eseguire una query TableAdapter che è configurata per eseguire un'istruzione SQL (ad esempio, `CustomersTableAdapter.UpdateTableData(CustomersDataTable)`).  
  
 Se l'applicazione non usa gli oggetti TableAdapter, chiamare il `ExecuteNonQuery` metodo su un oggetto comando, l'impostazione relativa `CommandType` proprietà <xref:System.Data.CommandType>. ("Oggetto comando" fa riferimento al comando specifico per il [Provider di dati .NET Framework](http://msdn.microsoft.com/library/03a9fc62-2d24-491a-9fe6-d6bdb6dcb131) usata dall'applicazione. Ad esempio, se l'applicazione usa il Provider di dati .NET Framework per SQL Server, l'oggetto comando sarà <xref:System.Data.SqlClient.SqlCommand>.)  
  
 Negli esempi seguenti illustrano come eseguire istruzioni SQL che non restituiscono alcun valore da un database utilizzando TableAdapter o oggetti command. Per altre informazioni sull'esecuzione di query TableAdapter e comandi, vedere [compilare i set di dati usando oggetti TableAdapter](../data-tools/fill-datasets-by-using-tableadapters.md).  
  
## <a name="executing-sql-statements-that-return-no-values-using-a-tableadapter"></a>L'esecuzione di istruzioni SQL che non restituiscono valori mediante un TableAdapter  
 In questo esempio viene illustrato come creare una query TableAdapter utilizzando il [modifica di TableAdapter](../data-tools/editing-tableadapters.md), e quindi fornisce informazioni su come dichiarare un'istanza dell'oggetto TableAdapter ed eseguire la query.  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
#### <a name="to-create-an-sql-statement-that-returns-no-value-using-a-tableadapter"></a>Per creare un'istruzione SQL che non restituisce alcun valore mediante un TableAdapter  
  
1.  Aprire un set di dati di **Progettazione Dataset**. Per altre informazioni, vedere [procedura: aprire un set di dati in Progettazione Dataset](http://msdn.microsoft.com/library/36fc266f-365b-42cb-aebb-c993dc2c47c3).  
  
2.  Se non hai già uno, creare un oggetto TableAdapter. Per altre informazioni sulla creazione di TableAdapter, vedere [creare e configurare oggetti TableAdapter](../data-tools/create-and-configure-tableadapters.md).  
  
3.  Se si dispone già di una query su un determinato TableAdapter che usa un'istruzione SQL che non restituisce alcun valore, quindi passare alla procedura successiva, "per"dichiarare un'istanza dell'oggetto TableAdapter ed eseguire la query. In caso contrario, continuare con il passaggio 4 per creare una nuova query che non restituisce alcun valore.  
  
4.  Fare doppio clic su oggetto TableAdapter che si desidera e usare il menu di scelta rapida per aggiungere una query.  
  
     Il **configurazione guidata Query TableAdapter** apre.  
  
5.  Lasciare il valore predefinito **Usa istruzioni SQL**, quindi fare clic su **successivo**.  
  
6.  Scegliere il **UPDATE**, **INSERT** oppure **eliminare** opzione e quindi fare clic su **successivo**.  
  
7.  Digitare l'istruzione SQL o usare il **generatore di Query** per crearne una e quindi fare clic su **successivo**.  
  
8.  Specificare un nome per la query.  
  
9. Completare la procedura guidata. la query viene aggiunto all'oggetto TableAdapter.  
  
10. Compilazione del progetto.  
  
#### <a name="to-declare-an-instance-of-the-tableadapter-and-execute-the-query"></a>Per dichiarare un'istanza dell'oggetto TableAdapter ed eseguire la query  
  
1.  Dichiarare un'istanza dell'oggetto TableAdapter che contiene la query da eseguire.  
  
    -   Per creare un'istanza usando gli strumenti di progettazione, trascinare il TableAdapter che si desidera dal **casella degli strumenti**. (Componenti del progetto vengono ora visualizzati nei **casella degli strumenti** sotto un'intestazione che corrisponde al nome del progetto.) Se non viene visualizzato il TableAdapter nel **casella degli strumenti**, potrebbe essere necessario compilare il progetto.  
  
         oppure  
  
    -   Per creare un'istanza nel codice, sostituire il codice seguente con i nomi delle <xref:System.Data.DataSet> e TableAdapter.  
  
         `Dim tableAdapter As New DataSetTableAdapters.TableAdapter`  
  
        > [!NOTE]
        >  Gli oggetti TableAdapter non si trovano all'interno delle classi set di dati associato. Ogni set di dati è una raccolta di oggetti TableAdapter corrispondente nel proprio spazio dei nomi. Ad esempio, se si dispone di un set di dati denominato `SalesDataSet`, non vi sarà un `SalesDataSetTableAdapters` dello spazio dei nomi che contiene la classe TableAdapter.  
  
2.  La query denominata procedendo come per qualsiasi altro metodo nel codice. La query è un metodo sull'oggetto TableAdapter. Sostituire il codice seguente con i nomi del TableAdapter e query. È anche necessario passare i parametri richiesti dalla query. Se non si è certi se la query richiede parametri, o i parametri che viene richiesto, quindi controllare IntelliSense per la firma obbligatoria della query. A seconda del fatto che la query accetta parametri o No, il codice avrebbe un aspetto simile a uno degli esempi seguenti:  
  
     `TableAdapter.Query()`  
  
     `TableAdapter.Query(Parameters)`  
  
     Le query che viene considerato come senza restituire alcun valore in realtà restituiscono un valore, ovvero un valore integer contenente il numero di righe interessate dalla query. Il codice completo per dichiarare un'istanza di un oggetto TableAdapter ed eseguire una query dovrebbe essere simile al seguente:  
  
     [!code-csharp[VbRaddataFillingAndExecuting#11](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/CS/Form2.cs#11)]
     [!code-vb[VbRaddataFillingAndExecuting#11](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/VB/Form2.vb#11)]  
  
## <a name="executing-sql-statements-that-return-no-value-using-a-command-object"></a>L'esecuzione di istruzioni SQL che non restituiscono valori usando un oggetto Command  
 Nell'esempio seguente viene illustrato come creare un comando ed eseguire un'istruzione SQL che non restituisce alcun valore. Per informazioni sull'impostazione e recupero i valori dei parametri per un comando, vedere [procedura: impostare e ottenere i parametri per gli oggetti comando](http://msdn.microsoft.com/library/10110ecc-d2ed-4796-bb8f-74f2ecd40787).  
  
 Questo esempio viene usato il <xref:System.Data.SqlClient.SqlCommand> dell'oggetto e richiede:  
  
-   Fa riferimento per la <xref:System>, <xref:System.Data>, e <xref:System.Xml> gli spazi dei nomi.  
  
-   Una connessione dati denominata `SqlConnection1`.  
  
-   Una tabella denominata `Customers` nei dati di origine che `SqlConnection1` si connette a. (In caso contrario, è necessario un'istruzione SQL valida per l'origine dati).  
  
#### <a name="to-execute-an-sql-statement-that-returns-no-value-using-a-datacommand"></a>Per eseguire un'istruzione SQL che non restituisce alcun valore utilizzando un DataCommand  
  
-   Aggiungere il codice seguente a un metodo che si desidera eseguire l'istruzione SQL da. Chiamare il `ExecuteNonQuery` metodo di un comando per non restituire alcun valore (ad esempio, <xref:System.Data.SqlClient.SqlCommand.ExecuteNonQuery%2A?displayProperty=fullName>).  
  
     [!code-csharp[VbRaddataFillingAndExecuting#12](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/CS/Form2.cs#12)]
     [!code-vb[VbRaddataFillingAndExecuting#12](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/VB/Form2.vb#12)]  
  
## <a name="net-framework-security"></a>Sicurezza di .NET Framework  
 L'applicazione richiede l'autorizzazione per accedere al database ed eseguire l'istruzione SQL.  
  
## <a name="see-also"></a>Vedere anche  
 <xref:System.Data.SqlClient.SqlCommand.ExecuteNonQuery%2A?displayProperty=fullName>   
 <xref:System.Data.OleDb.OleDbCommand.ExecuteNonQuery%2A?displayProperty=fullName>   
 <xref:System.Data.Odbc.OdbcCommand.ExecuteNonQuery%2A?displayProperty=fullName>   
 <xref:System.Data.OracleClient.OracleCommand.ExecuteNonQuery%2A?displayProperty=fullName>   
 [Procedura: creare query TableAdapter](../data-tools/how-to-create-tableadapter-queries.md)   
 [Procedura: modificare query TableAdapter](../data-tools/how-to-edit-tableadapter-queries.md)   
 [Procedura: riempire un set di dati](../data-tools/how-to-fill-a-dataset-with-data.md)   
 [Compilare i set di dati usando oggetti TableAdapter](../data-tools/fill-datasets-by-using-tableadapters.md)   
 [Procedura: impostare e recuperare parametri per gli oggetti comando](http://msdn.microsoft.com/library/10110ecc-d2ed-4796-bb8f-74f2ecd40787)