---
title: Registrare lo schermo e la voce durante i test
description: Informazioni su come configurare l'adattatore dati di diagnostica che registra la schermata e la voce dell'utente che esegue il test in Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 10/03/2016
ms.topic: how-to
helpviewer_keywords:
- test settings, recording desktop video
ms.assetid: 2cefe8c2-430a-4cb4-bbe0-f3edb2e5bc03
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-test
ms.openlocfilehash: 491980165ec7528ed111a3ec99eab79e656ecfda597c79b17dbc37e36d9fa1e7
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121366635"
---
# <a name="how-to-include-recordings-of-the-screen-and-voice-during-tests-using-test-settings"></a>Procedura: Includere le registrazioni dello schermo e della voce durante i test usando le impostazioni test

Dall'editor di configurazione in Visual Studio è possibile configurare l'adattatore dati di diagnostica che registra lo schermo e la voce dell'utente che esegue il test. Con l'adattatore dati di diagnostica è possibile salvare una registrazione dello schermo e della voce della sessione desktop durante il test. La registrazione viene salvata con il risultato del test oppure può essere allegata a un bug. Gli altri membri del team possono utilizzare la registrazione per isolare i difetti dell'applicazione difficili da riprodurre.

> [!WARNING]
> Le registrazioni dello schermo e della voce non supportano configurazioni con più monitor.

La funzionalità di registrazione dello schermo e della voce può essere utilizzata con i test manuali o automatizzati. Ad esempio, se si esegue un test codificato dell'interfaccia utente in modalità remota è necessario registrare il desktop per visualizzare il test nel corso dell'esecuzione. Per altre informazioni su come acquisire una registrazione dello schermo e della voce in modalità remota, vedere [Procedura: Configurare l'agente di test per eseguire test che interagiscono con il desktop](../test/how-to-set-up-your-test-agent-to-run-tests-that-interact-with-the-desktop.md).

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="to-configure-screen-and-voice-recording-for-your-test-settings"></a>Per configurare la registrazione dello schermo e della voce per le impostazioni di test

1. Aprire le impostazioni di test che si desidera configurare per la registrazione dello schermo e della voce. Per altre informazioni, vedere [Raccogliere dati di diagnostica durante i test (Azure Test Plans)](/azure/devops/test/collect-diagnostic-data?view=vsts&preserve-view=true) o [Raccogliere dati di diagnostica usando impostazioni test](../test/collect-diagnostic-information-using-test-settings.md).

2. Nelle impostazioni di test selezionare il **Ruolo** da usare per registrare lo schermo e la voce.

    > [!NOTE]
    > Per i test manuali e automatizzati, si tratta del computer in cui vengono eseguiti i test.

3. Selezionare **Registrazione dello schermo e della voce**, quindi **Configura**.

     Viene visualizzata la finestra di dialogo **Configura adattatore dati di diagnostica - Registrazione dello schermo e della voce**.

     ![Configurazione video](../test/media/testsettingvideoconfiggdr.png)

4. (Facoltativo) Selezionare **Abilita registrazione voce** per acquisire contenuti audio nella registrazione.

5. (Facoltativo) Selezionare la casella di controllo accanto a **Salva registrazione in caso di superamento del test case** per specificare il salvataggio delle registrazioni dello schermo e della voce per i test superati e non superati.

    > [!WARNING]
    > Se si seleziona **Salva registrazione in caso di superamento del test case**, la registrazione viene archiviata con i risultati del test, usando spazio di archiviazione sul server. È possibile usare lo strumento di **pulizia allegati di test** per pulire questi allegati.

6. In **Qualità registrazione dello schermo** configurare le opzioni seguenti:

    1. **Frequenza dei fotogrammi:** specificare il numero di fotogrammi al secondo da usare nella registrazione dello schermo e della voce. Il valore predefinito è 4 fotogrammi al secondo. È possibile specificare valori compresi tra 2 e 20.

    2. **Velocità in bit:** specificare quanti KB al secondo usare nella registrazione dello schermo e della voce. Il valore predefinito è 512. È possibile specificare valori compresi tra 512 e 10.000.

    3. **Qualità (1-100):** è possibile specificare la qualità della registrazione dello schermo e della voce selezionando un intervallo compreso tra 1 e 100. Il valore predefinito è 50 (intermedio).

7. Scegliere **OK**. Le impostazioni dell'agente di raccolta traccia di diagnostica sono ora configurate e salvate per le impostazioni di test.

    ::: moniker range="vs-2017"
    > [!TIP]
    > Per reimpostare la configurazione dell'adattatore dati di diagnostica, scegliere **Reimposta configurazione predefinita** per Visual Studio e **Ripristina predefinito** per Microsoft Test Manager.
    ::: moniker-end
    ::: moniker range=">=vs-2019"
    > [!TIP]
    > Per reimpostare la configurazione per questo adattatore dati di diagnostica, scegliere **Ripristina configurazione predefinita** in Visual Studio.
    ::: moniker-end

## <a name="see-also"></a>Vedi anche

- [Raccogliere dati di diagnostica durante i test (Azure Test Plans)](/azure/devops/test/collect-diagnostic-data?view=vsts&preserve-view=true)
- [Raccogliere dati di diagnostica nei test manuali (Azure Test Plans)](/azure/devops/test/mtm/collect-more-diagnostic-data-in-manual-tests?view=vsts&preserve-view=true)
- [Raccogliere dati di diagnostica usando impostazioni test](../test/collect-diagnostic-information-using-test-settings.md)
- [Eseguire test manuali (Azure Test Plans)](/azure/devops/test/run-manual-tests?view=vsts&preserve-view=true)