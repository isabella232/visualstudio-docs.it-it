---
title: Associare test controller/test agent a una scheda di rete
description: Informazioni su come associare un test controller o un agente di test a una scheda di rete usando un indirizzo IP, nel caso in cui sia installato per più schede di rete.
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- controllers, netwrok adapter
- agents, configuring
- agents, network adapter
- controllers, configuring
ms.assetid: 7eb9290a-f9f6-4e41-9caa-796fcfaf0610
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-test
ms.openlocfilehash: a1ea5e3729eaa9b52d825540fe392b61519a5f60
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122123021"
---
# <a name="how-to-bind-a-test-controller-or-test-agent-to-a-network-adapter"></a>Procedura: Associare un test controller o un agente di test a una scheda di rete

Se un computer con installato il software del test controller o dell'agente di test dispone di più schede di rete, è necessario specificare l'indirizzo IP anziché il nome del computer per identificare il test controller o l'agente di test.

> [!WARNING]
> Quando si tenta di configurare un agente di test, potrebbe verificarsi l'errore seguente:
>
> **Errore 8110. Non è possibile connettersi al computer controller specificato o accedere all'oggetto controller**
>
> Questo errore può essere causato dall'installazione del controller di test in un computer con più di una scheda di rete. È anche possibile installare correttamente gli agenti e non riscontrare il problema finché non si tenta di eseguire un test.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="bind-a-test-controller-to-a-specific-network-adapter"></a>Associare un controller di test a una scheda di rete specifica

### <a name="to-obtain-the-ip-addresses-of-the-network-adapters"></a>Per ottenere gli indirizzi IP delle schede di rete

1. In Microsoft Windows scegliere **Start**, **Inizia ricerca**, digitare **cmd** e quindi scegliere **INVIO**.

2. Digitare **ipconfig /all**.

     Verranno visualizzati gli indirizzi IP delle schede di rete. Registrare l'indirizzo IP della scheda di rete da associare al controller.

### <a name="to-bind-a-network-adapter-to-a-test-controller"></a>Per associare un adattatore di rete a un controller di test

1. In Microsoft Windows scegliere **Start**, **Inizia ricerca**, digitare **services.msc** e quindi scegliere **INVIO**.

     Viene visualizzata la finestra di dialogo **Servizi**.

2. Nel riquadro dei risultati, nella colonna **Nome** fare clic con il pulsante destro del mouse sul servizio **Visual Studio Test Controller** e quindi scegliere **Arresta**.

     -oppure-

     Aprire un prompt dei comandi con privilegi elevati ed eseguire il comando seguente nella riga di comando:

     `net stop vsttcontroller`

3. Aprire il file di configurazione XML *QTCcontroller.exe.config* che si trova in *%ProgramFiles(x86)%\Microsoft Visual Studio\2017\\\<edition>\Common7\IDE*.

4. Individuare il tag `<appSettings>`.

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

5. Aggiungere la chiave `BindTo` per specificare gli adattatori di rete da utilizzare nella sezione `<appSettings>`.

    ```xml
            <add key="BindTo" value="<YOUR IP ADDRESS>"/>
    </appSettings>
    ```

6. Avviare il servizio controller di test. A tale scopo, eseguire il comando seguente dal prompt dei comandi:

    `net start vsttcontroller`

    > [!WARNING]
    > Per connettere l'agente di test al controller è necessario eseguire nuovamente l'installazione dell'agente di test. Questa volta, specificare l'indirizzo IP anziché il nome del controller.

     Questa procedura si applica al controller, al servizio agente e al processo agente. La proprietà `BindTo` deve essere impostata per ogni processo in esecuzione in un computer che dispone di più schede di rete. La procedura per impostare la proprietà `BindTo` è identica per i tre processi, come specificato più indietro in questo argomento per il controller di test.

### <a name="to-bind-a-network-interface-card-to-a-test-agent"></a>Per associare una scheda di rete a un agente di test

1. In Microsoft Windows scegliere **Start**, **Inizia ricerca**, digitare **services.msc** e quindi scegliere **INVIO**.

    Viene visualizzata la finestra di dialogo **Servizi**.

2. Nel riquadro dei risultati, nella colonna **Nome** fare clic con il pulsante destro del mouse sul servizio **Agente di test di Visual Studio** e quindi scegliere **Arresta**.

     -oppure-

     Aprire un prompt dei comandi con privilegi elevati ed eseguire il comando seguente nella riga di comando:

     **net stop vsttagent**

3. Aprire il file di configurazione XML *QTAgentService.exe.config* che si trova in *%ProgramFiles(x86)%\Microsoft Visual Studio\2017\\\<edition>\Common7\IDE*.

4. Individuare il tag `<appSettings>`.

    ```xml
    <appSettings>
      <appSettings>
      <add key="LogSizeLimitInMegs" value="20"/>
      <add key="AgentServicePort" value="6910"/>
      <add key="ControllerConnectionPeriodInSeconds" value="30"/>
      <add key="StopTestRunCallTimeoutInSeconds" value="120"/>
      <add key="CreateTraceListener" value="no"/>
      <add key="GetCollectorDataTimeout" value="300"/>
    </appSettings>  </appSettings>
    ```

5. Aggiungere la chiave `BindTo` per specificare gli adattatori di rete da utilizzare nella sezione `<appSettings>`.

    ```xml
            <add key="BindTo" value="<YOUR IP ADDRESS>"/>
    </appSettings>
    ```

6. Avviare il servizio agente di test. A tale scopo, eseguire il comando seguente dal prompt dei comandi:

    `net start vsttagent`

## <a name="see-also"></a>Vedi anche

- [Installare e configurare agenti di test](../test/lab-management/install-configure-test-agents.md)
- [Modificare le impostazioni di registrazione dei test di carico](../test/modify-load-test-logging-settings.md)
- [Configurare le porte per test controller e agenti di test](../test/configure-ports-for-test-controllers-and-test-agents.md)
- [Procedura: Specificare i periodi di timeout per controller e agenti di test](../test/how-to-specify-timeout-periods-for-test-controllers-and-test-agents.md)
