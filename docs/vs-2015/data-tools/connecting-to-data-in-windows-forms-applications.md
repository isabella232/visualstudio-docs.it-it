---
title: Connessione ai dati in Windows Forms Application | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- System.Data.SqlClient.SqlConnection
- System.Data.Odbc.OdbcConnection
- System.Data.OleDb.OleDbConnection
- System.Data.OracleClient.OracleConnection
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- connection objects, tools for working with
- OleDbConnection class, ADO.NET connection objects
- databases [Visual Studio], connecting to
- data adapters, connections
- connection pooling, ADO.NET connections
- connection strings [Visual Studio], ADO.NET
- connection objects, types of
- dynamic properties, ADO.NET connections
- connections, about connections
- data [Visual Studio], connecting
- design-time connections
- connections, design-time
- TableAdapters, connections
- connection objects
- SqlConnection class, ADO.NET connection objects
- connecting to databases, ADO.NET connections
- transactions, ADO.NET
- database connections [Visual Studio], ADO.NET
ms.assetid: 184cbd0d-3b26-418d-a11c-f9f8f004fbff
caps.latest.revision: 31
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: d1132ee07e892886e49fbaa4670b309afc448da6
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47532038"
---
# <a name="connecting-to-data-in-windows-forms-applications"></a>Connessione ai dati nelle applicazioni Windows Forms
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] offre strumenti per connettere l'applicazione a dati da molte origini diverse, ad esempio database, servizi Web e oggetti. Se si usano strumenti per la progettazione di dati in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], spesso non occorre creare in modo esplicito un oggetto connessione per il form o il componente. L'oggetto connessione è in genere creato come risultato del completamento di una delle procedure guidate relative ai dati o del trascinamento di oggetti dati nel form. Per connettere l'applicazione ai dati in un database, un servizio web o un oggetto, eseguire la [configurazione guidata origine dati](http://msdn.microsoft.com/library/c4df7de5-5da0-4064-940c-761dd6d9e28f) selezionando **Aggiungi nuova origine dati** dal [finestra Origini dati](http://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992).  
  
 Il diagramma seguente mostra il flusso standard di operazioni durante la connessione a dati tramite l'esecuzione di una query TableAdapter per recuperare dati e visualizzarli in un form in un'applicazione Windows.  
  
 ![Flusso di dati in un'applicazione client](../data-tools/media/clientdatadiagram.gif "ClientDataDiagram")  
  
 In alcune situazioni è utile creare un oggetto connessione senza usare strumenti per la progettazione di dati. Per informazioni sulla creazione di connessioni a livello di codice, vedere [ci si connette a un'origine dati](http://msdn.microsoft.com/library/9abc3f92-1be3-4e1a-b360-762dc689650e).  
  
> [!NOTE]
>  Per informazioni sulla connessione di applicazioni web ai dati, vedere [ASP.NET Data Access Content Map](http://msdn.microsoft.com/en-us/f9219396-a0fa-481f-894d-e3d9c67d64f2).  
  
## <a name="walkthroughs-for-connecting-windows-forms-applications-to-data"></a>Procedure dettagliate per la connessione di applicazioni Windows Forms ai dati  
 Le procedure dettagliate seguenti includono procedure correlate alla connessione ai dati in applicazioni Windows Forms:  
  
-   [Procedura dettagliata: Connessione ai dati in un Database (Windows Form)](http://msdn.microsoft.com/library/02d39aa6-8993-4602-be13-a13536af3d1c)  
  
-   [Procedura dettagliata: connessione ai dati in un file di database lodale (Windows Form)](../data-tools/walkthrough-connecting-to-data-in-a-local-database-file-windows-forms.md)  
  
-   [Procedura dettagliata: Connessione ai dati in un servizio Web (Windows Form)](http://msdn.microsoft.com/library/079fb9b0-c733-40c1-acd1-d0d68834354d)  
  
-   [Procedura dettagliata: Connessione ai dati negli oggetti (Windows Form)](http://msdn.microsoft.com/library/21a7fba2-b38b-4726-8cbe-d22154b75a05)  
  
-   [Connettersi ai dati in un database di Access (Windows Form)](../data-tools/connect-to-data-in-an-access-database-windows-forms.md)  
  
## <a name="creating-connections"></a>Creazione di connessioni  
 Nelle [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], le connessioni vengono configurate mediante il **Aggiungi/Modifica connessione** nella finestra di dialogo. Il **Aggiungi connessione** finestra di dialogo viene visualizzata quando si modificano o si creano connessioni in una delle procedure guidate di data o [Esplora Server/Esplora Database](http://msdn.microsoft.com/library/4ea29b3b-bbb2-45e4-9082-eaf635c41c4d) o quando si modificano le proprietà di connessione in il **proprietà** finestra.  
  
 Le connessioni dati sono configurate automaticamente quando si esegue una delle azioni seguenti.  
  
|Azione|Descrizione|  
|------------|-----------------|  
|Eseguire la [configurazione guidata origine dati](http://msdn.microsoft.com/library/c4df7de5-5da0-4064-940c-761dd6d9e28f).|Le connessioni vengono configurate quando si sceglie il percorso del database nel **configurazione guidata origine dati**. Per altre informazioni, vedere [procedura: connettersi ai dati in un Database](../data-tools/how-to-connect-to-data-in-a-database.md).|  
|Eseguire la [configurazione guidata TableAdapter](http://msdn.microsoft.com/library/3a373dd9-7b34-4d3c-a48b-69414512bac8).|Le connessioni vengono create all'interno di **configurazione guidata TableAdapter**. Per altre informazioni, vedere [creare e configurare oggetti TableAdapter](../data-tools/create-and-configure-tableadapters.md).|  
|Eseguire la [modifica di TableAdapter](../data-tools/editing-tableadapters.md).|Le connessioni vengono create all'interno di **configurazione guidata Query TableAdapter**. Per altre informazioni, vedere [procedura: creare query TableAdapter](../data-tools/how-to-create-tableadapter-queries.md).|  
|Trascinare gli elementi dal [finestra Origini dati](http://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992) in un form o nella [Component Designer](http://msdn.microsoft.com/library/61a3a450-5b15-465e-bd9a-72a6c8c2b282).|Oggetti connessione vengono creati quando si trascinano elementi dal **Zdroje dat** finestra nel **progettazione form di Windows** oppure **Component Designer**. Per altre informazioni, vedere [associare controlli ai dati in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md).|  
|Aggiungere nuove connessioni dati a [Esplora Server/Esplora Database](http://msdn.microsoft.com/library/4ea29b3b-bbb2-45e4-9082-eaf635c41c4d).|Le connessioni dati in **Esplora Server/Esplora Database** vengono visualizzati nell'elenco delle connessioni disponibili nelle procedure guidate dei dati|  
  
## <a name="connection-strings"></a>Stringhe di connessione  
 Le stringhe di connessione possono essere archiviate nell'applicazione compilata o nel file di configurazione dell'applicazione. Per altre informazioni, vedere [procedura: salvare e modificare le stringhe di connessione](~/E:/Repos/visualstudio-docs-pr/docs/data-tools/how-to-save-and-edit-connection-strings.md).  
  
## <a name="connection-information-and-security"></a>Informazioni di connessione e sicurezza  
 Poiché la creazione di una connessione comporta l'accesso a una risorsa importante, ovvero un database, la configurazione e l'uso di una connessione presentano spesso problemi di sicurezza.  
  
 Il livello di sicurezza dell'applicazione e dell'accesso all'origine dati dipende dall'architettura del sistema. In un'applicazione basata su Web, ad esempio, gli utenti ottengono in genere l'accesso anonimo a Internet Information Services (IIS) e non forniscono quindi credenziali di sicurezza. In questo caso, l'applicazione gestisce e usa le proprie informazioni di accesso, invece di usare informazioni utente specifiche, per aprire le connessioni e accedere al database.  
  
> [!IMPORTANT]
>  L'archiviazione dei dettagli relativi alle stringhe di connessione, ad esempio una, può influire sulla sicurezza dell'applicazione. La sicurezza integrata di Windows consente di controllare l'accesso a un database in modo più sicuro. Per altre informazioni, vedere [Protezione delle informazioni di connessione](http://msdn.microsoft.com/library/1471f580-bcd4-4046-bdaf-d2541ecda2f4).  
  
 In applicazioni Intranet o a più livelli è possibile usare l'opzione di sicurezza integrata offerta da Windows, IIS e SQL Server. In questo modello le credenziali di autenticazione di un utente per la rete locale sono usate anche per accedere alle risorse del database e nella stringa di connessione non si usano password o nomi utente espliciti. Le autorizzazioni sono in genere definite nel computer server di database tramite i gruppi. Non sarà quindi necessario definire autorizzazioni individuali per ogni utente che potrebbe accedere al database. In questo modello non occorre archiviare le informazioni di accesso per la connessione e non sono necessari passaggi aggiuntivi per proteggere le informazioni della stringa di connessione.  
  
 Per altre informazioni sulla sicurezza, vedere gli argomenti seguenti:  
  
-   [Protezione delle applicazioni ADO.NET](http://msdn.microsoft.com/library/005a1d43-6ee5-471e-ad98-1d30a44d49d5)  
  
-   [Accesso più sicuro a file e dati in Windows Form](http://msdn.microsoft.com/library/3cd3e55b-2f5e-40dd-835d-f50f7ce08967)  
  
## <a name="design-time-connections-in-server-explorerdatabase-explorer"></a>Connessioni in fase di progettazione in Esplora server/Esplora database  
 **Esplora server/Esplora Database** fornisce un modo per creare connessioni in fase di progettazione alle origini dati. Sarà quindi possibile esplorare le origini dati disponibili, visualizzare informazioni su tabelle, colonne e altri elementi in esse contenuti e infine modificare e creare elementi di database.  
  
 L'applicazione non utilizza direttamente le connessioni disponibili nel **Esplora Server/Esplora Database**. Queste connessioni sono usate da [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] per operazioni relative al database in fase di progettazione. Per altre informazioni, vedere [Visual Database Tools](http://msdn.microsoft.com/en-us/6b145922-2f00-47db-befc-bf351b4809a1).  
  
 In fase di progettazione, ad esempio, è possibile utilizzare **Esplora Server/Esplora Database** per creare una connessione a un database. In un secondo momento, quando si progetta un form, è possibile passare al database, selezionare le colonne da una tabella e trascinarle nel [Progettazione Dataset](../data-tools/creating-and-editing-typed-datasets.md). Ciò consente di creare un [TableAdapter](../data-tools/tableadapter-overview.md) nel set di dati. oltre a creare un nuovo oggetto connessione, che fa parte del TableAdapter appena creato.  
  
 Le informazioni sulle connessioni in fase di progettazione sono archiviate nel computer locale in modo indipendente rispetto a in progetto specifico o una particolare soluzione. Di conseguenza, dopo aver stabilito una connessione in fase di progettazione mentre si lavora in un'applicazione, viene visualizzato nella **Esplora Server/Esplora Database** ogni volta che si lavora in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], purché il server a cui la connessione punti è disponibile. Per altre informazioni, vedere [procedura: connettersi a un Database da Esplora Server](http://msdn.microsoft.com/en-us/7c1c3067-0d77-471b-872b-639f9f50db74).  
  
 [!INCLUDE[SQLObjectExplorer](../includes/sqlobjectexplorer-md.md)]  
  
## <a name="see-also"></a>Vedere anche  
 [Connessione ai dati in Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Procedura: Connettersi ai dati di un database](../data-tools/how-to-connect-to-data-in-a-database.md)   
 [Procedura dettagliata: Connessione ai dati in un Database (Windows Form)](http://msdn.microsoft.com/library/02d39aa6-8993-4602-be13-a13536af3d1c)   
 [Mappa del contenuto per l'accesso dei dati di ASP.NET](http://msdn.microsoft.com/en-us/f9219396-a0fa-481f-894d-e3d9c67d64f2)   
 [Preparare l'applicazione per ricevere dati](http://msdn.microsoft.com/library/c17bdb7e-c234-4f2f-9582-5e55c27356ad)   
 [Recupero di dati nell'applicazione](../data-tools/fetching-data-into-your-application.md)   
 [Associazione di controlli ai dati in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Modifica dei dati nell'applicazione](../data-tools/editing-data-in-your-application.md)   
 [La convalida dei dati](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)   
 [Salvataggio di dati](../data-tools/saving-data.md)