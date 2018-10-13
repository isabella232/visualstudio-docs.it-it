---
title: 'Procedura: salvare le modifiche di set di dati in un Database | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- DbDataAdapter.Update
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- data [Visual Studio], saving
- databases, updating
- updating datasets, writing changes to data source
ms.assetid: c9970150-b71b-4c9d-a355-5efb6b510dca
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: a197952bcc392f84db3f612a158817237e077d36
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49202280"
---
# <a name="how-to-save-dataset-changes-to-a-database"></a>Procedura: salvare le modifiche di un dataset in un database
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Dopo aver modificati i dati nel set di dati e convalidati, probabilmente si desidera inviare i dati aggiornati in un database. Per inviare i dati modificati in un database, si chiama il `Update` metodo di un [TableAdapter](../data-tools/tableadapter-overview.md) o adattatore di dati. L'adapter `Update` metodo aggiorna una singola tabella di dati ed esegue il comando corretto (INSERT, UPDATE o DELETE) in base il <xref:System.Data.DataRow.RowState%2A> di ogni riga di dati nella tabella.  
  
 Durante il salvataggio dei dati nelle tabelle correlate, Visual Studio fornisce un componente TableAdapterManager che semplifica procedura nell'ordine corretto in base ai vincoli di chiave esterna definiti nel database. Per altre informazioni, vedere [Cenni preliminari sull'aggiornamento gerarchico](http://msdn.microsoft.com/library/c4f8e8b9-e4a5-4a02-8462-d03d1e8222d6).  
  
> [!NOTE]
>  Poiché il tentativo di aggiornare un'origine dati con il contenuto di un set di dati può causare errori, è necessario posizionare il codice che chiama l'adapter `Update` metodo all'interno di un `try` / `catch` blocco.  
  
 L'esatta procedura per aggiornare un'origine dati può variare a seconda delle esigenze aziendali, ma l'applicazione deve includere i passaggi seguenti:  
  
1.  Eseguire il codice che consente di inviare aggiornamenti al database all'interno di un `try` / `catch` blocco.  
  
2.  Se viene rilevata un'eccezione, individuare la riga di dati che ha causato l'errore. Per altre informazioni, vedere [procedura: individuare le righe che presentano errori](http://msdn.microsoft.com/library/1fa907c5-fe66-4f29-a253-2b97b900050c).  
  
3.  Risolvere il problema nei dati di riga (a livello di codice se possibile, o presentando la riga non valida per l'utente per la modifica) e quindi tentare nuovamente l'aggiornamento (<xref:System.Data.DataRow.HasErrors%2A> proprietà, <xref:System.Data.DataTable.GetErrors%2A> (metodo)).  
  
## <a name="saving-data-to-a-database"></a>Salvataggio dei dati in un Database  
 Chiamare il `Update` metodo di una scheda di dati o TableAdapter, passando il nome della tabella dati che contiene i valori da scrivere nel database. Per altre informazioni sul salvataggio dei dati da una singola tabella di dati in un database, vedere [procedura dettagliata: salvataggio di dati a un Database (a tabella singola)](http://msdn.microsoft.com/library/68befa96-7463-43e8-abcf-dc2f42ccd53d).  
  
#### <a name="to-update-a-database-with-a-dataset-using-a-tableadapter"></a>Per aggiornare un database con un set di dati mediante un TableAdapter  
  
-   Racchiudere le `TableAdapter.Update` metodo all'interno di un `try` / `catch` blocco. Nell'esempio seguente viene illustrato come tentativo di aggiornamento con il contenuto del `Customers` tabella di `NorthwindDataSet`.  
  
     [!code-csharp[VbRaddataSaving#9](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form3.cs#9)]
     [!code-vb[VbRaddataSaving#9](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form3.vb#9)]  
  
#### <a name="to-update-a-database-with-a-dataset-using-a-data-adapter"></a>Per aggiornare un database con un set di dati utilizzando un adattatore dati  
  
-   Racchiudere le `DataAdapter.Update` metodo all'interno di un `try` / `catch` blocco. Nell'esempio seguente viene illustrato come tentativo di aggiornamento a un'origine dati con il contenuto della `Table1` in `DataSet1`.  
  
     [!code-csharp[VbRaddataSaving#26](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs#26)]
     [!code-vb[VbRaddataSaving#26](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb#26)]  
  
## <a name="updating-two-related-tables-in-a-dataset"></a>L'aggiornamento di due tabelle correlate in un set di dati  
 Quando si aggiornano tabelle correlate in un set di dati, è importante per l'aggiornamento in sequenza appropriata per ridurre il rischio di violazione di vincoli di integrità referenziale. L'ordine di esecuzione del comando seguirà anche gli indici del <xref:System.Data.DataRowCollection> nel set di dati. Per impedire che vengano generati errori di integrità dei dati, la procedura consigliata consiste nell'aggiornare il database nella sequenza seguente:  
  
1.  Tabella figlio: eliminare record.  
  
2.  Tabella padre: inserire, aggiornare ed eliminare i record.  
  
3.  Tabella figlio: inseriscono e aggiornano i record.  
  
 Per informazioni dettagliate sul salvataggio dei dati da più tabelle, vedere [salvare i dati in un database (più tabelle)](../data-tools/save-data-to-a-database-multiple-tables.md).  
  
 Se si siano aggiornando due o più tabelle correlate, è necessario includere tutta la logica di aggiornamento all'interno di una transazione. Una transazione è un processo che garantisce che tutte le modifiche correlate apportate a un database vengano completate prima di eseguire il commit delle modifiche. Per altre informazioni, vedere [transazioni e concorrenza](http://msdn.microsoft.com/library/f46570de-9e50-4fe6-8710-a8c31fa8569b).  
  
#### <a name="to-update-two-related-tables-using-a-tableadapter"></a>Per aggiornare due tabelle correlate tramite un oggetto TableAdapter  
  
1.  Creare tre temporaneo <xref:System.Data.DataTable>s per contenere diversi record.  
  
2.  Chiamare il `Update` metodo per ogni subset di righe dall'interno una `try` / `catch` blocco. Se si verificano errori di aggiornamento, la linea di condotta suggerita è interrompere il processo e risolverli.  
  
3.  Salvare le modifiche dal set di dati nel database.  
  
4.  Eliminare le tabelle di dati temporanei per rilasciare le risorse.  
  
     [!code-csharp[VbRaddataSaving#27](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form2.cs#27)]
     [!code-vb[VbRaddataSaving#27](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form2.vb#27)]  
  
#### <a name="to-update-two-related-tables-using-a-data-adapter"></a>Per aggiornare due tabelle correlate utilizzando un adattatore dati  
  
-   Chiamare il `Update` metodo per ogni adattatore dati.  
  
     Nell'esempio seguente viene illustrato come aggiornare un'origine dati con un set di dati che contiene le tabelle correlate. Per seguire la sequenza precedente, tre temporaneo <xref:System.Data.DataTable>s verrà creato per contenere diversi record. L'oggetto `Update` metodo verrà chiamato per ogni subset di righe dall'interno una `try` / `catch` blocco. Se si verificano errori di aggiornamento, la linea di condotta suggerita è interrompere il processo e risolverli. Quindi il set di dati esegue il commit delle modifiche. Infine, eliminare le tabelle di dati temporanei per rilasciare le risorse.  
  
     [!code-csharp[VbRaddataSaving#28](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs#28)]
     [!code-vb[VbRaddataSaving#28](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb#28)]  
  
## <a name="see-also"></a>Vedere anche  
 [Procedure dettagliate di data](http://msdn.microsoft.com/library/15a88fb8-3bee-4962-914d-7a1f8bd40ec4)   
 [Associazione di controlli Windows Form ai dati in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Connessione ai dati in Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Preparare l'applicazione per ricevere dati](http://msdn.microsoft.com/library/c17bdb7e-c234-4f2f-9582-5e55c27356ad)   
 [Recupero di dati nell'applicazione](../data-tools/fetching-data-into-your-application.md)   
 [Associazione di controlli ai dati in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Modifica dei dati nell'applicazione](../data-tools/editing-data-in-your-application.md)   
 [La convalida dei dati](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)   
 [Salvataggio di dati](../data-tools/saving-data.md)