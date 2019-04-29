---
title: Data tools perC++
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CPP
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
- cplusplus
ms.openlocfilehash: 5157f1d6a851e0784e79dfbfe5b94aef0490a026
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62565242"
---
# <a name="visual-studio-data-tools-for-c"></a>Visual Studio Data Tools per C++

C++ nativo può spesso fornire prestazioni ottimali quando si accede a origini dati. Tuttavia, i dati degli strumenti per le applicazioni C++ in Visual Studio non avanzati come nel caso di applicazioni .NET. Ad esempio, il **Zdroje dat** finestra non può essere usata per trascinamento della selezione di origini dati in un C++ nell'area di progettazione. Se è necessario un livello relazionale a oggetti, sarà necessario scriverne uno proprio, oppure utilizzare un prodotto di terze parti. Lo stesso vale per la funzionalità di data binding, sebbene le applicazioni che usano la libreria Microsoft Foundation Class è possono usare alcune classi di database, insieme ai documenti e visualizzazioni, per archiviare i dati in memoria e la visualizza all'utente. Per altre informazioni, vedere [l'accesso ai dati in Visual C++](/cpp/data/data-access-in-cpp).

Per connettersi al database SQL, le applicazioni C++ native possono usare i driver ODBC e OLE DB e il provider ADO che sono inclusi in Windows. Questi possono connettersi a qualsiasi database che supporta tali interfacce. Il driver ODBC è lo standard. OLE DB viene fornito per compatibilità con le versioni precedenti. Per altre informazioni su queste tecnologie di dati, vedere [Windows Data Access Components](/previous-versions/windows/desktop/ms692897(v=vs.85)).

Per sfruttare i vantaggi di funzionalità personalizzate in SQL Server 2005 e versioni successive, usare il [SQL Server native client](/sql/relational-databases/native-client/sql-server-native-client). Il client nativo contiene anche il driver ODBC di SQL Server e il provider OLE DB per SQL Server in una libreria di collegamento dinamico (DLL). Che supportano applicazioni che utilizzano API in codice nativo (ODBC, OLE DB e ADO) per Microsoft SQL Server. SQL Server Native Client viene installato con SQL Server Data Tools. La Guida di programmazione è qui: [Programmazione client nativo di SQL Server](/sql/relational-databases/native-client/sql-server-native-client-programming).

## <a name="to-connect-to-localdb-through-odbc-and-sql-native-client-from-a-c-application"></a>Per connettersi al database locale tramite ODBC e SQL Native Client da un'applicazione C++

1. Installare SQL Server Data Tools.

2. Se è necessario un database SQL di esempio a cui connettersi, scaricare il database Northwind e decomprimerlo in una nuova posizione.

3. Usare SQL Server Management Studio per collegare il decompresso *mdf* file a localDB. All'avvio di SQL Server Management Studio, connettersi a (localdb) \MSSQLLocalDB.

   ![Finestra di dialogo connessione a SSMS](../data-tools/media/raddata-ssms-connect-dialog.png)

   Pulsante destro del mouse sul nodo database locale nel riquadro sinistro, quindi scegliere **Attach**.

   ![SQL Server Management Studio Collega database](../data-tools/media/raddata-ssms-attach-database.png)

4. Scaricare l'esempio di ODBC Windows SDK e decomprimerlo in una nuova posizione. In questo esempio mostra i comandi di base ODBC che consentono di connettersi a un database ed eseguire query e comandi. Altre informazioni su queste funzioni nel [Microsoft Open Database Connectivity (ODBC)](/sql/odbc/microsoft-open-database-connectivity-odbc). Quando si carica innanzitutto la soluzione (si trova nella cartella di C++), Visual Studio offre aggiornare la soluzione per la versione corrente di Visual Studio. Scegliere **Sì**.

5. Per usare il client nativo, è necessario relativo *intestazione* file e *lib* file. Questi file contengono le funzioni e le definizioni specifiche per SQL Server, oltre a funzioni ODBC definite in SQL. h. Nelle **progetto** > **delle proprietà** > **cartelle VC + +**, aggiungere le seguenti directory di inclusione:

   **%ProgramFiles%\Microsoft SQL Server\110\SDK\Include**

   E questa directory di libreria:

   **%ProgramFiles%\Microsoft SQL Server\110\SDK\Lib**

6. Aggiungere le righe seguenti in *odbcsql.cpp*. Il #define impedisce che le definizioni di OLE DB irrilevanti venga compilato.

   ```cpp
   #define _SQLNCLI_ODBC_
   #include <sqlncli.h>
   ```

    Si noti che il codice di esempio non utilizza effettivamente tutte le funzionalità native client, pertanto non sono necessari per poter compilare ed eseguire i passaggi precedenti. Ma il progetto è ora configurato per poter usare questa funzionalità. Per altre informazioni, vedere [Programmazione in SQL Server Native Client](/sql/relational-databases/native-client/sql-server-native-client).

7. Specificare il driver da usare nel sottosistema ODBC. L'esempio passa l'attributo di stringa di connessione del DRIVER in come un argomento della riga di comando. Nelle **Project** > **delle proprietà** > **debug**, aggiungere questo argomento di comando:

   ```cpp
   DRIVER="SQL Server Native Client 11.0"
   ```

8. Premere **F5** per compilare ed eseguire l'applicazione. Si deve visualizzare una finestra di dialogo del driver che viene richiesto di immettere un database. Immettere `(localdb)\MSSQLLocalDB`e controllare **Usa connessione Trusted**. Fare clic su **OK**. Verrà visualizzata una console con i messaggi che indicano una connessione riuscita. È visualizzato anche un prompt dei comandi in cui è possibile digitare in un'istruzione SQL. La schermata seguente mostra un esempio di query e i risultati:

   ![Output della query di esempio ODBC](../data-tools/media/raddata-odbc-sample-query-output.png)

## <a name="see-also"></a>Vedere anche

- [Accesso ai dati in Visual Studio](../data-tools/accessing-data-in-visual-studio.md)