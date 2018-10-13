---
title: 'Procedura: eseguire una Stored Procedure che non restituisce alcun valore | Microsoft Docs'
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
- ExecuteNonQuery method
- stored procedures, creating
- stored procedures, executing
ms.assetid: 8a929e96-2cf5-43a5-b5b7-c0a5a397bbc5
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 38dea599c0c3247c3dd2e3e1d1ca8bb02315cfc5
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49263094"
---
# <a name="how-to-execute-a-stored-procedure-that-returns-no-value"></a>Procedura: eseguire una stored procedure che non restituisce valori
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Per eseguire una stored procedure che non restituisce alcun valore, è possibile eseguire una query TableAdapter che è configurata per eseguire una stored procedure (ad esempio, `CustomersTableAdapter.UpdateTableData(CustomersDataTable)`).  
  
 Se l'applicazione non usa gli oggetti TableAdapter, chiamare il `ExecuteNonQuery` metodo su un oggetto comando, l'impostazione relativa `CommandType` proprietà <xref:System.Data.CommandType>. ("Oggetto comando" fa riferimento al comando specifico per il [Provider di dati .NET Framework](http://msdn.microsoft.com/library/03a9fc62-2d24-491a-9fe6-d6bdb6dcb131) usata dall'applicazione. Ad esempio, se l'applicazione usa il Provider di dati .NET Framework per SQL Server, quindi l'oggetto comando sarebbe <xref:System.Data.SqlClient.SqlCommand>.)  
  
 Negli esempi seguenti illustrano come oggetti comando o l'esecuzione di stored procedure che non restituiscono nessun valore da un database utilizzando TableAdapter. Per altre informazioni sull'esecuzione di query TableAdapter e comandi, vedere [compilare i set di dati usando oggetti TableAdapter](../data-tools/fill-datasets-by-using-tableadapters.md).  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
## <a name="executing-stored-procedures-that-return-no-values-using-a-tableadapter"></a>Esecuzione di Stored procedure che non restituiscono valori mediante un TableAdapter  
 In questo esempio viene illustrato come creare una query TableAdapter utilizzando il [modifica di TableAdapter](../data-tools/editing-tableadapters.md), e quindi fornisce informazioni su come dichiarare un'istanza dell'oggetto TableAdapter ed eseguire la query.  
  
#### <a name="to-create-a-stored-procedure-that-returns-no-value-using-a-tableadapter"></a>Per creare una stored procedure che non restituisce alcun valore mediante un TableAdapter  
  
1.  Aprire un set di dati di **Progettazione Dataset**. Per altre informazioni, vedere [procedura: aprire un set di dati in Progettazione Dataset](http://msdn.microsoft.com/library/36fc266f-365b-42cb-aebb-c993dc2c47c3).  
  
2.  Se non hai già uno, creare un oggetto TableAdapter. Per altre informazioni sulla creazione di TableAdapter, vedere [creare e configurare oggetti TableAdapter](../data-tools/create-and-configure-tableadapters.md).  
  
3.  Se si dispone già di una query su un determinato TableAdapter che utilizza una stored procedure che non restituisce alcun valore, passare alla procedura successiva, "per"dichiarare un'istanza dell'oggetto TableAdapter ed eseguire la query. In caso contrario, continuare con il passaggio 4 per creare una nuova query che non restituisce alcun valore.  
  
4.  Fare doppio clic su oggetto TableAdapter che si desidera e usare il menu di scelta rapida per aggiungere una query.  
  
     Il **configurazione guidata Query TableAdapter** apre.  
  
5.  Selezionare **usare stored procedure esistente**, quindi fare clic su **successivo**.  
  
6.  Selezionare una stored procedure nell'elenco a discesa e quindi fare clic su **successivo**.  
  
7.  Selezionare l'opzione per restituire **alcun valore**, quindi fare clic su **successivo**.  
  
8.  Specificare un nome per la query.  
  
9. Fare clic su **successivo**, o **fine** per completare la procedura guidata; la query viene aggiunto all'oggetto TableAdapter.  
  
10. Compilazione del progetto.  
  
#### <a name="to-declare-an-instance-of-the-tableadapter-and-execute-the-query"></a>Per dichiarare un'istanza dell'oggetto TableAdapter ed eseguire la query  
  
1.  Dichiarare un'istanza dell'oggetto TableAdapter che contiene la query che si desidera eseguire.  
  
    -   Per creare un'istanza usando gli strumenti di progettazione, trascinare il TableAdapter che si desidera dal **casella degli strumenti**. (Componenti del progetto vengono ora visualizzati nei **casella degli strumenti** sotto un'intestazione che corrisponde al nome del progetto.) Se non viene visualizzato il TableAdapter nel **casella degli strumenti**, potrebbe essere necessario compilare il progetto.  
  
         oppure  
  
    -   Per creare un'istanza nel codice, sostituire il codice seguente con i nomi delle <xref:System.Data.DataSet> e TableAdapter.  
  
         `Dim tableAdapter As New DataSetTableAdapters.TableAdapter`  
  
        > [!NOTE]
        >  Gli oggetti TableAdapter non si trovano all'interno delle classi set di dati associato. Ogni set di dati è una raccolta di oggetti TableAdapter corrispondente nel proprio spazio dei nomi. Ad esempio, se si dispone di un set di dati denominato `SalesDataSet`, quindi non vi sarà un `SalesDataSetTableAdapters` dello spazio dei nomi che contiene la classe TableAdapter.  
  
2.  La query denominata procedendo come per qualsiasi altro metodo nel codice. La query è un metodo sull'oggetto TableAdapter. Sostituire il codice seguente con i nomi del TableAdapter e query. Dovrai anche passare i parametri richiesti dalla query. Se non si è certi se la query richiede parametri, o i parametri che viene richiesto, quindi controllare IntelliSense per la firma obbligatoria della query. A seconda del fatto che la query accetta parametri o No, il codice avrebbe un aspetto simile a uno degli esempi seguenti:  
  
     `TableAdapter.Query()`  
  
     `TableAdapter.Query(Parameters)`  
  
     Il codice completo per dichiarare un'istanza dell'oggetto TableAdapter ed eseguire la query dovrebbe essere simile al seguente:  
  
     [!code-csharp[VbRaddataFillingAndExecuting#11](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/CS/Form2.cs#11)]
     [!code-vb[VbRaddataFillingAndExecuting#11](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/VB/Form2.vb#11)]  
  
## <a name="executing-stored-procedures-that-return-no-value-using-a-command-object"></a>L'esecuzione di Stored procedure che non restituiscono alcun valore utilizzando un oggetto Command  
 Nell'esempio seguente viene illustrato come creare un comando ed eseguire una stored procedure che non restituisce alcun valore. Per informazioni sull'impostazione e recupero i valori dei parametri per un comando, vedere [procedura: impostare e ottenere i parametri per gli oggetti comando](http://msdn.microsoft.com/library/10110ecc-d2ed-4796-bb8f-74f2ecd40787).  
  
 Questo esempio viene usato il <xref:System.Data.SqlClient.SqlCommand> dell'oggetto e richiede:  
  
-   Fa riferimento per la <xref:System>, <xref:System.Data>, e <xref:System.Xml> gli spazi dei nomi.  
  
#### <a name="to-execute-a-stored-procedure-that-returns-no-value-using-a-datacommand"></a>Per eseguire una stored procedure che non restituisce alcun valore utilizzando un DataCommand  
  
-   Aggiungere il codice seguente a un metodo che si vuole eseguire la stored procedure da. Chiamare il `ExecuteNonQuery` metodo di un comando per non restituire alcun valore (ad esempio, <xref:System.Data.SqlClient.SqlCommand.ExecuteNonQuery%2A>).  
  
     [!code-csharp[VbRaddataFillingAndExecuting#15](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/CS/Form2.cs#15)]
     [!code-vb[VbRaddataFillingAndExecuting#15](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/VB/Form2.vb#15)]  
  
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