---
title: Panoramica degli oggetti TableAdapter | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vbData.Microsoft.VSDesigner.DataSource.DataAccessor
- vbdata.Microsoft.VSDesigner.DataSource.DataAccessor
- TableAdapter
- vs.data.TableAdapter
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- data [Visual Studio], table adapters
- TableAdapters, queries
- data [Visual Studio], TableAdapters
- query data in Visual Studio
- TableAdapter.GetData
- TableAdapter.Fill
- data [Visual Studio], datasets
- TableAdapters
- table adapters
ms.assetid: a87c46a0-52ab-432a-a864-9ba55069f9eb
caps.latest.revision: 40
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: fb5ebcdaa1bebe67c2fb8e378c7345467dd10b78
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49269048"
---
# <a name="tableadapter-overview"></a>Cenni preliminari sugli oggetti TableAdapter
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Gli oggetti TableAdapter sono generato da Progettazione componenti che si connettono a un database, eseguire query o stored procedure e compilare il DataTable con i dati restituiti. La classe TableAdapter consentono inoltre di inviare i dati aggiornati dall'applicazione nel database. È possibile avere tanti di query su un oggetto TableAdapter, purché restituiscono dati conformi allo schema della tabella a cui è associato l'oggetto TableAdapter. Il diagramma seguente mostra come oggetti TableAdapter interagire con i database e altri oggetti in memoria:  
  
 ![Flusso di dati in un'applicazione client](../data-tools/media/clientdatadiagram.gif "ClientDataDiagram")  
  
 Anche se gli oggetti TableAdapter sono progettati con la **Progettazione Dataset**, le classi TableAdapter generate non vengono generate come classi annidate del <xref:System.Data.DataSet>. Si trovano in uno spazio dei nomi separato per ogni set di dati specifico. Ad esempio, se si dispone di un set di dati denominato `NorthwindDataSet`, gli oggetti TableAdapter associato con il <xref:System.Data.DataTable>s nel `NorthwindDataSet` sarebbe nel `NorthwindDataSetTableAdapters` dello spazio dei nomi. Per accedere a un oggetto TableAdapter particolare a livello di codice, è necessario dichiarare una nuova istanza dell'oggetto TableAdapter. Ad esempio:  
  
 [!code-csharp[VbRaddataTableAdapters#7](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataTableAdapters/CS/Class1.cs#7)]
 [!code-vb[VbRaddataTableAdapters#7](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataTableAdapters/VB/Class1.vb#7)]  
  
## <a name="associated-datatable-schema"></a>Schema di DataTable associati  
 Durante la creazione di un oggetto TableAdapter, la query iniziale o una stored procedure viene utilizzata per definire lo schema dell'oggetto TableAdapter associato del <xref:System.Data.DataTable>. Si esegue questa query iniziale o una stored procedure mediante la chiamata dell'oggetto TableAdapter `Fill` metodo (che riempie l'oggetto TableAdapter associato del <xref:System.Data.DataTable>). Tutte le modifiche apportate alla query principale dell'oggetto TableAdapter vengono riflesse nello schema della tabella dati associata. Ad esempio, la rimozione di una colonna dalla query principale rimuove la colonna dalla tabella dati associata. Se eventuali query aggiuntive sul TableAdapter Usa istruzioni SQL restituzione delle colonne non presenti nella query principale, quindi nella finestra di progettazione proverà a sincronizzare le modifiche di colonna tra la query principale e qualsiasi altra query. Per altre informazioni, vedere [procedura: modificare oggetti TableAdapter](http://msdn.microsoft.com/library/ca178745-e35a-45f1-a395-23cddfd8f855).  
  
## <a name="tableadapter-update-commands"></a>Comandi di aggiornamento di TableAdapter  
 La funzionalità di aggiornamento di un oggetto TableAdapter è dipendente dalla quantità di informazioni è disponibile in base alla query principale fornita nella procedura guidata TableAdapter. Ad esempio, gli oggetti TableAdapter che sono configurati per recuperare i valori da più tabelle (join), i valori scalari, viste o i risultati di funzioni di aggregazione non vengono inizialmente creati con la possibilità di inviare aggiornamenti al database sottostante. Tuttavia, è possibile configurare manualmente i comandi INSERT, UPDATE e DELETE di **proprietà** finestra.  
  
## <a name="tableadapter-queries"></a>Query TableAdapter  
 ![TableAdapter con più query](../data-tools/media/tableadapter.gif "TableAdapter")  
  
 Gli oggetti TableAdapter possono contenere più query fino a riempire le tabelle dati associate. È possibile definire tutte le query per un oggetto TableAdapter come l'applicazione richiede, purché ogni query restituisce dati conformi allo stesso schema della tabella dati associata. In questo modo il caricamento dei dati che soddisfano criteri diversi. Ad esempio, se l'applicazione contiene una tabella di clienti, è possibile creare una query che riempie la tabella con ogni cliente il cui nome inizia con una lettera e un'altra query che riempie la tabella con tutti i clienti che si trova nello stesso stato. Per riempire un `Customers` tabella con i clienti in uno stato specifico, è possibile creare un `FillByState` query che accetta un parametro per il valore di stato: `SELECT * FROM Customers WHERE State = @State`. Per eseguire la query, chiamare il `FillByState` metodo e passando il valore del parametro come segue: `CustomerTableAdapter.FillByState("WA")`. Per altre informazioni, vedere [procedura: creare query TableAdapter](../data-tools/how-to-create-tableadapter-queries.md).  
  
 Oltre alle query che restituiscono dati dello stesso schema della tabella di dati dell'oggetto TableAdapter, è possibile aggiungere query che restituiscono valori scalari (singolo). Ad esempio, la creazione di una query che restituisce un conteggio di clienti (`SELECT Count(*) From Customers`) è valido per un `CustomersTableAdapter` anche se i dati restituiti non è conforme allo schema della tabella.  
  
## <a name="clearbeforefill-property"></a>Proprietà ClearBeforeFill  
 Per impostazione predefinita, ogni volta che si esegue una query per compilare una tabella di dati TableAdapter, i dati vengono cancellati e vengono caricati solo i risultati della query nella tabella. Impostare dell'oggetto TableAdapter `ClearBeforeFill` proprietà `false` se si desidera aggiungere o unire i dati restituiti da una query per i dati esistenti in una tabella dati. Indipendentemente dal fatto che si cancella i dati, è necessario inviare in modo esplicito gli aggiornamenti nel database, se lo si desidera. Quindi, ricordarsi di salvare le modifiche apportate ai dati nella tabella prima di eseguire un'altra query che riempie la tabella. Per altre informazioni, vedere [aggiornare i dati mediante un TableAdapter](../data-tools/update-data-by-using-a-tableadapter.md).  
  
## <a name="tableadapter-inheritance"></a>Ereditarietà di TableAdapter  
 Gli oggetti TableAdapter estendere le funzionalità delle schede di dati standard incapsulando configurato <xref:System.Data.Common.DataAdapter>. Per impostazione predefinita, l'oggetto TableAdapter eredita da <xref:System.ComponentModel.Component> e non è possibile eseguire il cast di <xref:System.Data.Common.DataAdapter> classe. Esegue il cast di un oggetto TableAdapter a un <xref:System.Data.Common.DataAdapter> comporterà un <xref:System.InvalidCastException>. Per modificare la classe di base di un oggetto TableAdapter, è possibile digitare una classe che deriva da <xref:System.ComponentModel.Component> nella **della classe Base** proprietà dell'oggetto TableAdapter nel **Progettazione Dataset**.  
  
## <a name="tableadapter-methods-and-properties"></a>Le proprietà e i metodi TableAdapter  
 La classe TableAdapter non è in parte il [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)], e di conseguenza è possibile cercarla nella documentazione di o il **Visualizzatore oggetti**. Viene creato in fase di progettazione quando si utilizza una delle procedure guidate indicato in precedenza. Il nome assegnato a un oggetto TableAdapter durante la creazione è basato sul nome della tabella di cui che si sta lavorando. Ad esempio, quando la creazione di un oggetto TableAdapter di basato su una tabella in un database denominato `Orders`, avrà come nome dell'oggetto TableAdapter `OrdersTableAdapter`. Il nome della classe dell'oggetto TableAdapter può essere modificato usando il **Name** proprietà nel **Progettazione Dataset**.  
  
 Di seguito sono i metodi comunemente utilizzati e le proprietà degli oggetti TableAdapter:  
  
|Member|Descrizione|  
|------------|-----------------|  
|`TableAdapter.Fill`|Popola tabella dati associata dell'oggetto TableAdapter con i risultati del comando SELECT dell'oggetto TableAdapter. Per altre informazioni, vedere [procedura: riempire un set di dati](../data-tools/how-to-fill-a-dataset-with-data.md).|  
|`TableAdapter.Update`|Invia le modifiche nel database e restituisce un valore integer che rappresenta il numero di righe interessate dall'aggiornamento. Per altre informazioni, vedere [aggiornare i dati mediante un TableAdapter](../data-tools/update-data-by-using-a-tableadapter.md).|  
|`TableAdapter.GetData`|Restituisce un nuovo <xref:System.Data.DataTable> occupata dai dati.|  
|`TableAdapter.Insert`|Crea una nuova riga nella tabella dati. Per altre informazioni, vedere [procedura: aggiungere righe a un oggetto DataTable](http://msdn.microsoft.com/library/78ebbb43-c402-49cf-81da-0715289487bf).|  
|`TableAdapter.ClearBeforeFill`|Determina se una tabella di dati viene svuotata prima di chiamare uno del `Fill` metodi.|  
  
## <a name="tableadapter-update-method"></a>Metodo di aggiornamento di TableAdapter  
 TableAdapter usare comandi di dati per leggere e scrivere dal database. Iniziale dell'oggetto TableAdapter `Fill` query (principale) viene utilizzata come base per creare lo schema della tabella, i dati associati, nonché `InsertCommand`, `UpdateCommand`, e `DeleteCommand` comandi associati il `TableAdapter.Update` (metodo). Ciò significa che la chiamata a un oggetto TableAdapter `Update` metodo esegue le istruzioni create quando è stato originariamente configurato TableAdapter, e non una delle query aggiuntive aggiunto con il **diconfigurazioneguidataQueryTableAdapter**.  
  
 Quando si usa un oggetto TableAdapter, esegue in modo efficace le stesse operazioni con i comandi in genere eseguibili. Ad esempio, quando si chiama l'adapter `Fill` metodo, l'adapter esegue il comando di dati nel relativo `SelectCommand` proprietà e Usa un lettore di dati (ad esempio, <xref:System.Data.SqlClient.SqlDataReader>) per caricare il set dei risultati nella tabella di dati. Analogamente, quando si chiama l'adapter `Update` metodo, verrà eseguito il comando appropriato (nel `UpdateCommand`, `InsertCommand`, e `DeleteCommand` proprietà) per ciascun record nella tabella di dati modificato.  
  
> [!NOTE]
>  Se non sono sufficienti informazioni della query principale, il `InsertCommand`, `UpdateCommand`, e `DeleteCommand` i comandi vengono creati per impostazione predefinita quando viene generato l'oggetto TableAdapter. Se il TableAdapter principale query è più di un'istruzione SELECT singola tabella, è possibile la finestra di progettazione non sarà in grado di generare le `InsertCommand`, `UpdateCommand`, e `DeleteCommand`. Se non vengono generati i comandi seguenti, si verifichi un errore durante l'esecuzione di `TableAdapter.Update` (metodo).  
  
## <a name="tableadapter-generatedbdirectmethods"></a>TableAdapter GenerateDbDirectMethods  
 Oltre al `InsertCommand`, `UpdateCommand`, e `DeleteCommand`, vengono creati oggetti TableAdapter con metodi che possono essere eseguiti direttamente sul database. Questi metodi (`TableAdapter.Insert`, `TableAdapter.Update`, e `TableAdapter.Delete`) può essere chiamato direttamente per manipolare i dati nel database. Ciò significa che è possibile chiamare questi metodi singoli dal codice anziché chiamare TableAdapter per la gestione di inserimenti, aggiornamenti ed eliminazioni in sospeso per la tabella di dati associati.  
  
 Se non vuoi creare questi metodi diretti, impostare dell'oggetto TableAdapter **GenerateDbDirectMethods** proprietà `false` (nelle **proprietà** finestra). Altre query aggiunte all'oggetto TableAdapter sono query autonomo, ovvero non generano questi metodi.  
  
## <a name="tableadapter-support-for-nullable-types"></a>Supporto di TableAdapter per i tipi Nullable  
 Gli oggetti TableAdapter supporta i tipi nullable `Nullable(Of T)` e `T?`. Per altre informazioni sui tipi nullable in Visual Basic, vedere [tipi di valore Nullable](http://msdn.microsoft.com/library/9ac3b602-6f96-4e6d-96f7-cd4e81c468a6). Per altre informazioni sui tipi nullable in c#, vedere [utilizzando i tipi Nullable](http://msdn.microsoft.com/library/0bacbe72-ce15-4b14-83e1-9c14e6380c28).  
  
## <a name="see-also"></a>Vedere anche  
 [Procedure dettagliate di data](http://msdn.microsoft.com/library/15a88fb8-3bee-4962-914d-7a1f8bd40ec4)   
 [Procedura: Connettersi ai dati di un database](../data-tools/how-to-connect-to-data-in-a-database.md)   
 [Procedura dettagliata: Connessione ai dati in un Database (Windows Form)](http://msdn.microsoft.com/library/02d39aa6-8993-4602-be13-a13536af3d1c)   
 [Preparare l'applicazione per ricevere dati](http://msdn.microsoft.com/library/c17bdb7e-c234-4f2f-9582-5e55c27356ad)   
 [Recupero di dati nell'applicazione](../data-tools/fetching-data-into-your-application.md)   
 [Associazione di controlli ai dati in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Modifica dei dati nell'applicazione](../data-tools/editing-data-in-your-application.md)   
 [La convalida dei dati](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)   
 [Salvataggio di dati](../data-tools/saving-data.md)