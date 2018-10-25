---
title: Panoramica dei dati locali | Microsoft Docs
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
- SQL Server Express
- local data
- SQL Server LocalDB
- LocalDB
- SQLEXPRESS
- SQL Server, local data
- SQL Express
- SQL Server Compact
- data access [Visual Studio], troubleshooting
- Access, .mdb files in Visual Studio
- data [Visual Studio], local
ms.assetid: d6afa5ac-2bb8-49f2-a50e-f71f611ed506
caps.latest.revision: 71
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 94b3f066a66a380875609b4f6485d56a19ebde3e
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49885577"
---
# <a name="local-data-overview"></a>Cenni preliminari sui dati locali
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Quando si sviluppano applicazioni di dati, è in genere consigliabile usare una copia locale di un database, in modo che non vengano inseriti gli errori nei dati di produzione. Anche un database di prova di condivisione con altri sviluppatori consente di creare potenziali problemi, se due sviluppatori introducano errori che interagiscono in modi difficile da rilevare. È possibile evitare tutti questi problemi usando i propri dati di test nel computer locale. La maggior parte se non tutti i sistemi di database consentono di creare file di dati locali. Per i progetti .NET, Visual Studio offre uno speciale supporto per file di database SQL Server locali (con estensione mdf) e file di database Microsoft Access (mdb).  
  
 Visual Studio supporta questi scenari:  
  
1.  
  
2.  
  
- 
  
- 
  
- Creare un progetto di database di SQL Server facendo clic sul nodo della soluzione in Esplora soluzioni e scegliendo **Aggiungi &#124; nuovo progetto**.  Nel riquadro sinistro, scegliere **SQL Server &#124; Database** del progetto e fare clic su OK. In Esplora soluzioni fare clic con il pulsante destro sul nodo del progetto di database per importare un file di database locale, quindi sviluppare l'applicazione che si connette al database generato dal progetto. Soluzione idonea durante lo sviluppo e la modifica dello schema del database allo stesso tempo che si sviluppa l'applicazione.  
  
   ![Importa Database nel progetto di Database](../data-tools/media/raddata-import-database-into-database-project.png "raddata Database di importazione nel progetto di Database")  
  
- Se si sta creando un nuovo database, aggiungere prima di tutto una **file di database basato sul servizio** al progetto (**progetto &#124; Aggiungi nuovo elemento)**. Ciò consente di creare un nuovo file con estensione mdf che viene collegato all'istanza di SQL Server predefinita nel computer locale, che per impostazione predefinita è \MSSQLocalDB (localdb). Il database risulterà in Esplora Server. Espandere il nodo e fare doppio clic sui nodi per aggiungere nuovi oggetti di database quali tabelle, viste, funzioni e così via.  
  
  Per altre informazioni su SQL Server Express LocalDB, vedere [Introduzione a LocalDB, un SQL Express migliore](http://go.microsoft.com/fwlink/?LinkId=234375) e [LocalDB: Dov'è il Database?](http://go.microsoft.com/fwlink/?LinkId=234376) del sito Web Microsoft.  
  
  Nella tabella seguente sono forniti i collegamenti agli argomenti che descrivono come connettere l'applicazione ai dati locali:  
  
|Argomento|Descrizione|  
|-----------|-----------------|  
|[Creare un database SQL tramite una finestra di progettazione](../data-tools/create-a-sql-database-by-using-a-designer.md)|Vengono fornite istruzioni dettagliate per la creazione di un file di database locale che può essere utilizzato per verificare le funzionalità dei dati e la compilazione di applicazioni.|  
|[Procedura dettagliata: connessione ai dati in un file di database lodale (Windows Form)](../data-tools/walkthrough-connecting-to-data-in-a-local-database-file-windows-forms.md)|Vengono fornite istruzioni dettagliate per la connessione a un database LocalDB di SQL Server Express durante la creazione di una semplice applicazione per Windows.|  
|[Connettersi ai dati in un database di Access (Windows Form)](../data-tools/connect-to-data-in-an-access-database-windows-forms.md)|Vengono fornite istruzioni dettagliate per la connessione a un database di Microsoft Access.|  
|[Procedura: Connettersi al database Northwind](../data-tools/how-to-connect-to-the-northwind-database.md)|Vengono fornite istruzioni per la connessione al database di esempio Northwind [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], SQL Server Compact, SQL Server Express e Access.|  
  
## <a name="use-the-connection-string"></a>Usare la stringa di connessione  
 Questo è l'approccio più semplice ed è un'ottima scelta quando l'applicazione legge solo dal database e quando si usa database di terze parti. Il file di database possa essere situato in qualsiasi punto nel computer locale che l'applicazione dispone dell'autorizzazione per accedere e che supporta il sistema di database.  
  
1.  (Facoltativo) Creare una nuova connessione, come descritto in [aggiungere le nuove connessioni](../data-tools/add-new-connections.md). Per i database di terze parti e i file con estensione mdf per il quale già conosce la stringa di connessione e non verrà eseguire Data Binding o utilizzando un'origine dati, ad esempio le classi di Entity Framework o set di dati, questo passaggio non è necessario. Usare solo la stringa di connessione per connettersi al file locale. Per i file con estensione mdf, vedere [aggiornare i file con estensione mdf](../data-tools/upgrade-dot-mdf-files.md) e [stabilire una connessione](https://msdn.microsoft.com/en-us/library/ms254507.aspx).  
  
2.  (Facoltativo) Se si usa i set di dati, Entity Framework o LINQ to SQL, quindi creare l'origine dati tramite la configurazione guidata origine dati. Per altre informazioni, vedere [Add new data sources](../data-tools/add-new-data-sources.md) (Aggiungere nuove origini dati).  
  
## <a name="add-an-existing-mdf-to-your-project"></a>Aggiungere un file con estensione mdf esistente al progetto  
 Se l'applicazione verrà inserimento, eliminazione o aggiornamento dei dati e si vuole conservare una copia del file originale disponibile, quindi è consigliabile aggiungere il file al progetto. Quando si esegue questa operazione, è possibile impostare la proprietà item su di esso per **copia in Directory di Output** al **Copia sempre** oppure **copia se più recente**e sviluppare l'applicazione. Ogni volta che si compila l'applicazione, il database originale viene copiato nella cartella di output e le modifiche dell'applicazione vengono eseguite sulla copia. In questo modo che si ha sempre una copia pulita dei dati originali.  
  
1.  Uso **Esplora File Windows** trascinare e rilasciare il file con estensione mdf dalla posizione corrente nel nodo del progetto in Esplora soluzioni in Visual Studio.  Se il file è già collegato a un'istanza di Local DB, è necessario rimuoverlo prima di tutto. Dopo l'eliminazione nel progetto, Visual Studio verrà automaticamente collegarlo all'istanza predefinita localDB.  
  
2.  Fare doppio clic sul nuovo nodo database e scegliere Proprietà. Selezionare il comportamento di copia, ovvero **Copia sempre** oppure **copia se più recente**.  
  
## <a name="create-a-sql-server-database-project-and-import-your-database"></a>Creare un progetto di database di SQL Server e importare il database  
 Questa è una scelta ottimale quando si svilupperà il database stesso, magari aggiungendo colonne o tabelle o modificando i tipi di dati.  
  
## <a name="each-project-contains-two-copies-of-the-database"></a>Ciascun progetto contiene due copie del database  
 Quando si compila un progetto, il file di database può essere copiato dalla cartella radice del progetto nell'output, **bin**, cartella. Questo comportamento dipende il **Copy to Output Directory** proprietà del file e il valore predefinito di tale proprietà dipende dal tipo di file di database in uso.  
  
 Per visualizzare il **bin** cartella **Esplora soluzioni**, scegliere il **Mostra tutti i file** pulsante sulla barra degli strumenti.  
  
> [!NOTE]
>  Il **Copy to Output Directory** proprietà non è applicabile a web o i progetti C++.  
  
 Il file di database nella cartella radice del progetto viene modificato solo quando si modifica lo schema di database o i dati mediante **Esplora Server**/**Database Explorer** o altri [Visual Strumenti di database](http://msdn.microsoft.com/en-us/6b145922-2f00-47db-befc-bf351b4809a1).  
  
 Quando si modificano i dati durante lo sviluppo di applicazioni, si sta modificando il database di **bin** cartella. Se, ad esempio, si preme il tasto F5 per eseguire il debug dell'applicazione, si verrà connessi al database nella cartella.  
  
|Valore del **Copy to Output Directory** proprietà|Comportamento|  
|----------------------------------------------------|--------------|  
|**Copia se più recente** (valore predefinito per i file sdf)|Il file di database viene copiato dalla directory del progetto per la **bin** directory la prima volta che si compila il progetto. Il **Data ultima modifica** proprietà dei file viene quindi confrontato con ogni volta che si compila il progetto nuovamente. Se il file nella cartella del progetto è più recente, viene copiato per la **bin** cartella, sostituendo il file precedente. In caso contrario, non viene copiato alcun file. **Attenzione:** se ne sconsiglia questo valore per i file con estensione mdb o mdf. Il file di database può essere modificato anche se i dati non cambiano. Il file può essere contrassegnato come più recente semplicemente aprendo una connessione (ad esempio, espandere la **tabelle** nodo **Esplora Server**).|  
|**Copia sempre** (valore predefinito per i file con estensione mdf e mdb)|Il file di database viene copiato dalla directory del progetto per la **bin** directory ogni volta che si compila l'applicazione. Tutte le modifiche apportate al file di dati nella cartella di output vengono sovrascritte durante la successiva esecuzione dell'applicazione.|  
|**Non copiare**|Il sistema non viene mai sovrascritto il file nei **bin** directory. L'applicazione crea una stringa di connessione dinamica che punta al file di database nella directory di output. Pertanto, è necessario copiare manualmente il file nella directory di output se si desidera che i dati nella directory di output corrispondano ai dati nella directory del progetto.|  
  
## <a name="common-issues-with-local-data"></a>Problemi comuni dei dati locali  
 Nella tabella riportata di seguito sono fornite spiegazioni sui problemi comuni che potrebbero verificarsi quando si utilizzano file di dati locali.  
  
|Problema|Descrizione|  
|-----------|-----------------|  
|Ogni volta che viene eseguito il test dell'applicazione e vengono modificati i dati, le modifiche vengono perse quando si esegue nuovamente l'applicazione.|Il valore della **copia in Directory di Output** proprietà è **copia se più recente** oppure **Copia sempre**. Il database della cartella di output verrà sovrascritto (il database che è stato modificato durante il test dell'applicazione) tutte le volte che si compila un progetto. Per altre informazioni, vedere [procedura: gestire i file di dati locale in un progetto](../data-tools/how-to-manage-local-data-files-in-your-project.md).|  
|Viene visualizzato un messaggio che indica che il file di dati è bloccato.|Access (file mdb): verificare che il file non sia aperto in un altro programma, ad esempio Access.<br /><br /> SQL Server Express (file mdf): in SQL Express il file di dati viene bloccato se si tenta di copiare, spostare o rinominare lo stesso file di dati all'esterno dell'IDE di Visual Studio.|  
|L'accesso viene negato se il tentativo di accesso allo stesso database viene effettuato da più utenti contemporaneamente.|Visual Studio sfrutta *le istanze utente*, che è una funzionalità di SQL Server Express che crea un'istanza separata di SQL Server per ogni utente. Dopo che un utente ha eseguito l'accesso al file, nessun utente successivo sarà in grado di effettuare la connessione. Questo problema può verificarsi se, ad esempio, si tenta di eseguire un'applicazione Web in ASP.NET Development Server e IIS (Internet Information Service) contemporaneamente, dal momento che IIS in genere viene eseguito con un diverso account.|  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura dettagliata: Connessione ai dati in un File di Database locale (Windows Form)](../data-tools/walkthrough-connecting-to-data-in-a-local-database-file-windows-forms.md)   
 [Connettersi ai dati in un database di Access (Windows Form)](../data-tools/connect-to-data-in-an-access-database-windows-forms.md)