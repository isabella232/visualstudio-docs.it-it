---
title: Configurare un agente di test
description: Informazioni su come eseguire test automatizzati che interagiscono con il desktop configurando l'agente per l'esecuzione come processo anziché come servizio.
ms.custom: SEO-VS-2020
ms.date: 09/18/2018
ms.topic: how-to
helpviewer_keywords:
- agents, configuring for interaction with desktop
ms.assetid: 3a94dd07-6d17-402c-ae8f-7947143755c9
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-test
ms.openlocfilehash: 238c266d11c1057ab59fe5296edc514cfdc2d937
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122075840"
---
# <a name="how-to-set-up-your-test-agent-to-run-tests-that-interact-with-the-desktop"></a>Procedura: Configurare l'agente di test per eseguire test che interagiscono con il desktop

::: moniker range="vs-2017"
Se si vuole eseguire test automatizzati che interagiscono con il desktop, è necessario configurare l'agente affinché venga eseguito come processo anziché come servizio. Se ad esempio si desidera eseguire un test codificato dell'interfaccia utente in remoto mediante un controller di test e un agente di test oppure eseguire un test e acquisire una registrazione video, è necessario configurare l'agente affinché venga eseguito come processo. Quando si assegnano agenti ai ruoli nelle impostazioni test tramite Visual Studio oppure si assegnano agenti ai ruoli nell'ambiente in uso mediante Microsoft Test Manager, è necessario modificare la configurazione per tutti gli agenti assegnati a ruoli che devono interagire con il desktop.
::: moniker-end
::: moniker range=">=vs-2019"
Se si vuole eseguire test automatizzati che interagiscono con il desktop, è necessario configurare l'agente affinché venga eseguito come processo anziché come servizio. Se ad esempio si desidera eseguire un test codificato dell'interfaccia utente in remoto mediante un controller di test e un agente di test oppure eseguire un test e acquisire una registrazione video, è necessario configurare l'agente affinché venga eseguito come processo. Quando si assegnano agenti ai ruoli nelle impostazioni di test usando Visual Studio, è necessario modificare la configurazione per tutti gli agenti assegnati ai ruoli che devono interagire con il desktop.
::: moniker-end

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

::: moniker range="vs-2017"
> [!WARNING]
> Se si usa Microsoft Test Manager per configurare un ambiente lab, viene installato l'agente di test. Nella **procedura guidata di creazione dell'ambiente** è possibile specificare che si desidera configurare uno dei ruoli per eseguire test codificati dell'interfaccia utente.
:::moniker-end

> [!IMPORTANT]
> Il computer che esegue l'agente su cui si desidera eseguire test codificati dell'interfaccia utente non può essere bloccato né avere uno screen saver attivo.

Se si eseguono test codificati dell'interfaccia utente che avviano un browser, per tale operazione viene utilizzato l'account del servizio dell'agente di test. L'account del servizio deve corrispondere all'account utente attivo nel computer. In caso contrario, il browser non verrà avviato.

> [!IMPORTANT]
> Se si esegue un test codificato dell'interfaccia utente che avvia un browser nell'ambito di una definizione di compilazione, per eseguire l'operazione verrà utilizzato l'account del servizio di compilazione. L'account del servizio deve corrispondere all'account utente attivo nel computer. In caso contrario, il browser non verrà avviato.

Utilizzare la procedura riportata di seguito per configurare qualsiasi agente assegnato a un ruolo che esegue un'attività per la quale è necessaria l'interazione con il desktop.

## <a name="to-set-up-an-agent-to-run-as-a-process"></a>Per configurare un agente affinché venga eseguito come processo

1. Per configurare l'agente di test installato per l'esecuzione come processo, passare a **Avvia strumento di** configurazione  >  **dell'agente di test**.

   Viene visualizzata la finestra di dialogo **Configura agente di test**.

   ![Configurare l'agente di test per Visual Studio](media/configure-test-agent.png)

2. Selezionare **Processo interattivo**. L'agente di test verrà avviato come processo anziché come servizio. Scegliere **Avanti**.

3. Immettere il nome utente e la password per l'utente che eseguirà il processo dell'agente di test.

   > [!NOTE]
   > - L'utente che si aggiunge per l'avvio del processo deve essere inoltre aggiunto come membro del gruppo TeamTestAgentService nel computer del controller di test associato all'agente. Se tale utente corrisponde all'utente corrente, quando lo si aggiunge al computer del test controller è necessario disconnettersi o riavviare il sistema.
   > - Le password Null non sono supportate per gli account utente.
   > - Per usare IntelliTrace o l'adattatore dati di emulazione di rete e diagnostico, l'account utente deve essere membro del gruppo Administrators. Se nel computer che esegue l'agente di test viene usato un sistema operativo che dispone di un account utente con privilegi minimi, sarà necessario eseguire l'agente di test anche come amministratore (con privilegi elevati). Se il nome utente dell'agente non è presente nel servizio agente, verrà effettuato il tentativo di aggiungerlo. Questa operazione richiede autorizzazioni sul controller di test.
   > - È necessario che l'utente che sta tentando di usare il test controller sia incluso nell'account utente di tale test controller. In caso contrario non sarà in grado di eseguire i test.

4. Per assicurarsi che un computer con un agente di test sia in grado di eseguire i test dopo il riavvio, è possibile configurarlo per l'accesso automatico come utente dell'agente di test. Selezionare **Accesso automatico**. In questo modo il nome utente e la password verranno archiviati in formato crittografato nel Registro di sistema.

   > [!NOTE]
   > Quando si è connessi all'ambiente lab usando un desktop remoto o una connessione basata su guest, si potrebbero verificare disconnessioni frequenti e impreviste. La connessione potrebbe interrompersi in quanto il computer potrebbe essere configurato per l'accesso automatico alla rete.

5. Per assicurarsi che lo screen saver sia disabilitato in quanto potrebbe interferire con i test automatizzati che devono interagire con il desktop, selezionare **Verifica che lo screen saver sia disabilitato**.

   > [!WARNING]
   > L'accesso automatico e la disabilitazione dello screen saver implicano rischi per la sicurezza. Se si abilita l'accesso automatico si consente ad altri utenti di avviare il computer e di usare l'account in grado di accedere automaticamente. Se si disabilita lo screen saver, è possibile che non venga richiesto di immettere le credenziali di un utente per accedere e sbloccare il computer. In questo modo chiunque possa raggiungere il computer fisico può accedere al sistema. Se si abilitano queste funzionalità in un computer, è consigliabile accertarsi che esso sia fisicamente protetto. Ad esempio, i computer potrebbero essere collocati in un laboratorio sicuro. Se si deseleziona **Assicurarsi che screen saver sia disabilitato,** non viene abilitato l'screen saver.

   Per modificare l'agente riconfigurandolo per l'esecuzione come servizio, è possibile utilizzare questo strumento e selezionare **Servizio**.

6. Per applicare le modifiche apportate, scegliere **Applica impostazioni**.

   Viene visualizzata la finestra di dialogo **Riepilogo configurazione** indicante lo stato di ognuno dei passaggi necessari per configurare l'agente di test.

7. Per chiudere la finestra di dialogo **Riepilogo configurazione**, fare clic su **Chiudi**. Quindi scegliere ancora **Chiudi** per chiudere **Test Agent Configuration Tool**.

   > [!NOTE]
   > Per gli agenti di test eseguiti come processo, nel computer è disponibile un'icona dell'area di notifica. Tale icona indica lo stato dell'agente di test. Se l'agente è in esecuzione come processo, con questo strumento è possibile avviarlo, arrestarlo o riavviarlo. Per avviare l'agente di test come processo se non è in esecuzione, scegliere Avvia Visual Studio  >    >  **Microsoft Visual Studio test agent**.

   ::: moniker range="vs-2017"
   Se il controller di test per questo agente di test è registrato con Team Foundation Server, lo stato dell'agente di test in esecuzione come processo interattivo viene riprodotto nella visualizzazione **Controller** in **Centro lab** per Microsoft Test Manager. Viene elencato con un simbolo di asterisco anteposto al nome per indicare che viene eseguito come un processo interattivo. Per riavviare questo agente di test, è necessario usare lo strumento eseguito nel computer per l'agente di test e non per la **visualizzazione Controller.**
   ::: moniker-end

## <a name="see-also"></a>Vedi anche

- [Installare e configurare agenti di test](../test/lab-management/install-configure-test-agents.md)
