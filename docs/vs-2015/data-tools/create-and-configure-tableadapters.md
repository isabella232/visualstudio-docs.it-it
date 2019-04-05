---
title: Creare e configurare oggetti TableAdapter | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- table adapters, creating
- creating TableAdapters
- data [Visual Studio], creating data components
- data [Visual Studio], TableAdapters
- data [Visual Studio], creating table adapters
ms.assetid: 08630d69-0d6c-4e8f-b42d-2922f45f8415
caps.latest.revision: 33
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 24f53af16bcab0e3ff631a7c264f139f94d92232
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58954727"
---
# <a name="create-and-configure-tableadapters"></a>Creare e configurare oggetti TableAdapter
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
La classe TableAdapter consentono la comunicazione tra l'applicazione e un database. Si connettono al database, eseguire query o stored procedure e restituiscono un nuovi dati di tabella o di riempimento esistente <xref:System.Data.DataTable> con i dati restituiti. Gli oggetti TableAdapter possono anche inviare dati aggiornati dall'applicazione nel database.  
  
 La classe TableAdapter vengono create automaticamente quando si esegue una delle azioni seguenti:  
  
- Eseguire la [configurazione guidata origine dati](http://msdn.microsoft.com/library/c4df7de5-5da0-4064-940c-761dd6d9e28f) e selezionare il **Database** oppure **servizio Web** tipo di origine dati.  
  
- Trascinare gli oggetti di database dal [Esplora Server](http://msdn.microsoft.com/library/4ea29b3b-bbb2-45e4-9082-eaf635c41c4d) nel **Progettazione Dataset**.  
  
  È possibile creare un nuovo TableAdapter e configurarlo con un'origine dati mediante il trascinamento di un oggetto TableAdapter dalla casella degli strumenti in un'area vuota nel **Progettazione Dataset** superficie.  
  
  Per un'introduzione agli oggetti TableAdapter, vedere [compilare i set di dati usando oggetti TableAdapter](../data-tools/fill-datasets-by-using-tableadapters.md).  
  
  [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
## <a name="use-the-tableadapter-configuration-wizard"></a>Usare la configurazione guidata TableAdapter  
 Eseguire la **configurazione guidata TableAdapter** per creare o modificare oggetti TableAdapter e le tabelle dati associate. È possibile configurare un oggetto TableAdapter esistente facendo clic su di esso nel **Progettazione Dataset**.  
  
 ![Configurazione guidata adattatore tabella raddata](../data-tools/media/raddata-table-adapter-configuration-wizard.png "raddata configurazione guidata adattatore di tabella")  
  
 Se si trascina un nuovo TableAdapter dalla casella degli strumenti quando la **Progettazione Dataset** presenta lo stato attivo, le istruzioni della procedura guidata è possibile specificare l'origine dati a cui deve connettersi il TableAdapter e i tipi di comandi deve usare per comunicare con il database, le istruzioni SQL o stored procedure. Ciò non visibili se si sta configurando un TableAdapter che è già associato a un'origine dati.  
  
-   Usando il **Crea metodi per inviare aggiornamenti direttamente al database** opzione è equivalente all'impostazione di `GenerateDBDirectMethods` proprietà su true. Questa opzione non è disponibile quando l'istruzione SQL originale non fornisce informazioni sufficienti o se la query non è aggiornabile. Questa situazione può verificarsi, ad esempio, nella **JOIN** query e le query che restituiscono un singolo valore (scalare).  
  
-   È possibile creare una nuova stored procedure nel database sottostante, se si dispone delle autorizzazioni corrette per il database. Se non si dispone di queste autorizzazioni, ciò non è un'opzione.  
  
-   È anche possibile scegliere di eseguire le stored procedure esistenti per il **selezionare**, **Inserisci**, **UPDATE**, e **Elimina** i comandi del TableAdapter. La stored procedure che viene assegnata al **Update** comando, ad esempio, viene eseguito quando il `TableAdapter.Update()` viene chiamato il metodo.  
  
     Mappare i parametri dalla stored procedure selezionata alle colonne corrispondenti nella tabella dati. Ad esempio, se la stored procedure accetta un parametro denominato `@CompanyName` che viene passato al `CompanyName` set di colonne nella tabella, il **colonna di origine** del `@CompanyName` parametro `CompanyName`.  
  
    > [!NOTE]
    >  La stored procedure che è assegnata al comando SELECT viene eseguita chiamando il metodo dell'oggetto TableAdapter tale nome è nel passaggio successivo della procedura guidata. Il metodo predefinito è `Fill`, in modo che il codice che viene in genere utilizzato per l'esecuzione della stored procedure SELECT è `TableAdapter.Fill(tableName)`. Se si modifica il nome predefinito `Fill`, sostituire `Fill` con il nome assegnare e sostituire "TableAdapter" con il nome effettivo dell'oggetto TableAdapter (ad esempio, `CustomersTableAdapter`).  
  
-   Il **opzioni avanzate** della procedura guidata consentono di generare istruzioni INSERT, UPDATE e DELETE in base all'istruzione SELECT su cui viene definito il **genera istruzioni SQL** pagina. Usare la concorrenza ottimistica e specificare se aggiornare la tabella di dati dopo l'inserimento e aggiornamento vengono eseguite le istruzioni.  
  
## <a name="configure-a-tableadapters-fill-method"></a>Configurare il metodo di riempimento di un oggetto TableAdapter  
 In alcuni casi si potrebbe voler modificare lo schema della tabella dell'oggetto TableAdapter. A tale scopo, si modifica primario dell'oggetto TableAdapter `Fill` (metodo). Con il database primario vengono creati oggetti TableAdapter `Fill` metodo che definisce lo schema della tabella dati associata. Il database primario `Fill` metodo si basa sulla query o stored procedure immesse durante la configurazione iniziale del TableAdapter. È il primo metodo (in primo piano) sotto la tabella di dati in Progettazione DataSet.  
  
 ![TableAdapter con più query](../data-tools/media/tableadapter.gif "TableAdapter")  
  
 Tutte le modifiche apportate all'oggetto TableAdapter principale del `Fill` metodo vengono riflesse nello schema della tabella dati associata. Ad esempio la rimozione di una colonna dalla query principale `Fill` metodo rimuove anche la colonna dalla tabella dati associata. Inoltre, rimuovere la colonna dalla principale `Fill` metodo rimuove la colonna da qualsiasi altra query per tale oggetto TableAdapter.  
  
 È possibile utilizzare la configurazione guidata Query TableAdapter per creare e modificare query aggiuntive per l'oggetto TableAdapter. Queste query aggiuntive devono essere conformi allo schema della tabella, a meno che non restituiscono un valore scalare.  Le ulteriori query che hanno un nomi specificati (ad esempio, `CustomersTableAdapter.FillByCity(NorthwindDataSet.Customers, "Seattle")`.)  
  
#### <a name="to-start-the-tableadapter-query-configuration-wizard-with-a-new-query"></a>Per avviare la configurazione guidata Query TableAdapter con una nuova query  
  
1.  Aprire il set di dati in **Progettazione DataSet**.  
  
2.  Se si sta creando una nuova query, trascinare un **Query** dall'oggetto il **set di dati** scheda della finestra di **della casella degli strumenti** in un <xref:System.Data.DataTable>, o selezionare **Aggiungi Query**dal menu di scelta rapida dell'oggetto TableAdapter. È anche possibile trascinare un **Query** oggetto in un'area vuota del **Progettazione Dataset**, che consente di creare un oggetto non associato a un TableAdapter <xref:System.Data.DataTable>. Queste query possono restituire valori singoli (scalari) oppure eseguire UPDATE, INSERT, o solo eliminare comandi sul database.  
  
3.  Nel **Seleziona connessione dati** schermata, selezionare o creare la connessione che userà la query.  
  
    > [!NOTE]
    >  Questa schermata viene visualizzata solo quando la finestra di progettazione non è possibile stabilire la connessione appropriata da utilizzare oppure quando non vi sono connessioni disponibili.  
  
4.  Nel **scegliere un tipo di comando** schermata, seleziona uno dei seguenti metodi di recupero dei dati dal database:  
  
    -   **Usare le istruzioni SQL** consente di digitare un'istruzione SQL per selezionare i dati dal database.  
  
    -   **Crea nuova stored procedure** Abilita per la creazione guidata crei una nuova stored procedure (database) in base all'istruzione SELECT specificata.  
  
    -   **Usare le stored procedure esistenti** consente di eseguire una stored procedure esistente quando si esegue la query.  
  
#### <a name="to-start-the-tableadapter-query-configuration-wizard-on-an-existing-query"></a>Per avviare la configurazione guidata Query TableAdapter in una query esistente  
  
-   Se si sta modificando una query TableAdapter esistente, fare doppio clic su query e quindi scegliere **configura** dal menu di scelta rapida.  
  
    > [!NOTE]
    >  Pulsante destro del mouse la query principale di un oggetto TableAdapter riconfigura TableAdapter e <xref:System.Data.DataTable> dello schema. Pulsante destro del mouse su una query aggiuntiva in un oggetto TableAdapter, configura, tuttavia, solo la query selezionata. Il **configurazione guidata TableAdapter** riconfigura la definizione di TableAdapter, mentre la configurazione guidata Query TableAdapter riconfigura solo la query selezionata.  
  
#### <a name="to-add-a-global--query-to-a-tableadapter"></a>Per aggiungere una query globali a un oggetto TableAdapter  
  
-   *Query globali* sono le query SQL che restituiscono un singolo valore (scalare) o nessun valore. In genere, funzioni globali di eseguono operazioni di database, ad esempio inserimenti, aggiornamenti, Elimina. Inoltre, vengono aggregate informazioni, ad esempio un conteggio di clienti in una tabella o gli addebiti totali per tutti gli elementi in un ordine particolare.  
  
     Per aggiungere query globali mediante il trascinamento di un **Query** dall'oggetto il **set di dati** scheda della finestra di **della casella degli strumenti** in un'area vuota del **Progettazione Dataset**.  
  
-   Fornire una query che esegue l'attività desiderata, ad esempio, `SELECT COUNT(*) AS CustomerCount FROM Customers`.  
  
    > [!NOTE]
    >  Il trascinamento di un **Query** dell'oggetto direttamente nel **Progettazione Dataset** crea un metodo che restituisce solo un valore scalare (singolo). Mentre la query o stored procedure selezionata potrebbe restituire più di un singolo valore, il metodo che viene creato dalla procedura guidata restituisce solo un singolo valore. Ad esempio, la query potrebbe restituire la prima colonna della prima riga dei dati restituiti.  
  
## <a name="see-also"></a>Vedere anche  
 [Compilare i set di dati usando oggetti TableAdapter](../data-tools/fill-datasets-by-using-tableadapters.md)
