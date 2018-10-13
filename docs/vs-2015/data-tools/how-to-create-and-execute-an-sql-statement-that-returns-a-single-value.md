---
title: "Procedura: creare ed eseguire un'istruzione SQL che restituisce un singolo valore | Microsoft Docs"
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
- data reader
- scalar values
- stored procedures, returning single value
- SQL statements, data commands
- DataReader object
- data commands, returning scalar values
ms.assetid: eb366496-69e5-4462-8683-653054165c5c
caps.latest.revision: 24
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 7d5d57637a25db62832ad535bbad60214a0aa4ad
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49192153"
---
# <a name="how-to-create-and-execute-an-sql-statement-that-returns-a-single-value"></a>Procedura: creare ed eseguire un'istruzione SQL che restituisce un valore
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Per eseguire un'istruzione SQL che restituisce un valore singolo, è possibile eseguire una query TableAdapter che è configurata per eseguire un'istruzione SQL (ad esempio, `CustomersTableAdapter.CustomerCount()`).  
  
 Se l'applicazione non usa gli oggetti TableAdapter, chiamare il `ExecuteScalar` metodo su un oggetto comando, l'impostazione relativa `CommandType` proprietà <xref:System.Data.CommandType>. ("Oggetto comando" fa riferimento al comando specifico per il [Provider di dati .NET Framework](http://msdn.microsoft.com/library/03a9fc62-2d24-491a-9fe6-d6bdb6dcb131) usata dall'applicazione. Ad esempio, se l'applicazione usa il Provider di dati .NET Framework per SQL Server, l'oggetto comando sarà <xref:System.Data.SqlClient.SqlCommand>.)  
  
 Negli esempi seguenti illustrano come eseguire le istruzioni SQL che restituiscono valori a precisione singola da un database utilizzando TableAdapter o oggetti command. Per altre informazioni sull'esecuzione di query TableAdapter e comandi, vedere [compilare i set di dati usando oggetti TableAdapter](../data-tools/fill-datasets-by-using-tableadapters.md).  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
## <a name="executing-sql-statements-that-return-single-values-using-a-tableadapter"></a>L'esecuzione di istruzioni SQL che restituiscono valori singoli mediante un TableAdapter  
 In questo esempio viene illustrato come creare una query TableAdapter utilizzando il [modifica di TableAdapter](../data-tools/editing-tableadapters.md), e quindi fornisce informazioni su come dichiarare un'istanza dell'oggetto TableAdapter ed eseguire la query.  
  
#### <a name="to-create-an-sql-statement-returning-a-single-value-using-a-tableadapter"></a>Per creare un'istruzione SQL che restituisce un valore singolo utilizzando un oggetto TableAdapter  
  
1.  Aprire un set di dati di **Progettazione Dataset**. Per altre informazioni, vedere [procedura: aprire un set di dati in Progettazione Dataset](http://msdn.microsoft.com/library/36fc266f-365b-42cb-aebb-c993dc2c47c3).  
  
2.  Se non hai già uno, creare un oggetto TableAdapter. Per altre informazioni sulla creazione di TableAdapter, vedere [creare e configurare oggetti TableAdapter](../data-tools/create-and-configure-tableadapters.md).  
  
3.  Se si dispone già di una query su un determinato TableAdapter che utilizza un'istruzione SQL per restituire un singolo valore, quindi passare alla procedura successiva, "per"dichiarare un'istanza dell'oggetto TableAdapter ed eseguire la query. In caso contrario, continuare con il passaggio 4 per creare una nuova query che restituisce un valore singolo.  
  
4.  Fare doppio clic su oggetto TableAdapter che si desidera e usare il menu di scelta rapida per aggiungere una query.  
  
     Il **configurazione guidata Query TableAdapter** apre.  
  
5.  Lasciare il valore predefinito **Usa istruzioni SQL**, quindi fare clic su **successivo**.  
  
6.  Scegliere il **SELECT che restituisce un valore singolo** opzione e quindi fare clic su **successivo**.  
  
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
        >  Gli oggetti TableAdapter non si trovano all'interno delle classi set di dati associato. Ogni set di dati è una raccolta di oggetti TableAdapter corrispondente nel proprio spazio dei nomi. Ad esempio, se si dispone di un set di dati denominato `SalesDataSet`, quindi non vi sarà un `SalesDataSetTableAdapters` dello spazio dei nomi che contiene la classe TableAdapter.  
  
2.  La query denominata procedendo come per qualsiasi altro metodo nel codice. La query è un metodo sull'oggetto TableAdapter. Sostituire il codice seguente con i nomi del TableAdapter e query. È anche necessario passare i parametri richiesti dalla query e operazioni con il valore restituito (ad esempio, assegnarla a una variabile). Se non si è certi se la query richiede parametri, o i parametri che viene richiesto, quindi controllare IntelliSense per la firma obbligatoria della query. A seconda del fatto che la query accetta parametri o No, il codice avrebbe un aspetto simile a uno degli esempi seguenti:  
  
     `TableAdapter.Query()`  
  
     `TableAdapter.Query(Parameters)`  
  
3.  Sarà probabilmente necessario assegnare il valore restituito dalla query a una variabile. Le query TableAdapter che restituiscono un singolo valore restituiscono un tipo di dati in base alla query (in contrapposizione al `ExecuteScalar` metodo, che restituisce un oggetto). Ad esempio, se la query TableAdapter consente di selezionare una singola colonna con tipo di dati è un numero intero, il valore restituito della query è un numero intero. Se la colonna ammette valori null, il valore restituito è uno dei tipi nullable (ad esempio, `Nullable(Of Integer)`). Per altre informazioni sui tipi nullable, vedere <xref:System.Nullable>. Il codice completo per dichiarare un'istanza di un oggetto TableAdapter ed eseguire una query dovrebbe essere simile al seguente (in questo esempio si presuppone che il valore restituito il valore è un numero intero, modificare il codice in base al tipo di dati restituito dalla query):  
  
     [!code-csharp[VbRaddataFillingAndExecuting#9](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/CS/Form2.cs#9)]
     [!code-vb[VbRaddataFillingAndExecuting#9](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/VB/Form2.vb#9)]  
  
## <a name="executing-sql-statements-that-return-single-values-using-a-command-object"></a>L'esecuzione di istruzioni SQL che restituiscono valori singoli usando un oggetto Command  
 Nell'esempio seguente viene illustrato come creare un comando ed eseguire un'istruzione SQL che restituisce un valore singolo. Per informazioni sull'impostazione e recupero i valori dei parametri per un comando, vedere [procedura: impostare e ottenere i parametri per gli oggetti comando](http://msdn.microsoft.com/library/10110ecc-d2ed-4796-bb8f-74f2ecd40787).  
  
 Questo esempio viene usato il <xref:System.Data.SqlClient.SqlCommand> dell'oggetto e richiede:  
  
-   Fa riferimento per la <xref:System>, <xref:System.Data>, e <xref:System.Xml> gli spazi dei nomi.  
  
-   Una connessione dati denominata `SqlConnection1`.  
  
-   Una tabella denominata `Customers` nei dati di origine che `SqlConnection1` si connette a. (In caso contrario, è necessario un'istruzione SQL valida per l'origine dati).  
  
#### <a name="to-execute-an-sql-statement-returning-a-single-value-using-a-datacommand"></a>Per eseguire un'istruzione SQL che restituisce un valore singolo utilizzando un DataCommand  
  
-   Aggiungere il codice seguente a un metodo che si desidera eseguire il codice da. Per restituire un singolo valore, chiamare il `ExecuteScalar` metodo di un comando (ad esempio, <xref:System.Data.SqlClient.SqlCommand.ExecuteScalar%2A>). I dati vengono restituiti un <xref:System.Object>.  
  
     [!code-csharp[VbRaddataFillingAndExecuting#10](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/CS/Form2.cs#10)]
     [!code-vb[VbRaddataFillingAndExecuting#10](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/VB/Form2.vb#10)]  
  
## <a name="net-framework-security"></a>Sicurezza di .NET Framework  
 L'applicazione richiede l'autorizzazione per accedere al database ed eseguire l'istruzione SQL.  
  
## <a name="see-also"></a>Vedere anche  
 <xref:System.Data.SqlClient.SqlCommand.ExecuteScalar%2A?displayProperty=fullName>   
 <xref:System.Data.OleDb.OleDbCommand.ExecuteScalar%2A?displayProperty=fullName>   
 <xref:System.Data.Odbc.OdbcCommand.ExecuteScalar%2A?displayProperty=fullName>   
 <xref:System.Data.OracleClient.OracleCommand.ExecuteScalar%2A?displayProperty=fullName>   
 [Procedura: creare query TableAdapter](../data-tools/how-to-create-tableadapter-queries.md)   
 [Procedura: modificare query TableAdapter](../data-tools/how-to-edit-tableadapter-queries.md)   
 [Procedura: riempire un set di dati](../data-tools/how-to-fill-a-dataset-with-data.md)   
 [Compilare i set di dati usando oggetti TableAdapter](../data-tools/fill-datasets-by-using-tableadapters.md)   
 [Procedura: impostare e recuperare parametri per gli oggetti comando](http://msdn.microsoft.com/library/10110ecc-d2ed-4796-bb8f-74f2ecd40787)