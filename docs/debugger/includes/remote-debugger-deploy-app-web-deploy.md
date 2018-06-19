---
title: Distribuisci tramite distribuzione Web
description: Distribuire un'app usando distribuzione Web in Visual Studio
services: ''
author: mikejo5000
ms.service: ''
ms.topic: include
ms.date: 05/23/2018
ms.author: mikejo
ms.custom: include file
ms.openlocfilehash: 8c843ffa6abcb7517ebfe7cdfb0e742a5f244e07
ms.sourcegitcommit: d1824ab926ebbc4a8057163e0edeaf35cec57433
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/24/2018
ms.locfileid: "34478313"
---
Se è stato installato utilizzando l'installazione guidata piattaforma Web di distribuzione Web, è possibile distribuire l'app direttamente da Visual Studio.

1. Avviare Visual Studio con privilegi di amministratore e riaprire il progetto.

    Per distribuire l'app tramite distribuzione Web sono necessari i privilegi di amministratore.

1. In **Esplora soluzioni**fare clic con il pulsante destro del mouse sul nodo del progetto e scegliere **Pubblica**.

    Se in precedenza è stato configurato alcun profilo di pubblicazione, il **pubblica** viene visualizzato il riquadro. Fare clic su **nuovo profilo**.

1. Per **selezionare una destinazione di pubblicazione**selezionare **IIS, FTP, e così via** e fare clic su **pubblica**.

    ![RemoteDBG_Publish_IISl](../media/remotedbg_iis_profile.png "RemoteDBG_Publish_IIS")

1. Immettere i parametri di configurazione della correzione per l'installazione IIS.

    ![RemoteDBG_Publish_WebDeployl](../media/remotedbg_iis_webdeploy_config.png "RemoteDBG_Publish_WebDeploy")

    Se non si risolve un nome host quando si tenta di convalidare nei passaggi successivi il **Server** testo casella, provare l'indirizzo IP. Includere `http://` come un prefisso nel **Server** campo.  Assicurarsi di utilizzare la porta 80 nel **Server** testo e assicurarsi che la porta 80 sia aperta nel firewall.

1. Fare clic su **Avanti**, scegliere un **Debug** configurazione, scegliere **Rimuovi file aggiuntivi nella destinazione** sotto il **pubblicare File** Opzioni.

    > [!NOTE]
    > Se si sceglie una configurazione di rilascio, disabilitare il debug nel file Web. config quando esegue la pubblicazione.

1. Fare clic su **Prev**, quindi scegliere **convalida**. Se la configurazione della connessione di convalida, è possibile provare a pubblicare.

1. Fare clic su **pubblica** per pubblicare l'app.

    Nella scheda Output Mostra se la pubblicazione ha esito positivo e il browser apre quindi l'app.

    Se si verifica un errore citare distribuzione Web, eseguire nuovamente la procedura di installazione Web Deploy e assicurarsi che siano aperte le porte corrette (distribuzione Web è necessario porta 8172 sia aperta sul server).

    Se l'app viene distribuito correttamente, ma non viene eseguito correttamente, potrebbe esserci un problema con la configurazione di IIS, l'installazione di ASP.NET o la configurazione del sito Web. In Windows Server, aprire il sito Web da IIS per i messaggi di errore più specifici e quindi eseguire nuovamente i passaggi precedenti.
