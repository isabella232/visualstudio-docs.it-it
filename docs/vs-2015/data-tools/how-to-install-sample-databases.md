---
title: 'Procedura: installare database di esempio | Microsoft Docs'
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
- sample databases, Adventure Works
- data [Visual Studio], sample databases
- sample databases, Northwind
- Northwind sample database
- Adventure Works sample database
ms.assetid: ed1291f6-604c-4972-ae22-0345c6dea12e
caps.latest.revision: 56
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 86dd1914b69dc047c6f8fd9b5d531976141b5ded
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47518473"
---
# <a name="how-to-install-sample-databases"></a>Procedura: installare database di esempio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Diversi esempi di dati prevedono come requisito la connessione ai database di esempio Northwind, Pubs e AdventureWorks. È possibile installare e connettersi a questi database tramite le procedure riportate di seguito.  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
## <a name="installing-databases"></a>Installazione dei database  
 Molti esempi di dati richiedono la disponibilità dei database di esempio che possono essere scaricati da siti Web. I database di esempio includono AdventureWorks, Northwind e Pubs.  
  
#### <a name="to-install-the-northwind-and-pubs-sample-databases-for-sql-server"></a>Per installare i database di SQL Server di esempio Northwind e Pubs  
  
1.  Andare alla [Northwind and Pubs Sample Databases](http://go.microsoft.com/fwlink?linkid=64296) sito web.  
  
2.  Scaricare ed eseguire il programma di installazione.  
  
     Il programma di installazione aggiunge una cartella **SQL Server 2000 Sample Databases** nella cartella radice nel computer. (Ad esempio: **C:\SQL Server 2000 Sample Databases**).  
  
3.  Individuare lo script SQL per il database desiderato, Northwind o Pubs.  
  
    > [!WARNING]
    >  Il file di database .MDF non può essere facilmente convertito in un formato utilizzabile nelle versioni correnti di SQL Server, è preferibile usare lo script per creare il database.  
  
4.  Nelle **Esplora Server**, creare una connessione a un'istanza di SQL Server in cui si desidera installare il database. Se non si dispone di un'istanza specifica di SQL Server che si desidera usare, è possibile usare il database che viene installato automaticamente con Visual Studio. A tale scopo, specificare `(localdb)\v11.0` come nome del server.  
  
     Per creare la connessione, effettuare le operazioni seguenti.  
  
    ###### <a name="to-create-a-connection-to-an-instance-of-sql-server"></a>Per creare una connessione a un'istanza di SQL Server  
  
    1.  Nelle **Esplora Server**, aprire il menu di scelta rapida per il **connessioni dati** nodo e scegliere **Aggiungi connessione**.  
  
         Il **Aggiungi connessione** verrà visualizzata la finestra di dialogo.  
  
    2.  Immettere il nome dell'istanza di SQL Server in cui si desidera creare il database Pubs o Northwind o immettere (localdb)\v11.0.  
  
    3.  Sotto **selezionare o immettere un nome di database**, scegliere qualsiasi database nell'elenco, ad esempio, tempdb.  
  
    4.  Scegliere il **Test connessione** per verificare che tutto funzioni, quindi scegliere il **OK** pulsante.  
  
         Verrà visualizzato un nuovo nodo di connessione **Esplora Server**.  
  
5.  Menu di scelta rapida per il nodo della connessione per il server, quindi scegliere il **nuova Query** pulsante.  
  
     Verrà visualizzata una finestra dell'editor con un file di script .sql.  
  
6.  Incollare il contenuto di instnwnd.sql o di instpubs.sql nella finestra dell'editor.  
  
7.  Scegliere il pulsante Esegui query (l'icona del triangolo verde aperto nella parte superiore destra della finestra della query).  
  
     Se la query ha esito positivo, il messaggio **comandi riusciti** viene visualizzata. Ciò significa che il database Northwind o pubs è stato creato.  
  
     È comunque necessario aggiungere una connessione al database di esempio. Nelle **Esplora Server**, aprire il menu di scelta rapida per il **connessioni dati** nodo e scegliere **Aggiungi connessione**.  
  
8.  Scegliere lo stesso database server in cui si è scelto in precedenza, ma questa volta, in, selezionare o immettere un nome di database, scegliere il database Northwind o pubs e scegliere il **OK** pulsante.  
  
     Verrà visualizzato un nuovo nodo in Connessioni dati per il database di esempio.  
  
9. Chiudere la finestra dell'editor e confermare che non si vuole salvare il file di query. Non è necessario salvare lo script di creazione del database dopo aver creato il database.  
  
#### <a name="to-install-the-adventureworks-sample-databases"></a>Per installare il database di esempio AdventureWorks  
  
-   Scaricare il database di esempio AdventureWorks dal [sito CodePlex Web](http://go.microsoft.com/fwlink/?linkid=87843).  
  
#### <a name="to-install-the-northwind-sample-database-for-microsoft-access"></a>Per installare il database di esempio Northwind per Microsoft Access  
  
1.  In Microsoft Access 2010 o versione successiva, cercare online modelli Northwind e scegliere **database di esempio Desktop Northwind 2007**.  
  
2.  In Microsoft Access salvare il file di database come Northwind.accdb.  
  
 La nuova estensione per i database di Access è .accdb. Visualizzare [programmazione dei dati con Microsoft Access 2010](http://msdn.microsoft.com/library/office/ff965871.aspx). Per connettersi al database Northwind tramite Access, vedere [procedura: connettersi al Northwind Database](../data-tools/how-to-connect-to-the-northwind-database.md).  
  
## <a name="net-framework-security"></a>Sicurezza di .NET Framework  
 I database di esempio sono forniti a fini illustrativi e non necessariamente presentano le procedure di sicurezza ottimali.  
  
## <a name="see-also"></a>Vedere anche  
 [Come determinare la versione ed edizione di SQL Server e i relativi componenti](http://support.microsoft.com/kb/321185)   
 [Creare un database SQL usando una finestra di progettazione](../data-tools/create-a-sql-database-by-using-a-designer.md)   
 [Procedura: Connettersi al database Northwind](../data-tools/how-to-connect-to-the-northwind-database.md)