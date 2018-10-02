---
title: Compilare i set di dati usando oggetti TableAdapter | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
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
- datasets [Visual Basic]
- datasets [Visual Basic], loading data
- data retrieval
- retrieving data
- datasets [Visual Basic], filling
- data [Visual Studio], retrieving
- data [Visual Studio], datasets
ms.assetid: 55f3bfbe-db78-4486-add3-c62f49e6b9a0
caps.latest.revision: 35
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: c25bbba01d89935044e82a67b3ce40f99d1bf9a4
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47540607"
---
# <a name="fill-datasets-by-using-tableadapters"></a>Compilare i set di dati usando oggetti TableAdapter
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [compilare i set di dati usando oggetti TableAdapter](https://docs.microsoft.com/visualstudio/data-tools/fill-datasets-by-using-tableadapters).  
  
  
Un componente di TableAdapter inserisce un set di dati con i dati dal database, in base a uno o più query o stored procedure specificato. Gli oggetti TableAdapter possono anche eseguire aggiunte, aggiornamenti ed eliminazioni sul database per rendere persistenti le modifiche apportate al set di dati. È inoltre possibile emettere comandi globali che sono correlati a qualsiasi tabella specifica.  
  
> [!NOTE]
>  La classe TableAdapter generati dalle finestre di progettazione di Visual Studio. Se si sta creando i set di dati a livello di codice, quindi usare DataAdapter, ovvero una classe .NET Framework.  
  
 Per informazioni dettagliate sulle operazioni del TableAdapter, è possibile passare direttamente a uno degli argomenti seguenti:  
  
|Argomento|Descrizione|  
|-----------|-----------------|  
|[Creare e configurare oggetti TableAdapter](../data-tools/create-and-configure-tableadapters.md)|Come usare le finestre di progettazione per creare e configurare oggetti TableAdapter|  
|[Creare query TableAdapter con parametri](../data-tools/create-parameterized-tableadapter-queries.md)|Come consentire agli utenti di fornire argomenti all'oggetto TableAdapter procedure o query|  
|[Accedere direttamente al database mediante un oggetto TableAdapter](../data-tools/directly-access-the-database-with-a-tableadapter.md)|Come usare i metodi Dbdirect di TableAdapter|  
|[Disattivare i vincoli durante il riempimento di un set di dati](../data-tools/turn-off-constraints-while-filling-a-dataset.md)|Come usare i vincoli foreign key durante l'aggiornamento dati|  
|[Come estendere le funzionalità di un oggetto TableAdapter](../data-tools/fill-datasets-by-using-tableadapters.md)|Come aggiungere codice personalizzato per gli oggetti TableAdapter|  
|[Leggere dati XML in un set di dati](../data-tools/read-xml-data-into-a-dataset.md)|Come lavorare con XML|  
  
## <a name="tableadapters-overview"></a>Panoramica degli oggetti TableAdapter  
 Gli oggetti TableAdapter sono generato da Progettazione componenti che si connettono a un database, eseguire query o stored procedure e compilare il DataTable con i dati restituiti. Gli oggetti TableAdapter anche inviare i dati aggiornati dall'applicazione nel database. È possibile eseguire tante di query su un oggetto TableAdapter, purché restituiscono dati conformi allo schema della tabella a cui è associato l'oggetto TableAdapter. Il diagramma seguente mostra come oggetti TableAdapter interagire con i database e altri oggetti in memoria:  
  
 ![Flusso di dati in un'applicazione client](../data-tools/media/clientdatadiagram.gif "ClientDataDiagram")  
  
 Anche se gli oggetti TableAdapter sono progettati con la **Progettazione Dataset**, le classi TableAdapter non vengono generate come classi annidate di <xref:System.Data.DataSet>. Si trovano in spazi dei nomi distinti che sono specifiche per ogni set di dati. Ad esempio, se si dispone di un set di dati denominato `NorthwindDataSet`, gli oggetti TableAdapter associate <xref:System.Data.DataTable>s nel `NorthwindDataSet` sarebbe nel `NorthwindDataSetTableAdapters` dello spazio dei nomi. Per accedere a un oggetto TableAdapter particolare a livello di codice, è necessario dichiarare una nuova istanza dell'oggetto TableAdapter. Ad esempio:  
  
 [!code-csharp[VbRaddataTableAdapters#7](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataTableAdapters/CS/Class1.cs#7)]
 [!code-vb[VbRaddataTableAdapters#7](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataTableAdapters/VB/Class1.vb#7)]  
  
## <a name="associated-datatable-schema"></a>Schema di DataTable associati  
 Quando si crea un oggetto TableAdapter, si usa la query iniziale o associato alla stored procedure per definire lo schema dell'oggetto TableAdapter <xref:System.Data.DataTable>. Si esegue questa query iniziale o una stored procedure mediante la chiamata dell'oggetto TableAdapter `Fill` metodo (che riempie l'oggetto TableAdapter associato del <xref:System.Data.DataTable>). Tutte le modifiche apportate alla query principale dell'oggetto TableAdapter vengono riflesse nello schema della tabella dati associata. Ad esempio, la rimozione di una colonna dalla query principale rimuove la colonna dalla tabella dati associata. Se eventuali query aggiuntive sul TableAdapter Usa istruzioni SQL che restituiscono le colonne che non sono presenti nella query principali, la finestra di progettazione prova a sincronizzare le modifiche di colonna tra la query principale e le query aggiuntive. Per altre informazioni, vedere [procedura: modificare oggetti TableAdapter](http://msdn.microsoft.com/library/ca178745-e35a-45f1-a395-23cddfd8f855).  
  
## <a name="tableadapter-update-commands"></a>Comandi di aggiornamento di TableAdapter  
 La funzionalità di aggiornamento di un oggetto TableAdapter è dipendente dalla quantità di informazioni è disponibile la query principale della procedura guidata TableAdapter. Ad esempio, gli oggetti TableAdapter che sono configurati per recuperare i valori da più tabelle (join), i valori scalari, viste o i risultati di funzioni di aggregazione non vengono inizialmente creati con la possibilità di inviare aggiornamenti al database sottostante. Tuttavia, è possibile configurare manualmente i comandi INSERT, UPDATE e DELETE di **proprietà** finestra.  
  
## <a name="tableadapter-queries"></a>TableAdapter (query)  
 ![TableAdapter con più query](../data-tools/media/tableadapter.gif "TableAdapter")  
  
 Gli oggetti TableAdapter possono contenere più query fino a riempire le tabelle dati associate. È possibile definire tutte le query per un oggetto TableAdapter come l'applicazione richiede, purché ogni query restituisce dati conformi allo stesso schema della tabella dati associata. Questa funzionalità Abilita un TableAdapter per caricare i risultati diversi in base a criteri diversi.  
  
 Ad esempio, se l'applicazione contiene una tabella con i nomi dei clienti, è possibile creare una query che riempie la tabella con ogni nome del cliente che inizia con una lettera e un altro che riempie la tabella con tutti i clienti che si trovano nello stesso stato. Per riempire un `Customers` tabella con i clienti in uno stato specifico, è possibile creare un `FillByState` query che accetta un parametro per il valore di stato come segue: `SELECT * FROM Customers WHERE State = @State`. Eseguire la query chiamando il `FillByState` metodo e passando il valore del parametro come segue: `CustomerTableAdapter.FillByState("WA")`.  
  
 Oltre ad aggiungere query che restituiscono dati dello stesso schema della tabella di dati dell'oggetto TableAdapter, è possibile aggiungere query che restituiscono valori scalari (singolo). Ad esempio, una query che restituisce un conteggio di clienti (`SELECT Count(*) From Customers`) è valido per un `CustomersTableAdapter,` anche se i dati restituiti non sono conformi allo schema della tabella.  
  
## <a name="clearbeforefill-property"></a>Proprietà ClearBeforeFill  
 Per impostazione predefinita, ogni volta che si esegue una query per compilare una tabella di dati TableAdapter, i dati esistenti viene cancellati e vengono caricati solo i risultati della query nella tabella. Impostare dell'oggetto TableAdapter `ClearBeforeFill` proprietà `false` se si desidera aggiungere o unire i dati restituiti da una query per i dati esistenti in una tabella dati. Indipendentemente dal fatto che si cancella i dati, è necessario inviare in modo esplicito gli aggiornamenti nel database, se si vuole renderli persistenti. Quindi, ricordarsi di salvare le modifiche ai dati nella tabella prima di eseguire un'altra query che riempie la tabella. Per altre informazioni, vedere [aggiornare i dati mediante un TableAdapter](../data-tools/update-data-by-using-a-tableadapter.md).  
  
## <a name="tableadapter-inheritance"></a>Ereditarietà di TableAdapter  
 Gli oggetti TableAdapter estendere le funzionalità delle schede di dati standard incapsulando configurato <xref:System.Data.Common.DataAdapter> classe? AssetID:///String?qualifyhint=false&AutoUpgrade=True = False & autoUpgrade = True. Per impostazione predefinita, l'oggetto TableAdapter eredita dal <xref:System.ComponentModel.Component> classe e non è possibile eseguire il cast di <xref:System.Data.Common.DataAdapter> classe. Esegue il cast di un oggetto TableAdapter per il <xref:System.Data.Common.DataAdapter> classe risultati in un <xref:System.InvalidCastException> errore? AssetID:///String?qualifyhint=false&AutoUpgrade=True = False & autoUpgrade = True. Per modificare la classe di base di un oggetto TableAdapter, è possibile digitare una classe che deriva da <xref:System.ComponentModel.Component> nella **della classe Base** proprietà dell'oggetto TableAdapter nel **Progettazione Dataset**.  
  
## <a name="tableadapter-methods-and-properties"></a>Le proprietà e i metodi TableAdapter  
 La classe TableAdapter non è in parte il [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]. Ciò significa che è possibile cercarla nella documentazione o la **Visualizzatore oggetti**. Viene creato in fase di progettazione quando si utilizza una delle procedure guidate indicate in precedenza. Il nome assegnato a un oggetto TableAdapter durante la creazione è basato sul nome della tabella di cui che si sta lavorando. Ad esempio, quando si crea un oggetto TableAdapter basato su una tabella in un database denominato `Orders`, denominato oggetto TableAdapter `OrdersTableAdapter`. Il nome della classe dell'oggetto TableAdapter può essere modificato usando il **Name** proprietà nel **Progettazione Dataset**.  
  
 Di seguito sono i metodi comunemente utilizzati e le proprietà degli oggetti TableAdapter:  
  
|Member|Descrizione|  
|------------|-----------------|  
|`TableAdapter.Fill`|Popola tabella dati associata dell'oggetto TableAdapter con i risultati del comando SELECT dell'oggetto TableAdapter.|  
|`TableAdapter.Update`|Invia le modifiche nel database e restituisce un intero che rappresenta il numero di righe interessate dall'aggiornamento. Per altre informazioni, vedere [aggiornare i dati mediante un TableAdapter](../data-tools/update-data-by-using-a-tableadapter.md).|  
|`TableAdapter.GetData`|Restituisce un nuovo <xref:System.Data.DataTable> compilato con i dati.|  
|`TableAdapter.Insert`|Crea una nuova riga nella tabella dati. Per altre informazioni, vedere [inserire nuovi record in un database](../data-tools/insert-new-records-into-a-database.md).|  
|`TableAdapter.ClearBeforeFill`|Determina se una tabella di dati viene svuotata prima di chiamare uno del `Fill` metodi.|  
  
## <a name="tableadapter-update-method"></a>Metodo di aggiornamento di TableAdapter  
 TableAdapter usare comandi di dati per leggere e scrivere dal database. Iniziale dell'oggetto TableAdapter `Fill` query (principale) viene utilizzata come base per creare lo schema della tabella dati associati, nonché la `InsertCommand`, `UpdateCommand`, e `DeleteCommand` comandi che sono associati il `TableAdapter.Update` (metodo). La chiamata a un oggetto TableAdapter `Update` esecuzione del metodo le istruzioni che sono state create quando l'oggetto TableAdapter è stato originariamente configurato, non una delle query aggiuntive che è stato aggiunto con il **configurazione guidata Query TableAdapter**.  
  
 Quando si usa un oggetto TableAdapter, esegue in modo efficace le stesse operazioni con i comandi in genere eseguibili. Ad esempio, quando si chiama l'adapter `Fill` metodo, l'adapter viene eseguito il comando dati relativo `SelectCommand` proprietà e Usa un lettore di dati (ad esempio, <xref:System.Data.SqlClient.SqlDataReader>) per caricare il set dei risultati nella tabella di dati. Analogamente, quando si chiama l'adapter `Update` metodo, viene eseguito il comando appropriato (nelle `UpdateCommand`, `InsertCommand`, e `DeleteCommand` proprietà) per ciascun record nella tabella di dati modificato.  
  
> [!NOTE]
>  Se non sono sufficienti informazioni della query principale, il `InsertCommand`, `UpdateCommand`, e `DeleteCommand` i comandi vengono creati per impostazione predefinita quando viene generato l'oggetto TableAdapter. Se la query TableAdapter principale è più di un'istruzione SELECT singola tabella, è possibile la finestra di progettazione non sia in grado di generare `InsertCommand`, `UpdateCommand`, e `DeleteCommand`. Se non vengono generati i comandi seguenti, è possibile ricevere un errore durante l'esecuzione di `TableAdapter.Update` (metodo).  
  
## <a name="tableadapter-generatedbdirectmethods"></a>TableAdapter GenerateDbDirectMethods  
 Oltre a `InsertCommand`, `UpdateCommand`, e `DeleteCommand`, vengono creati oggetti TableAdapter con metodi che possono essere eseguiti direttamente sul database. Questi metodi (`TableAdapter.Insert`, `TableAdapter.Update`, e `TableAdapter.Delete`) può essere chiamato direttamente per manipolare i dati nel database. Ciò significa che è possibile chiamare questi metodi singoli dal codice anziché chiamare `TableAdapter.Update` per la gestione di inserimenti, aggiornamenti ed eliminazioni in sospeso per la tabella di dati associati.  
  
 Se non si desidera creare questi metodi diretti, impostare dell'oggetto TableAdapter **GenerateDbDirectMethods** proprietà `false` (nelle **proprietà** finestra). Query aggiuntive che vengono aggiunti all'oggetto TableAdapter sono query autonomo, ovvero non generano questi metodi.  
  
## <a name="tableadapter-support-for-nullable-types"></a>Supporto di TableAdapter per i tipi nullable  
 Gli oggetti TableAdapter supporta i tipi nullable `Nullable(Of T)` e `T?`. Per altre informazioni sui tipi nullable in Visual Basic, vedere [Tipi di valori Nullable](http://msdn.microsoft.com/library/9ac3b602-6f96-4e6d-96f7-cd4e81c468a6). Per altre informazioni sui tipi nullable in c#, vedere [utilizzando i tipi Nullable](http://msdn.microsoft.com/library/0bacbe72-ce15-4b14-83e1-9c14e6380c28).  
  
## <a name="security"></a>Sicurezza  
 Quando si usano i comandi di dati con un `CommandType` impostata su <xref:System.Data.CommandType>, attentamente controllare le informazioni inviate da un client prima di passarlo al database. Gli utenti malintenzionati potrebbero tentare di inviare (inserire) istruzioni SQL modificate o aggiuntive nel tentativo di accesso non autorizzato o danneggiare il database. Prima di trasferire input dell'utente a un database, verificare sempre che le informazioni siano valide. Una procedura consigliata consiste nell'utilizzare sempre query con parametri o stored procedure, laddove possibile.  
  
## <a name="see-also"></a>Vedere anche  
 [Strumenti di set di dati in Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)

