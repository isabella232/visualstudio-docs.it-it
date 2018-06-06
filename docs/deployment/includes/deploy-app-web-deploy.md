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
ms.openlocfilehash: 4ef232e64f308699c73c60cbe5b155f1d4ebb725
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/05/2018
ms.locfileid: "34794198"
---
Se è stato installato utilizzando l'installazione guidata piattaforma Web di distribuzione Web, è possibile distribuire l'app direttamente da Visual Studio.

1. Avviare Visual Studio con privilegi di amministratore e riaprire il progetto.

    Per distribuire l'app tramite distribuzione Web sono necessari i privilegi di amministratore.

1. In **Esplora soluzioni**fare clic con il pulsante destro del mouse sul nodo del progetto e scegliere **Pubblica**.

    Se in precedenza è stato configurato alcun profilo di pubblicazione, il **pubblica** viene visualizzato il riquadro. Fare clic su **nuovo profilo**.

1. Per **selezionare una destinazione di pubblicazione**selezionare **IIS, FTP, e così via** e fare clic su **pubblica**.

    ![RemoteDBG_Publish_IISl](../../debugger/media/remotedbg_iis_profile.png "RemoteDBG_Publish_IIS")

1. Immettere i parametri di configurazione della correzione per l'installazione IIS.

    ![RemoteDBG_Publish_WebDeployl](../../debugger/media/remotedbg_iis_webdeploy_config.png "RemoteDBG_Publish_WebDeploy")

    Se non si risolve un nome host quando si tenta di convalidare nei passaggi successivi il **Server** testo casella, provare l'indirizzo IP. Includere `http://` come un prefisso nel **Server** campo.  Assicurarsi di utilizzare la porta 80 nel **Server** testo finestra e assicurarsi che la porta 80 e la porta 8172 siano aperte nel firewall.

1. Scegliere **convalidare**. Se la configurazione della connessione di convalida, è possibile provare a pubblicare.

1. Fare clic su **pubblica** per pubblicare l'app.

    Nella scheda Output Mostra se la pubblicazione ha esito positivo e il browser apre quindi l'app.

    Se si verifica un errore citare distribuzione Web, eseguire nuovamente la procedura di installazione Web Deploy e assicurarsi che siano aperte le porte corrette (distribuzione Web è necessario porta 8172 sia aperta sul server).

    Se l'app viene distribuito correttamente, ma non viene eseguito correttamente, potrebbe esserci un problema con la configurazione di IIS, l'installazione di ASP.NET o la configurazione del sito Web. In Windows Server, aprire il sito Web da IIS per i messaggi di errore più specifici e quindi eseguire nuovamente i passaggi precedenti.
