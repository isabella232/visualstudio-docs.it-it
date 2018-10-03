---
title: Distribuisci con distribuzione Web
description: Distribuire un'app tramite distribuzione Web in Visual Studio
services: ''
author: mikejo5000
ms.service: ''
ms.topic: include
ms.date: 05/23/2018
ms.author: mikejo
ms.custom: include file
ms.openlocfilehash: 4ef232e64f308699c73c60cbe5b155f1d4ebb725
ms.sourcegitcommit: 1c675dae7c348defb32d9f7ccf7079a1062a1c4b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/03/2018
ms.locfileid: "48244112"
---
Se è stato installato utilizzando l'installazione guidata piattaforma Web di distribuzione Web, è possibile distribuire l'app direttamente da Visual Studio.

1. Avviare Visual Studio con privilegi di amministratore e riaprire il progetto.

    Per distribuire l'app con distribuzione Web sono necessari privilegi di amministratore.

1. In **Esplora soluzioni**fare clic con il pulsante destro del mouse sul nodo del progetto e scegliere **Pubblica**.

    Se sono stati configurati tutti i profili di pubblicazione, il **pubblica** viene visualizzato il riquadro. Fare clic su **nuovo profilo**.

1. Per la **selezionare una destinazione di pubblicazione**, selezionare **IIS, FTP, e così via** e fare clic su **Publish**.

    ![RemoteDBG_Publish_IISl](../../debugger/media/remotedbg_iis_profile.png "RemoteDBG_Publish_IIS")

1. Immettere i parametri di configurazione di correzione per l'installazione di IIS.

    ![RemoteDBG_Publish_WebDeployl](../../debugger/media/remotedbg_iis_webdeploy_config.png "RemoteDBG_Publish_WebDeploy")

    Se un nome host non viene risolto quando si prova a convalidare i passaggi successivi il **Server** testo casella, provare l'indirizzo IP. Includere `http://` come prefisso sotto la **Server** campo.  Assicurarsi di usare la porta 80 nel **Server** testo casella e assicurarsi che porte 80 e 8172 siano aperte nel firewall.

1. Scegli **convalidare**. Se viene convalidata la configurazione della connessione, è possibile provare a pubblicare.

1. Fare clic su **pubblica** per pubblicare l'app.

    Nella scheda Output Mostra se la pubblicazione ha esito positivo e il browser apre quindi l'app.

    Se si verifica un errore che cita distribuzione Web, controlla di nuovo la procedura di installazione Web Deploy e assicurarsi che le porte appropriate siano aperte (distribuzione Web richiede anche la porta 8172 siano aperte nel server).

    Se l'app distribuisce correttamente ma non viene eseguita correttamente, potrebbe esserci un problema con la configurazione di IIS, l'installazione di ASP.NET o la configurazione del sito Web. Nel Server di Windows, aprire il sito Web da IIS per i messaggi di errore più specifici e quindi controlla di nuovo i passaggi precedenti.
