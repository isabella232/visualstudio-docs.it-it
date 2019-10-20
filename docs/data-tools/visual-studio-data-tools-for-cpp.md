---
title: Data Tools perC++
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CPP
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- data-storage
- cplusplus
ms.openlocfilehash: 33c91a7c21a04624d71692d12b7a7f15a16e1d67
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72639509"
---
# <a name="visual-studio-data-tools-for-c"></a>Visual Studio Data Tools per C++

I C++ nativi possono spesso fornire le prestazioni più veloci quando si accede alle origini dati. Tuttavia, gli strumenti per i C++ dati per le applicazioni in Visual Studio non sono così ricchi come per le applicazioni .NET. La finestra **origini dati** , ad esempio, non può essere utilizzata per trascinare le origini dati su C++ un'area di progettazione. Se è necessario un livello relazionale a oggetti, sarà necessario scrivere un prodotto personalizzato oppure utilizzare un prodotto di terze parti. Lo stesso vale per le funzionalità di data binding, sebbene le applicazioni che utilizzano la libreria Microsoft Foundation Class possano utilizzare alcune classi di database, insieme a documenti e visualizzazioni, per archiviare i dati in memoria e visualizzarli all'utente. Per altre informazioni, vedere [accesso ai dati in C++Visual ](/cpp/data/data-access-in-cpp).

Per connettersi ai database SQL, le C++ applicazioni native possono utilizzare i driver ODBC e OLE DB e il provider ADO inclusi in Windows. Questi possono connettersi a qualsiasi database che supporti tali interfacce. Il driver ODBC è lo standard. OLE DB viene fornito per compatibilità con le versioni precedenti. Per ulteriori informazioni su queste tecnologie dati, vedere [Windows Data Access Components](/previous-versions/windows/desktop/ms692897(v=vs.85)).

Per sfruttare i vantaggi della funzionalità personalizzata in SQL Server 2005 e versioni successive, utilizzare [SQL Server Native Client](/sql/relational-databases/native-client/sql-server-native-client). Native Client contiene anche il driver ODBC SQL Server e il provider di OLE DB SQL Server in una libreria a collegamento dinamico (DLL) nativa. Supportano le applicazioni che utilizzano API in codice nativo (ODBC, OLE DB e ADO) per Microsoft SQL Server. SQL Server Native Client viene installato con SQL Server Data Tools. La guida alla programmazione è la seguente: [SQL Server Native Client Programming](/sql/relational-databases/native-client/sql-server-native-client-programming).

## <a name="to-connect-to-localdb-through-odbc-and-sql-native-client-from-a-c-application"></a>Per connettersi al database locale tramite ODBC e SQL Native Client da C++ un'applicazione

1. Installare SQL Server Data Tools.

2. Se è necessario un database SQL di esempio a cui connettersi, scaricare il database Northwind e decomprimerlo in una nuova posizione.

3. Utilizzare SQL Server Management Studio per alleghi il file *Northwind. MDF* decompresso al database locale. Quando SQL Server Management Studio viene avviato, connettersi a (local DB) \MSSQLLocalDB.

   ![Finestra di dialogo connessione di SSMS](../data-tools/media/raddata-ssms-connect-dialog.png)

   Fare quindi clic con il pulsante destro del mouse sul nodo del database locale nel riquadro sinistro e scegliere **Connetti**.

   ![Database di connessione SSMS](../data-tools/media/raddata-ssms-attach-database.png)

4. Scaricare l'esempio ODBC Windows SDK e decomprimerlo in una nuova posizione. In questo esempio vengono illustrati i comandi ODBC di base utilizzati per connettersi a un database ed eseguire query e comandi. Per ulteriori informazioni su tali funzioni, vedere [Microsoft Open Database Connectivity (ODBC)](/sql/odbc/microsoft-open-database-connectivity-odbc). Quando si carica la soluzione per la prima volta (si C++ trova nella cartella), Visual Studio offrirà l'aggiornamento della soluzione alla versione corrente di Visual Studio. Scegliere **Sì**.

5. Per usare native client, sono necessari il file di *intestazione* e il file *lib* . Questi file contengono funzioni e definizioni specifiche per SQL Server, oltre alle funzioni ODBC definite in SQL. h. Nelle**Proprietà** di **Project**  >   > **directory di VC + +** aggiungere la directory di inclusione seguente:

   **%Programmi%\Microsoft SQL Server\110\SDK\Include**

   E questa directory della libreria:

   **%Programmi%\Microsoft SQL Server\110\SDK\Lib**

6. Aggiungere queste righe in *odbcsql. cpp*. Il #define impedisce la compilazione di definizioni OLE DB irrilevanti.

   ```cpp
   #define _SQLNCLI_ODBC_
   #include <sqlncli.h>
   ```

    Si noti che l'esempio non usa effettivamente alcuna funzionalità client nativa, quindi i passaggi precedenti non sono necessari per la compilazione e l'esecuzione. Il progetto è ora configurato per l'uso di questa funzionalità. Per altre informazioni, vedere [Programmazione in SQL Server Native Client](/sql/relational-databases/native-client/sql-server-native-client).

7. Consente di specificare il driver da utilizzare nel sottosistema ODBC. L'esempio passa l'attributo della stringa di connessione del DRIVER in come argomento della riga di comando. In **Project**  > **Properties**  > **debug**aggiungere questo argomento del comando:

   ```cpp
   DRIVER="SQL Server Native Client 11.0"
   ```

8. Premere **F5** per compilare ed eseguire l'applicazione. Verrà visualizzata una finestra di dialogo dal driver che richiede di immettere un database. Immettere `(localdb)\MSSQLLocalDB` e selezionare **Usa connessione trusted**. Fare clic su **OK**. Verrà visualizzata una console con messaggi che indicano una connessione riuscita. Dovrebbe essere visualizzato anche un prompt dei comandi in cui è possibile digitare un'istruzione SQL. La schermata seguente mostra una query di esempio e i risultati:

   ![Output della query di esempio ODBC](../data-tools/media/raddata-odbc-sample-query-output.png)

## <a name="see-also"></a>Vedere anche

- [Accesso ai dati in Visual Studio](../data-tools/accessing-data-in-visual-studio.md)