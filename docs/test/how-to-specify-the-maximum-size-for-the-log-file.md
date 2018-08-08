---
title: Dimensione del file di log per i test di carico in Visual Studio
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, logging
ms.assetid: 417059bf-37ae-4e7a-b9b0-29bd71f1414f
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: 29329cb1403745b80d68670f5316ce570582d72c
ms.sourcegitcommit: 495bba1d8029646653f99ad20df2f80faad8d58b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/31/2018
ms.locfileid: "39379397"
---
# <a name="how-to-specify-the-maximum-size-for-the-log-file-for-load-tests"></a>Procedura: Specificare la dimensione massima del file di log per i test di carico

Per impostazione predefinita, la dimensione massima del file di log utilizzata per i test di carico è impostata su 20 megabyte. È possibile modificare questo valore modificando il file di configurazione associato al servizio controller.

## <a name="specify-the-maximum-log-file-size-for-load-test"></a>Specificare la dimensione massima del file di log per i test di carico

1.  Aprire il file di configurazione XML *QTCcontroller.exe.config* che si trova nel percorso *%ProgramFiles(x86)%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\QTCcontroller.exe.config*.

2.  Individuare la voce `<add key="LogSizeLimitInMegs" value="20"/>` nel tag `<appSettings>`.

    ```xml
    <appSettings>
        <add key="LogSizeLimitInMegs" value="20"/>
        <add key="AgentConnectionTimeoutInSeconds" value="120"/>
        <add key="AgentSyncTimeoutInSeconds" value="300"/>
        <add key="ControllerServicePort" value="6901"/>
        <add key="ControllerUsersGroup" value="TeamTestControllerUsers"/>
        <add key="ControllerAdminsGroup" value="TeamTestControllerAdmins"/>
        <add key="CreateTraceListener" value="no"/>
      </appSettings>
    ```

3.  Modificare `value ="20"` impostando la dimensione massima consentita che si desidera specificare per il file di log.

    > [!NOTE]
    > L'immissione di un valore "0" indica che le dimensioni del file di log sono limitate solo dallo spazio disponibile su disco.

## <a name="see-also"></a>Vedere anche

- [Modificare le impostazioni di registrazione dei test di carico](../test/modify-load-test-logging-settings.md)
- [Configurare le porte per test controller e agenti di test](../test/configure-ports-for-test-controllers-and-test-agents.md)