---
title: Visual Studio Data Tools per C++ | Microsoft Docs
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.date: 11/15/2016
ms.topic: conceptual
ms.assetid: 3a3849d9-1bc7-47d1-805e-1755223ccba2
caps.latest.revision: 12
author: jillre
ms.author: jillfra
manager: jillfra
robots: noindex,nofollow
ms.openlocfilehash: ec68d54ced85737d66c64ca2dbf7942ca81e5314
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "72621214"
---
# <a name="visual-studio-data-tools-for-c"></a>Visual Studio Data Tools per C++
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Il linguaggio C++ nativo può spesso fornire le prestazioni più veloci quando si accede alle origini dati. Tuttavia, gli strumenti per i dati per le applicazioni C++ in Visual Studio non sono così ricchi come per le applicazioni .NET. Le finestre origini dati, ad esempio, non possono essere utilizzate per trascinare le origini dati in un'area di progettazione C++. Se è necessario un livello relazionale a oggetti, sarà necessario scrivere un prodotto personalizzato oppure utilizzare un prodotto di terze parti.  Lo stesso vale per le funzionalità di data binding, sebbene le applicazioni che utilizzano la libreria Microsoft Foundation Class possano utilizzare alcune classi di database, insieme a documenti e visualizzazioni, per archiviare i dati in memoria e visualizzarli all'utente. Per ulteriori informazioni, vedere [accesso ai dati in Visual C++](https://msdn.microsoft.com/library/7wtdsdkh.aspx) .

 Per connettersi ai database SQL, le applicazioni C++ native possono usare i driver ODBC e OLE DB e il provider ADO inclusi in Windows.     Questi possono connettersi a qualsiasi database che supporti tali interfacce. Il driver ODBC è lo standard. OLE DB viene fornito per compatibilità con le versioni precedenti. Per ulteriori informazioni su queste tecnologie dati, vedere [Windows Data Access Components](https://msdn.microsoft.com/library/windows/desktop/aa968814\(v=vs.85\).aspx) .

 Per sfruttare le funzionalità personalizzate di SQL Server 2005 e versioni successive, usare il [SQL Server Native Client](https://msdn.microsoft.com/sqlserver/aa937733). Native Client contiene anche il driver ODBC SQL Server e il provider di OLE DB SQL Server in una libreria a collegamento dinamico (DLL) nativa. Supportano le applicazioni che utilizzano API in codice nativo (ODBC, OLE DB e ADO) per Microsoft SQL Server.  SQL Server Native Client viene installato con SQL Server Data Tools. La guida alla programmazione è disponibile qui: [SQL Server Native Client Programming](https://msdn.microsoft.com/library/ms130892.aspx).

## <a name="to-connect-to-localdb-through-odbc-and-sql-native-client-from-a-c-application"></a>Per connettersi al database locale tramite ODBC e SQL Native Client da un'applicazione C++

1. Installare SQL Server Data Tools.

2. Se è necessario un database SQL di esempio a cui connettersi, scaricare il database Northwind e decomprimerlo in una nuova posizione.

3. Utilizzare SQL Server Management Studio per alleghi il file Northwind. MDF decompresso al database locale. Quando SQL Server Management Studio viene avviato, connettersi a (local DB) \MSSQLLocalDB.

    ![Finestra di dialogo connessione di SSMS](../data-tools/media/raddata-ssms-connect-dialog.png "finestra di dialogo di connessione di raddata SSMS")

    Fare quindi clic con il pulsante destro del mouse sul nodo del database locale nel riquadro sinistro e scegliere **Connetti**.

    ![Database di connessione SSMS](../data-tools/media/raddata-ssms-attach-database.png "database di associazione di raddata SSMS")

4. Scaricare l'esempio ODBC Windows SDK e decomprimerlo in una nuova posizione. In questo esempio vengono illustrati i comandi ODBC di base utilizzati per connettersi a un database ed eseguire query e comandi. Per ulteriori informazioni su tali funzioni, vedere [Microsoft Open Database Connectivity (ODBC)](https://msdn.microsoft.com/library/windows/desktop/ms710252\(v=vs.85\).aspx). Quando si carica la soluzione per la prima volta (si trova nella cartella C++), Visual Studio offrirà l'aggiornamento della soluzione alla versione corrente di Visual Studio. Fare clic su **Sì**.

5. Per usare native client, sono necessari il file di intestazione e il file lib. Questi file contengono funzioni e definizioni specifiche per SQL Server, oltre alle funzioni ODBC definite in SQL. h. In **Proprietà progetto**directory di  >  **Properties**  >  **VC + +** aggiungere la directory di inclusione seguente:

   ** \<system drive> : \Programmi\microsoft SQL Server\110\SDK\Include** e questa directory della libreria:

   **C:\Programmi\Microsoft SQL Server\110\SDK\Lib**

6. Aggiungere queste righe in odbcsql. cpp. Il #define impedisce la compilazione di definizioni OLE DB irrilevanti.

   ```
   #define _SQLNCLI_ODBC_
   #include <sqlncli.h>
   ```

    Si noti che l'esempio non usa effettivamente alcuna funzionalità client nativa, quindi i passaggi precedenti non sono necessari per la compilazione e l'esecuzione. Il progetto è ora configurato per l'uso di questa funzionalità. Per altre informazioni, vedere [Programmazione in SQL Server Native Client](https://msdn.microsoft.com/library/ms130892\(v=sql.130\).aspx).

7. Consente di specificare il driver da utilizzare nel sottosistema ODBC. L'esempio passa l'attributo della stringa di connessione del DRIVER in come argomento della riga di comando. In debug delle proprietà del **progetto**  >  **Properties**  >  **Debugging**aggiungere questo argomento del comando:

   ```
   DRIVER="SQL Server Native Client 11.0"
   ```

8. Premere F5 per compilare ed eseguire l'applicazione. Verrà visualizzata una finestra di dialogo dal driver che richiede di immettere un database. Immettere `(localdb)\MSSQLLocalDB` e selezionare **Usa connessione trusted**. Fare clic su **OK**. Verrà visualizzata una console con messaggi che indicano una connessione riuscita. Dovrebbe essere visualizzato anche un prompt dei comandi in cui è possibile digitare un'istruzione SQL. La schermata seguente mostra una query di esempio e i risultati:

    ![Output della query di esempio ODBC](../data-tools/media/raddata-odbc-sample-query-output.png "output della query di esempio ODBC di raddata")

## <a name="see-also"></a>Vedere anche
 [Accesso ai dati in Visual Studio](../data-tools/accessing-data-in-visual-studio.md)
