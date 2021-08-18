---
title: Aggiungere nuove connessioni
description: Aggiungere una connessione in Visual Studio a un database o a un servizio ed esplorare il contenuto e gli schemi del database usando Esplora server, Cloud Explorer o SQL Server Esplora oggetti.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 0348a3ba4db339e7472fc3ff72b09fe8cc23135e
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122067247"
---
# <a name="add-new-connections"></a>Aggiungere nuove connessioni

È possibile testare la connessione a un database o a un servizio ed esplorare il contenuto e gli schemi del database usando Esplora server **,** **Cloud Explorer** o **SQL Server Esplora oggetti**. La funzionalità di queste finestre si sovrappone in qualche modo. Le differenze di base sono:

- Esplora server

   Installato per impostazione predefinita in Visual Studio. Può essere usato per testare le connessioni e visualizzare SQL Server database, tutti gli altri database in cui è installato un provider ADO.NET e alcuni servizi di Azure. Mostra anche oggetti di basso livello, ad esempio contatori delle prestazioni di sistema, log eventi e code di messaggi. Se un'origine dati non ADO.NET un provider di dati, non verrà visualizzato qui, ma sarà comunque possibile usarlo dal Visual Studio connettendosi a livello di codice.

- Cloud Explorer

   Installare questa finestra manualmente come estensione Visual Studio da [Visual Studio Marketplace.](https://marketplace.visualstudio.com/items?itemName=ms-azuretools.CloudExplorerForVS) Fornisce funzionalità specializzate per l'esplorazione e la connessione ai servizi di Azure.

- Esplora oggetti di SQL Server

   Installato con SQL Server Data Tools e visibile **nel** menu Visualizza. Se non viene visualizzato, passare a Programmi e funzionalità **in** Pannello di controllo, trovare Visual Studio e  quindi selezionare Cambia per eseguire nuovamente il programma di installazione dopo aver selezionato la casella di controllo per SQL Server Data Tools. Usare **SQL Server Esplora oggetti** per visualizzare i database SQL (se dispongono di un provider ADO.NET), creare nuovi database, modificare schemi, creare stored procedure, recuperare stringhe di connessione, visualizzare i dati e altro ancora. SQL i database in cui non ADO.NET installato un provider di servizi non vengono visualizzati qui, ma è comunque possibile connettersi a essi a livello di codice.

## <a name="add-a-connection-in-server-explorer"></a>Aggiungere una connessione in Esplora server

Per creare una connessione al  database, fare clic sull'icona Aggiungi connessione in **Esplora server**  oppure fare clic con il pulsante destro del mouse su **Esplora server** nel nodo Connessioni dati e scegliere **Aggiungi connessione**. Da qui è anche possibile connettersi a un database in un altro server, un SharePoint o un servizio di Azure.

![Esplora server icona Nuova connessione](../data-tools/media/raddata-server-explorer-new-connection-icon.png)

Verrà visualizzata la **finestra di dialogo Aggiungi** connessione . In questo caso è stato immesso il nome dell'SQL Server Local DB locale.

![Aggiungere una nuova connessione](../data-tools/media/raddata-add-new-connection-dialog.png)

## <a name="change-the-provider"></a>Modificare il provider

Se l'origine dati non è  quella desiderata, fare clic sul pulsante Cambia per scegliere una nuova origine dati e/o un nuovo provider ADO.NET dati. Il nuovo provider potrebbe richiedere le credenziali, a seconda di come è stato configurato.

![Modificare AD0.NET provider di dati](../data-tools/media/raddata-change-ad0.net-data-provider.png)

## <a name="test-the-connection"></a>Testare la connessione

Dopo aver scelto l'origine dati, fare clic su **Test connessione**. Se l'operazione non riesce, è necessario risolvere i problemi in base alla documentazione del fornitore.

![Test della connessione](../data-tools/media/raddata-test-connection.png)

Se il test ha esito positivo, è possibile creare un'origine dati ,  ovvero un termine Visual Studio che in realtà significa un modello di dati basato sul database o sul servizio sottostante.

## <a name="see-also"></a>Vedi anche

- [Visual Studio data tools per .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)
