---
title: Strumenti dati per C++
description: Esplorare Visual Studio strumenti dati per C++. Connessione a localDB tramite ODBC e SQL client nativo da un'applicazione C++.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: overview
dev_langs:
- CPP
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: vs-data-tools
ms.workload:
- data-storage
- cplusplus
ms.openlocfilehash: 8376adeeedbb4bbdae10d147573799813da95bec
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126631080"
---
# <a name="visual-studio-data-tools-for-c"></a>Visual Studio Data Tools per C++

C++ nativo può spesso offrire le prestazioni più veloci quando si accede alle origini dati. Tuttavia, gli strumenti di dati per le applicazioni C++ in Visual Studio non sono così ricchi come per le applicazioni .NET. Ad esempio, la **finestra Origini dati** non può essere usata per trascinare e rilasciare origini dati in un'area di progettazione C++. Se è necessario un livello relazionale a oggetti, è necessario scriverlo o usare un prodotto di terze parti. Lo stesso vale per la funzionalità di data binding, anche se le applicazioni che usano la libreria Microsoft Foundation Class possono usare alcune classi di database, insieme a documenti e viste, per archiviare i dati in memoria e visualizzarli all'utente. Per altre informazioni, vedere [Accesso ai dati in Visual C++](/cpp/data/data-access-in-cpp).

Per connettersi SQL database, le applicazioni C++ native possono usare i driver ODBC e OLE DB e il provider ADO inclusi in Windows. Possono connettersi a qualsiasi database che supporta tali interfacce. Il driver ODBC è lo standard. OLE DB viene fornito per la compatibilità con le versioni precedenti. Per altre informazioni su queste tecnologie di dati, vedere Windows [componenti di accesso ai dati](/previous-versions/windows/desktop/ms692897(v=vs.85)).

Per sfruttare le funzionalità personalizzate in SQL Server 2005 e versioni successive, usare SQL Server [client nativo.](/sql/relational-databases/native-client/sql-server-native-client) Il client nativo contiene anche il driver ODBC SQL Server e il provider SQL Server OLE DB in una libreria a collegamento dinamico (DLL) nativa. Queste applicazioni supportano l'uso di API di codice nativo (ODBC, OLE DB e ADO) per Microsoft SQL Server. SQL Server Native Client con SQL Server Data Tools. La guida per programmatori è disponibile qui: SQL Server [programmazione client nativa.](/sql/relational-databases/native-client/sql-server-native-client-programming)

## <a name="to-connect-to-localdb-through-odbc-and-sql-native-client-from-a-c-application"></a>Per connettersi a localDB tramite ODBC e SQL Native Client da un'applicazione C++

1. Installare SQL Server Data Tools.

2. Se è necessario un database SQL di esempio a cui connettersi, scaricare il database Northwind e decomprimerlo in un nuovo percorso.

3. Usare SQL Server Management Studio per collegare il file *Northwind.mdf* decompresso a localDB. Quando SQL Server Management Studio, connettersi a (localdb)\MSSQLLocalDB.

   ![SSMS dialogo Connetti](../data-tools/media/raddata-ssms-connect-dialog.png)

   Fare quindi clic con il pulsante destro del mouse sul nodo localdb nel riquadro sinistro e scegliere **Collega**.

   ![SSMS database collegato](../data-tools/media/raddata-ssms-attach-database.png)

4. Scaricare l'Windows SDK odbc e decomprimerlo in un nuovo percorso. Questo esempio illustra i comandi ODBC di base usati per connettersi a un database ed eseguire query e comandi. Altre informazioni su queste funzioni sono disponibili in [Microsoft Open Database Connectivity (ODBC)](/sql/odbc/microsoft-open-database-connectivity-odbc). Quando si carica per la prima volta la soluzione (si tratta della cartella C++), Visual Studio offrirà di aggiornare la soluzione alla versione corrente di Visual Studio. Fare clic su **Sì**.

5. Per usare il client nativo, sono necessari il file *di intestazione* e il file *lib.* Questi file contengono funzioni e definizioni specifiche SQL Server, oltre alle funzioni ODBC definite in sql.h. In **Project**  >  **proprietà VC++**  >  **directory** aggiungere la directory di inclusione seguente:

   **%ProgramFiles%\Microsoft SQL Server\110\SDK\Include**

   E questa directory della libreria:

   **%ProgramFiles%\Microsoft SQL Server\110\SDK\Lib**

6. Aggiungere queste righe in *odbcsql.cpp*. Il #define impedisce la compilazione di definizioni OLE DB irrilevanti.

   ```cpp
   #define _SQLNCLI_ODBC_
   #include <sqlncli.h>
   ```

    Si noti che nell'esempio non viene effettivamente utilizzata alcuna funzionalità client nativa, pertanto i passaggi precedenti non sono necessari per la compilazione e l'esecuzione. Ma il progetto è ora configurato per l'uso di questa funzionalità. Per altre informazioni, vedere SQL Server Native Client [programmazione .](/sql/relational-databases/native-client/sql-server-native-client)

7. Specificare il driver da usare nel sottosistema ODBC. L'esempio passa l'attributo della stringa di connessione DRIVER in come argomento della riga di comando. In **Project**  >  **debug**  >  **delle** proprietà aggiungere questo argomento del comando:

   ```cpp
   DRIVER="SQL Server Native Client 11.0"
   ```

8. Premere **F5** per compilare ed eseguire l'applicazione. Verrà visualizzata una finestra di dialogo del driver che richiede di immettere un database. Immettere `(localdb)\MSSQLLocalDB` e selezionare Usa connessione **attendibile**. Fare clic su **OK**. Verrà visualizzata una console con messaggi che indicano una connessione riuscita. Verrà visualizzato anche un prompt dei comandi in cui è possibile digitare un'SQL comando. La schermata seguente mostra una query di esempio e i risultati:

   ![Output delle query di esempio ODBC](../data-tools/media/raddata-odbc-sample-query-output.png)

## <a name="see-also"></a>Vedi anche

- [Accesso ai dati in Visual Studio](../data-tools/accessing-data-in-visual-studio.md)
