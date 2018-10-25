---
title: 'Procedura: connettersi al Database Northwind | Microsoft Docs'
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
- connections [Visual Studio], Northwind database
- Northwind sample database
ms.assetid: cc6cb79f-d035-41f8-b398-8d4a45922bfb
caps.latest.revision: 29
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 3f64fa378029546f7a3126b324c282f6a91d7231
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49897634"
---
# <a name="how-to-connect-to-the-northwind-database"></a>Procedura dettagliata: connettersi al database Northwind
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Per comprendere come creare applicazioni di database usando Visual Studio, è necessario connettersi al database Northwind per seguire molti degli esempi forniti nella documentazione del prodotto. A seconda dell'esempio che si sta seguendo, verrà effettuata la connessione al database di SQL Server o di un file database, ad esempio uno per Microsoft Access o SQL Server.  
  
## <a name="creating-data-connections-to-the-northwind-database"></a>Creazione delle connessioni dati al database Northwind  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
#### <a name="to-create-a-data-connection-to-the-northwind-database-sql-server"></a>Per creare una connessione dati al database Northwind  
  
1. Nel **View** menu, scegliere **Esplora Server**/**Esplora Database**.  
  
2. Nelle **Esplora Server**/**Esplora Database**, aprire il menu di scelta rapida **connessioni dati** scegliere **Aggiungi connessione**.  
  
    Dopo aver scelto **Aggiungi connessione**, ad esempio le **Scegli origine dati** la finestra di dialogo o la **Aggiungi connessione** verrà visualizzata la finestra di dialogo.  
  
3. Se il **Scegli origine dati** verrà visualizzata la finestra di dialogo, selezionare **Microsoft SQL Server**, quindi scegliere **OK**.  
  
    Se il **Aggiungi connessione** verrà visualizzata la finestra di dialogo e il **zdroj dat** non **Microsoft SQL Server (SqlClient)**, scegliere il **modifica** pulsante per aprire la **Modifica origine dati** finestra di dialogo **Microsoft SQL Server**, quindi scegliere il **OK** pulsante.  
  
4. Nel **nome Server** elenco, specificare il nome del server in cui si trova il database Northwind.  
  
5. In base ai requisiti della versione di SQL Server e il database Northwind, scegliere **usare l'autenticazione di Windows** oppure scegliere **autenticazione di SQL Server** e immettere un nome utente e password per accedere al computer che esegue SQL Server.  
  
6. Scegliere il database Northwind nel **selezionare o immettere un nome di database** elenco.  
  
7. Scegli **Test connessione** per verificare la connettività al database Northwind.  
  
8. Scegliere **OK**.  
  
    Una connessione dati al database Northwind viene aggiunta al **Esplora Server**/**Esplora Database**.  
  
   Oltre a connettersi a un'istanza remota di un database SQL Server, è possibile anche connettersi direttamente ai file effettivi che contengono il database. In questo modo è possibile aggiungere i file di database direttamente in un progetto dove possono essere implementati come parte dell'applicazione. I seguente file di database locali sono attualmente supportati: file di database SQL Server Compact (sdf), [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] e file di database SQL Server Express (. mdf) e i file di database Microsoft Access (mdb o accdb).  
  
#### <a name="to-create-a-data-connection-to-the-northwind-databasesql-server-database-file-mdf"></a>Per creare una connessione dati al database Northwind: file di database SQL Server (.mdf)  
  
1.  Nel **View** menu, scegliere **Esplora Server**/**Esplora Database**.  
  
2.  Nelle **Esplora Server**/**Esplora Database**, aprire il menu di scelta rapida **connessioni dati** scegliere **Aggiungi connessione**.  
  
     Dopo aver scelto **Aggiungi connessione**, ad esempio le **Aggiungi connessione** la finestra di dialogo o la **Scegli origine dati** verrà visualizzata la finestra di dialogo.  
  
3.  Se il **Scegli origine dati** verrà visualizzata la finestra di dialogo, selezionare **File di Database di Microsoft SQL Server**, quindi scegliere il **OK**.  
  
4.  Se il **Aggiungi connessione** verrà visualizzata la finestra di dialogo, verificare che il **zdroj dat** è impostata su **File di Database Microsoft SQL Server (SqlClient)**. Se non è impostata su **File di Database Microsoft SQL Server (SqlClient)**, scegliere **Change** per aprire il **Modifica origine dati** finestra di dialogo scegliere **Microsoft SQL File di Database server**, quindi scegliere il **OK** pulsante.  
  
5.  Scegli **esplorare** per individuare il file con estensione mdf che contiene il database Northwind.  
  
6.  In base ai requisiti della versione del database Northwind, scegliere **usare l'autenticazione di Windows** oppure scegliere **autenticazione di SQL Server** e immettere un nome utente e password per l'accesso alla computer che esegue SQL Server.  
  
7.  Fare clic sul pulsante **OK** .  
  
     Una connessione dati al database Northwind viene aggiunta al **Esplora Server**/**Esplora Database**.  
  
> [!NOTE]
>  [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] ha modifiche che si applicano al file di database Northwind database file (.mdf). Per informazioni, vedere [procedura: installare database di esempio](../data-tools/how-to-install-sample-databases.md).  
  
#### <a name="to-create-a-data-connection-to-the-northwind-databaseaccess-database-file-mdb-or-accdb"></a>Per creare una connessione dati al file di database Northwind o Access (mdb o .accdb)  
  
1.  Nel **View** menu, scegliere **Esplora Server**/**Esplora Database**.  
  
2.  Nelle **Esplora Server**/**Esplora Database**, aprire il menu di scelta rapida **connessioni dati** scegliere **Aggiungi connessione**.  
  
     Dopo aver scelto **Aggiungi connessione**, ad esempio le **Aggiungi connessione** la finestra di dialogo o la **Scegli origine dati** verrà visualizzata la finestra di dialogo.  
  
3.  Se il **Scegli origine dati** verrà visualizzata la finestra di dialogo, selezionare **File di Database Microsoft Access**, quindi scegliere **OK**.  
  
4.  Se il **Aggiungi connessione** verrà visualizzata la finestra di dialogo, verificare che il **zdroj dat** è impostata su **File di Database Microsoft Access**. Se non è impostata su **File di Database Microsoft Access**, scegliere **Change** per aprire il **Modifica origine dati** finestra di dialogo scegliere **Database Microsoft Access File**, quindi scegliere il **OK** pulsante.  
  
5.  Scegli **esplorare** per individuare il file con estensione mdb o accdb che contiene il database Northwind.  
  
6.  Immettere un nome utente e una password se richiesto dalla versione del database Northwind.  
  
7.  Scegliere **OK**.  
  
     Una connessione dati al database Northwind viene aggiunta al **Esplora Server**/**Esplora Database**.  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura: installare database di esempio](../data-tools/how-to-install-sample-databases.md)   
 [Programmazione dei dati con Microsoft Access 2010](http://msdn.microsoft.com/library/office/ff965871.aspx)   
 [Procedure dettagliate di data](http://msdn.microsoft.com/library/15a88fb8-3bee-4962-914d-7a1f8bd40ec4)