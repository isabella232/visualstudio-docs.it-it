---
title: Aggiungere nuove connessioni
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.workload:
- data-storage
ms.openlocfilehash: 73b09384bd57fd4ea0890d107ce641e4b615559f
ms.sourcegitcommit: 73861cd0ea92e50a3be1ad2a0ff0a7b07b057a1c
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 01/09/2019
ms.locfileid: "54154218"
---
# <a name="add-new-connections"></a>Aggiungere nuove connessioni

È possibile testare la connessione a un database o un servizio ed esplorare i contenuti del database e schemi, utilizzando **Esplora Server**, **Cloud Explorer**, o **Esplora oggetti di SQL Server**. La funzionalità di queste finestre si sovrappone a una certa misura. Le differenze di base sono:

- Esplora server

   Installato per impostazione predefinita in Visual Studio. Utilizzabile per testare le connessioni e visualizzare i database di SQL Server, ad altri database che hanno installato un provider ADO.NET e alcuni servizi di Azure. Mostra anche gli oggetti di basso livello, ad esempio i contatori delle prestazioni di sistema, registri eventi e le code di messaggi. Se un'origine dati non dispone di alcun provider ADO.NET, non verranno visualizzati qui, ma è comunque possibile usarlo da Visual Studio tramite la connessione a livello di codice.

- Cloud Explorer

   Installare manualmente questa finestra come un'estensione di Visual Studio selezionando **degli strumenti** > **estensioni e aggiornamenti** > **Online**  >  **Visual Studio Marketplace**. Fornisce funzionalità specializzate per l'esplorazione e la connessione a servizi di Azure.

- Esplora oggetti di SQL Server

   Installato con SQL Server Data Tools e visibile sotto il **vista** menu. Se non viene visualizzato non esiste, andare al **programmi e funzionalità** nel Pannello di controllo Cerca Visual Studio e quindi selezionare **modifica** per eseguire nuovamente il programma di installazione dopo aver selezionato la casella di controllo per SQL Server Data Tools. Uso **Esplora oggetti di SQL Server** ai database SQL di visualizzazione (se dispongono di un provider ADO.NET), creare nuovi database, modificare gli schemi, creare stored procedure, recuperare le stringhe di connessione, visualizzare i dati e altro ancora. Database SQL di cui non sono installato alcun provider ADO.NET non verranno visualizzate qui, ma può comunque connettersi a essi a livello di codice.

## <a name="add-a-connection-in-server-explorer"></a>Aggiungere una connessione in Esplora Server

Per creare una connessione al database, fare clic sui **Aggiungi connessione** icona nella **Esplora Server**, o fare doppio clic nella **Esplora Server** nel **dati Le connessioni** nodo e selezionare **Aggiungi connessione**. A questo punto, è anche possibile connettersi a un database in un altro server, un servizio di SharePoint o un servizio di Azure.

![Icona nuova connessione di Esplora server](../data-tools/media/raddata-server-explorer-new-connection-icon.png)

Verrà visualizzata la **Aggiungi connessione** nella finestra di dialogo. In questo caso, è stato immesso il nome dell'istanza di LocalDB di SQL Server.

![Aggiungere una nuova connessione](../data-tools/media/raddata-add-new-connection-dialog.png)

## <a name="change-the-provider"></a>Modificare il provider

Se l'origine dati non si desidera, fare clic il **modifica** pulsante per selezionare una nuova origine dati e/o un nuovo provider di dati ADO.NET. Il nuovo provider potrebbe chiedere le credenziali, a seconda di come è stato configurato.

![Provider di dati di modifica AD0.NET](../data-tools/media/raddata-change-ad0.net-data-provider.png)

## <a name="test-the-connection"></a>Testare la connessione

Dopo aver scelto l'origine dati, fare clic su **Test connessione**. Se non viene completato, è necessario risolvere i problemi di base la documentazione del fornitore.

![Test connessione](../data-tools/media/raddata-test-connection.png)

Se il test ha esito positivo, si è pronti per creare un *zdroj dat*, che è un termine di Visual Studio che in realtà indica una *modello di dati* basato sul database o del servizio sottostante.

## <a name="see-also"></a>Vedere anche

- [Visual Studio Data Tools per .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)
