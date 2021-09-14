---
title: Configurare le porte per test controller e agenti di test
description: Informazioni su come modificare le porte in ingresso predefinite usate dal test controller, dall'agente di test e dal client per evitare conflitti con altri software.
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- firewalls, configuring for test agents
- firewalls, configuring for test controllers
- test agents, firewalls
- test controllers, firewalls
- agents, firewalls
- controllers, firewalls
ms.assetid: 211edbd7-9fe4-4251-ba85-8bec4363261b
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-test
ms.openlocfilehash: c12affe5d2979aefbc8776264fade321e4950818
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126710124"
---
# <a name="configure-ports-for-test-controllers-and-test-agents"></a>Configurare le porte per test controller e agenti di test

È possibile modificare le porte in ingresso predefinite utilizzate dal controller di test, dall'agente di test e dal client. Questa operazione potrebbe essere necessaria se si tenta di utilizzare insieme il controller di test, l'agente di test o il client con altro software che crea conflitti con le impostazioni della porta. Un altro motivo per il quale è necessaria la modifica delle porte è legato alla restrizione del firewall tra il controller di test e il client. In questo caso è possibile configurare manualmente la porta per abilitarla per un firewall in modo che sia possibile inviare i risultati al client tramite il controller di test.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Nella figura seguente sono mostrati i punti di connessione tra il controller di test, l'agente di test e il client. Sono inoltre illustrate le porte che vengono usate per le connessioni in ingresso e in uscita e le restrizioni di sicurezza applicate a tali porte.

![Porte e sicurezza del controller e dell'agente di test](../test/media/test-controller-agent-firewall.png)

## <a name="incoming-connections"></a>Connessioni in ingresso

La porta predefinita usata dal test controller è 6901 e la porta predefinita dell'agente di test è 6910. Per la ricezione dei risultati del test dal controller di test viene utilizzata una porta casuale per impostazione predefinita da parte del client. Per tutte le connessioni in ingresso, tramite il controller di test viene autenticata la parte chiamante e viene verificata l'appartenenza di quest'ultima al gruppo di sicurezza specifico.

- **Test controller** Le connessioni in ingresso sono sulla porta TCP 6901. Se necessario, è possibile configurare la porta in ingresso. Per altre informazioni, vedere [Configurare le porte in ingresso](#configure-the-incoming-ports).

    Il controller di test deve essere in grado di eseguire connessioni in uscita agli agenti di test e al client.

    > [!NOTE]
    > Per il test controller è necessaria la connessione in ingresso **Condivisione di file e stampanti** aperta.

- **Agente di test** Le connessioni in ingresso sono sulla porta TCP 6910. Se necessario, è possibile configurare la porta in ingresso. Per altre informazioni, vedere [Configurare le porte in ingresso](#configure-the-incoming-ports).

   L'agente di test deve essere in grado di eseguire connessioni in uscita al controller di test.

- **Client** Per impostazione predefinita, per le connessioni in ingresso viene usata una porta TCP casuale. Se necessario, è possibile configurare la porta in ingresso. Per altre informazioni, vedere [Configurare le porte in ingresso](#configure-the-incoming-ports).

   Si potrebbero ottenere notifiche del firewall se tramite il controller di test viene tentata la connessione al client la prima volta.

   In Windows Server 2008 le notifiche del firewall sono disabilitate per impostazione predefinita ed è necessario aggiungere manualmente eccezioni firewall per i programmi Client (*devenv.exe*, *mstest.exe*, *mlm.exe*) in modo che sia possibile accettare connessioni in ingresso.

## <a name="outgoing-connections"></a>Connessioni in uscita

Le porte TCP casuali vengono usate per tutte le connessioni in uscita.

- **Test controller** Il test controller deve essere in grado di eseguire una connessione in uscita agli agenti e al client.

- **Agente di test** L'agente di test deve essere in grado di eseguire una connessione in uscita al controller.

- **Client** Il client deve essere in grado di eseguire una connessione in uscita al controller.

## <a name="configure-the-incoming-ports"></a>Configurare le porte in ingresso

Seguire le istruzioni per configurare le porte per un test controller e gli agenti di test.

- **Servizio controller** Modificare il valore della porta modificando il file *%ProgramFiles(x86)%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\QTCcontroller.exe.config*:

    ```xml
    <appSettings>
      <add key="ControllerServicePort" value="6901"/>
    </appSettings>
    ```

- **Servizio agente** Modificare la porta modificando il file *%ProgramFiles(x86)%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\QTAgentService.exe.config*:

    ```xml
    <appSettings>
      <add key="AgentServicePort" value="6910"/>
    </appSettings>
    ```

- **Client** Usare l'editor del Registro di sistema per aggiungere i valori (**DWORD**) del Registro di sistema riportati di seguito. Per il client verrà utilizzata una delle porte dall'intervallo specificato per ricevere dati dal controller di test:

     **HKEY_LOCAL_MACHINE\SOFTWARE\MICROSOFT\VisualStudio\12.0\EnterpriseTools\QualityTools\ListenPortRange\PortRangeStart**

     **HKEY_LOCAL_MACHINE\SOFTWARE\MICROSOFT\VisualStudio\12.0\EnterpriseTools\QualityTools\ListenPortRange\PortRangeEnd**

## <a name="see-also"></a>Vedi anche

- [Installare e configurare agenti di test](../test/lab-management/install-configure-test-agents.md)
