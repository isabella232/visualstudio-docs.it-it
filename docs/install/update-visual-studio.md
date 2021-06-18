---
title: Aggiornare Visual Studio
titleSuffix: ''
description: Informazioni dettagliate su come Visual Studio alla versione più recente.
ms.date: 04/06/2021
ms.custom: acquisition
ms.topic: how-to
ms.prod: visual-studio-windows
ms.technology: vs-installation
helpviewer_keywords:
- update [Visual Studio]
- change [Visual Studio]
f1_keywords:
- VS.ToolsOptionsPages.Environment.ProductUpdates
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: b541568da45c9bd8dda7258534193371e7e9f04b
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/17/2021
ms.locfileid: "112306839"
---
# <a name="update-visual-studio-to-the-most-recent-release"></a>Aggiornare Visual Studio alla versione più recente

::: moniker range="vs-2017"

È consigliabile eseguire l'aggiornamento alla [versione più recente](/visualstudio/releasenotes/vs2017-relnotes/) di Visual Studio 2017, in modo da avere sempre a disposizione le funzionalità, le correzioni e i miglioramenti più recenti.

Se invece si vuole provare la versione più recente, è consigliabile scaricare e installare [Visual Studio 2019](https://visualstudio.microsoft.com/downloads).

> [!IMPORTANT]
> Per installare, aggiornare o modificare Visual Studio, è necessario accedere con un account con autorizzazioni amministrative. Per altre informazioni, vedere [Autorizzazioni utente e Visual Studio](../ide/user-permissions-and-visual-studio.md).
>
> [!NOTE]
> Questo argomento si applica a Visual Studio in Windows. Per Visual Studio per Mac, vedere [Aggiornare Visual Studio per Mac](/visualstudio/mac/update).

## <a name="update-visual-studio-2017-version-156-or-later"></a>Eseguire l'aggiornamento a Visual Studio 2017 versione 15.6 o successiva

L'esperienza di installazione e aggiornamento è stata migliorata per semplificarne l'uso direttamente dall'interno dell'IDE. Di seguito viene illustrato come eseguire l'aggiornamento dalla versione 15.6 e versioni successive alle versioni più recenti di Visual Studio.

### <a name="using-the-notifications-hub"></a>Uso dell'hub Notifiche

Quando è disponibile un aggiornamento, in Visual Studio viene visualizzato un flag di notifica corrispondente.

1. Salvare il lavoro.

1. Scegliere il flag di notifica per aprire l'hub **Notifiche** e quindi scegliere l'aggiornamento che si vuole installare.

   ![Aggiornare Visual Studio 2017 usando l'hub di notifica](media/vs-install-notifications-hub-15dot6.png "Hub notifiche in Visual Studio 2017")

      > [!TIP]
      > Un aggiornamento per un'edizione di Visual Studio 2017 è cumulativo, quindi scegliere sempre di installare quello con il numero di versione più recente.

1. Quando viene visualizzata la finestra di dialogo **Aggiorna** scegliere **Aggiorna adesso**.

    ![Aggiornare Visual Studio 2017 usando la finestra di dialogo Aggiorna dell'hub Notifiche](media/vs-update-now-from-notifications-hub.png "Finestra di dialogo Aggiorna dall'hub notifiche in Visual Studio")

     Se si apre una finestra di dialogo di controllo dell'accesso utente, scegliere **Sì**. È possibile che venga visualizzata brevemente una finestra di dialogo "Attendere" e quindi viene aperto il programma di installazione di Visual Studio per avviare l'aggiornamento.

     ![La nuova Programma di installazione di Visual Studio nella versione 15.6](media/visual-studio-15dot6-installer.png "La nuova Programma di installazione di Visual Studio nella versione 15.6")

     L'aggiornamento continua. Al termine, verrà riavviato Visual Studio.

     > [!NOTE]
     > Quando si esegue Visual Studio in modalità amministratore, dopo l'aggiornamento è necessario riavviare manualmente Visual Studio.

### <a name="using-the-ide"></a>Utilizzo di IDE

È possibile verificare la disponibilità di un aggiornamento e quindi installarlo dalla barra dei menu in Visual Studio.

1. Salvare il lavoro.

1. Scegliere **Help** > **Check for Updates (Verifica della disponibilità di aggiornamenti).**

     ![Il nuovo menu ? in Visual Studio versione 15.6](media/vs-help-menu-check-for-updates.png "Il nuovo menu ? in Visual Studio versione 15.6")

1. Quando viene visualizzata la finestra di dialogo **Aggiorna** scegliere **Aggiorna adesso**.

   L'aggiornamento procede come descritto nella sezione precedente e Visual Studio viene riavviato dopo il corretto completamento dell'aggiornamento.

   > [!NOTE]
   > Quando si esegue Visual Studio in modalità amministratore, dopo l'aggiornamento è necessario riavviare manualmente Visual Studio.

### <a name="using-the-visual-studio-installer"></a>Uso del programma di installazione di Visual Studio

Come nelle versioni precedenti di Visual Studio, è possibile usare il programma di installazione di Visual Studio per installare un aggiornamento.

1. Salvare il lavoro.

1. Aprire il programma di installazione. Il programma di installazione di Visual Studio potrebbe richiedere l'aggiornamento prima di continuare.

   > [!NOTE]
   > In un computer che esegue Windows 10, il programma di installazione compare sotto la lettera **P** come **Programma di installazione di Visual Studio** ocome **Programma di installazione di Microsoft Visual Studio**.

1. Nella pagina **Prodotto** del programma di installazione cercare l'edizione di Visual Studio precedentemente installata.

1. Se è disponibile un aggiornamento, viene visualizzato un pulsante **Aggiorna**. La verifica della disponibilità di un aggiornamento potrebbe richiedere alcuni secondi.

   Scegliere il pulsante **Aggiorna** per installare gli aggiornamenti.

     ![Aggiornare Visual Studio 2017 usando il Programma di installazione di Visual Studio](media/update-visual-studio.png "Aggiornare Visual Studio 2017 usando il Programma di installazione di Visual Studio")

## <a name="update-visual-studio-2017-version-155-or-earlier"></a>Aggiornare Visual Studio 2017 versione 15.5 o versioni precedenti

Se si usa una versione precedente, di seguito viene descritto come eseguire l'aggiornamento da Visual Studio 2017 versione 15.0 fino alla versione 15.5.

### <a name="update-by-using-the-notifications-hub"></a>Eseguire gli aggiornamenti tramite l'hub Notifiche

1. Quando sono disponibili aggiornamenti, in Visual Studio viene visualizzato un flag di notifica corrispondente.

   ![Flag di Visual Studio 2017](media/notification-flag.png "Flag di notifica di aggiornamento in Visual Studio")

   Scegliere il flag di notifica per aprire l'hub **di notifica**.

   ![Visual Studio 2017 nell'hub di notifica](media/notifications-hub.png "Visual Studio 2017 nell'hub di notifica")

      > [!TIP]
      > Un aggiornamento per un'edizione di Visual Studio 2017 è cumulativo, quindi scegliere sempre di installare quello con il numero di versione più recente.

1. Scegliere **"Visual Studio Update" è disponibile**. Verrà aperta la finestra di dialogo **Estensioni e aggiornamenti**.

   ![Scegliere Visual Studio aggiorna](media/notifications-hub-select.png "Scegliere Visual Studio aggiornamento")

1. Nella finestra di dialogo **Estensioni e aggiornamenti** scegliere il pulsante **Aggiorna**.

   ![Scegliere Aggiorna nella finestra di dialogo Estensioni e aggiornamenti](media/notifications-extensions-and-updates.png "Finestra di dialogo Estensioni e aggiornamenti in Visual Studio")

#### <a name="more-about-visual-studio-notifications"></a>Altre informazioni sulle notifiche di Visual Studio

Visual Studio invia una notifica all'utente quando è disponibile un aggiornamento di Visual Studio stesso o di uno o più componenti, nonché quando si verificano eventi specifici nell'ambiente di Visual Studio.

* Se il flag di notifica è giallo, un aggiornamento del prodotto Visual Studio è disponibile per l'installazione.
* Se il flag di notifica è rosso, la licenza presenta un problema.
* Se il flag di notifica è nero, sono presenti messaggi informativi o facoltativi.

Scegliere il flag di notifica per aprire l'hub di **notifica** e quindi scegliere le notifiche su cui si vuole agire. In alternativa, è possibile scegliere di ignorare o eliminare una notifica.

 ![Visualizzare un messaggio facoltativo o informativo nell'hub di notifica](media/notification-flag-optional.png "Flag di notifica del messaggio facoltativo o informativo in Visual Studio")

Se si sceglie di ignorare una notifica, questa non viene più visualizzata da Visual Studio. Se si vuole reimpostare l'elenco delle notifiche ignorate, scegliere il pulsante **Impostazioni** nell'hub Notifiche.

   ![Scegliere il pulsante Impostazioni nell'hub Notifiche per visualizzare le opzioni di notifica](media/vs-notifications-hub-settings-button.png "Scegliere il pulsante Impostazioni nell'hub notifiche per visualizzare le opzioni di notifica")

### <a name="update-by-using-the-visual-studio-installer"></a>Eseguire gli aggiornamenti tramite il programma di installazione di Visual Studio

1. Aprire il programma di installazione. Prima di continuare, potrebbe essere necessario aggiornare il programma di installazione. In questo caso, viene richiesto di effettuare questa operazione.

   > [!NOTE]
   > In un computer che esegue Windows 10, il programma di installazione compare sotto la lettera **P** come **Programma di installazione di Visual Studio** ocome **Programma di installazione di Microsoft Visual Studio**.

1. Nella pagina **Prodotto** del programma di installazione cercare l'edizione di Visual Studio precedentemente installata.

1. Se è disponibile un aggiornamento, viene visualizzato un pulsante **Aggiorna**. La verifica della disponibilità di un aggiornamento potrebbe richiedere alcuni secondi.

   Scegliere il pulsante **Aggiorna** per installare gli aggiornamenti.

     ![Aggiornare Visual Studio 2017 usando il Programma di installazione di Visual Studio](media/update-visual-studio.png "Aggiornare Visual Studio usando il Programma di installazione di Visual Studio")

::: moniker-end

::: moniker range="vs-2019"

Si consiglia di eseguire [](/visualstudio/releases/2019/release-notes/) l'aggiornamento alla versione più recente di Visual Studio in modo da ottenere sempre le funzionalità, le correzioni e i miglioramenti più recenti.

Se non è ancora stato installato Visual Studio, passare alla pagina [Visual Studio download](https://visualstudio.microsoft.com/downloads) per installarlo gratuitamente. Se attualmente si usa una versione diversa di Visual Studio, è possibile installare le versioni di [Visual Studio side-by-side](../install/install-visual-studio-versions-side-by-side.md)o disinstallare le versioni [precedenti di Visual Studio](../install/uninstall-visual-studio.md).

> [!IMPORTANT]
> Per installare, aggiornare o modificare Visual Studio, è necessario accedere con un account con autorizzazioni amministrative. Per altre informazioni, vedere [Autorizzazioni utente e Visual Studio](../ide/user-permissions-and-visual-studio.md).
>
> [!NOTE]
> Questo argomento si applica a Visual Studio in Windows. Per Visual Studio per Mac, vedere [Aggiornare Visual Studio per Mac](/visualstudio/mac/update).

Ecco come aggiornare Visual&nbsp;Studio&nbsp;2019.

## <a name="use-the-visual-studio-installer"></a>Usare il programma di installazione di Visual Studio

1. Individuare il **programma di installazione di Visual Studio** all'interno del computer in uso.

   Nel menu Start di Windows è possibile cercare "programma di installazione".

   ![Programma di installazione di Visual Studio](media/vs-2019/visual-studio-installer.png "Cercare il Programma di installazione di Visual Studio")

   Prima di continuare, potrebbe essere necessario aggiornare il programma di installazione. In questo caso, seguire i prompt.

1. Nel programma di installazione cercare l'edizione di Visual Studio installata.

   Se ad esempio è stato precedentemente installato Visual&nbsp;Studio Community&nbsp;2019 ed è disponibile un aggiornamento, nel programma di installazione verrà visualizzato un messaggio **Aggiornamento disponibile**.

     ![Selezionare l'edizione Visual Studio 2019 da aggiornare](media/vs-2019/vs-installer-update-visual-studio-community.png "Selezionare l'edizione Visual Studio 2019 da aggiornare")

1. Scegliere **Aggiorna** per installare gli aggiornamenti.

    ![Selezionare il pulsante Aggiorna per installare gli aggiornamenti](media/vs-2019/vs-installer-choose-update-visual-studio-community.png "Selezionare il pulsante Aggiorna per installare gli aggiornamenti")

1. Al termine dell'aggiornamento, potrebbe essere richiesto di riavviare il computer. In tal caso, eseguire questa operazione e quindi avviare Visual Studio come si fa normalmente.

   Se non viene richiesto di riavviare il computer, scegliere **Avvia** per avviare Visual Studio dal programma di installazione.

    ![Selezionare il pulsante Avvia per avviare Visual Studio](media/vs-2019/choose-launch-visual-studio-community.png "Selezionare il pulsante Avvia per avviare Visual Studio")

## <a name="use-the-ide"></a>Usare l'IDE

È possibile verificare la disponibilità di un aggiornamento e quindi installarlo dalla barra dei menu o dalla casella di ricerca in Visual Studio 2019.

### <a name="open-visual-studio"></a>Aprire Visual Studio.

1. Dal menu **Start** di Windows scegliere **Visual Studio 2019**.

    ![Open Visual Studio 2019](media/vs-2019/vs-installer-visual-studio-2019.png "Aprire Visual Studio 2019 da Windows")

1. Sotto **Inizia** scegliere un'opzione qualsiasi per aprire l'IDE.

    ![Aprire il Programma di installazione di Visual Studio](media/vs2019-choose-option-from-get-started.png "Aprire il Programma di installazione di Visual Studio")

    Viene aperto Visual Studio. Nell'IDE viene visualizzato un messaggio **Aggiornamento Visual Studio 2019**.

    ![Messaggio "Aggiornamento Visual Studio 2019" nell'IDE](media/vs-2019/update-visual-studio-ide-message.png "Messaggio di Visual Studio 2019 nell'IDE")

1. Nel messaggio **Aggiornamento Visual Studio 2019** scegliere **Visualizza dettagli**.

   ![Scegliere il pulsante Visualizza dettagli nel messaggio di aggiornamento dell Visual Studio IDE 2019](media/vs-2019/update-visual-studio-ide-view-details.png "Scegliere il pulsante Visualizza dettagli nel messaggio di aggiornamento Visual Studio 2019")

1. Nella finestra di dialogo **Aggiornamento scaricato e pronto per l'installazione** scegliere **Aggiorna**.

     ![Scegliere il pulsante Aggiorna nella finestra di dialogo "Aggiorna scaricato e pronto per l'installazione"](media/vs-2019/update-ready-install-visual-studio-community-from-ide.png "Scegliere il pulsante Aggiorna nella finestra di dialogo &quot;Aggiornamento scaricato e pronto per l'installazione&quot;")

   Visual Studio viene aggiornato, chiuso e quindi riaperto.

### <a name="in-visual-studio"></a>In Visual Studio

1. Dalla barra dei menu scegliere **?** e quindi scegliere **Controlla aggiornamenti**.

     ![Scegliere "Controlla aggiornamenti" dal menu ?](media/vs-2019/vs-ide-check-updates-help-menu.png "Scegliere &quot;Controlla aggiornamenti&quot; dal menu ?")

    > [!NOTE]
    > È anche possibile usare la casella di ricerca nell'IDE per controllare se sono disponibili aggiornamenti. Premere **CTRL** + **Q,** digitare "controlla la disponibilità di aggiornamenti" e quindi scegliere il risultato della ricerca corrispondente.

1. Nella finestra di dialogo **Aggiornamento disponibile** scegliere **Aggiorna**.

     ![Scegliere il pulsante Aggiorna nella finestra di dialogo "Aggiorna disponibile"](media/vs-2019/update-visual-studio-community-from-ide.png "Scegliere il pulsante Aggiorna nella finestra di dialogo &quot;Aggiorna disponibile&quot;")

   Visual Studio viene aggiornato, chiuso e quindi riaperto.

## <a name="use-the-notifications-hub"></a>Usare l'hub Notifiche

1. In Visual Studio salvare il lavoro.

1. Scegliere l'icona di notifica nell'angolo in basso a destra dell'IDE di Visual Studio per aprire l'hub **Notifiche**.

   ![Icona di notifica nell'IDE Visual Studio](media/vs-2019/notification-bar.png "Icona di notifica nell'IDE Visual Studio")

1. Nell'**hub Notifiche** scegliere l'aggiornamento che si vuole installare e quindi scegliere **Visualizza dettagli**.

     ![Hub di notifica in Visual Studio 2019](media/vs-2019/notification-hub-update.png "Hub di notifica in Visual Studio 2019")

      > [!TIP]
      > Un aggiornamento per un'edizione di Visual Studio 2019 è cumulativo, quindi scegliere sempre di installare quello con il numero di versione più recente.

1. Nella finestra di dialogo **Aggiornamento disponibile** scegliere **Aggiorna**.

   Visual Studio viene aggiornato, chiuso e quindi riaperto.

## <a name="customize-update-settings"></a>Personalizzare le impostazioni di aggiornamento

È possibile personalizzare le impostazioni di aggiornamento in Visual Studio in diversi modi, ad esempio modificando la modalità di installazione e selezionando i download automatici.

Esistono due modalità di installazione tra cui scegliere:

* **Installa durante il download**
* **Scarica tutto, quindi installa**

È anche possibile scegliere l'impostazione **Scarica automaticamente gli aggiornamenti** che consente il download degli aggiornamenti mentre il computer è inattivo.

Ecco come:

1. Sulla barra dei menu scegliere **Strumenti** > **Opzioni**.

2. Espandere **Ambiente** e quindi scegliere **Aggiornamenti prodotto**.

    ![Impostazioni di aggiornamento in Visual Studio](media/vs-2019/update-settings-options.png)

3. Scegliere la modalità di installazione e le opzioni di download automatico desiderate per gli aggiornamenti di Visual Studio.

::: moniker-end

::: moniker range=">=vs-2022"

Si consiglia di eseguire [](/visualstudio/releases/2022/release-notes/) l'aggiornamento alla versione più recente di Visual Studio in modo da ottenere sempre le funzionalità, le correzioni e i miglioramenti più recenti.

Se non è ancora stato installato Visual Studio, passare alla pagina [Visual Studio download](https://visualstudio.microsoft.com/downloads) per installarlo gratuitamente. Se attualmente si usa una versione diversa di Visual Studio, è possibile installare le versioni di [Visual Studio side-by-side](../install/install-visual-studio-versions-side-by-side.md)o disinstallare le versioni [precedenti di Visual Studio](../install/uninstall-visual-studio.md).

> [!IMPORTANT]
> Per installare, aggiornare o modificare Visual Studio, è necessario accedere con un account con autorizzazioni amministrative. Per altre informazioni, vedere [Autorizzazioni utente e Visual Studio](../ide/user-permissions-and-visual-studio.md).
>
> [!NOTE]
> Questo argomento si applica a Visual Studio in Windows. Per Visual Studio per Mac, vedere [Aggiornare Visual Studio per Mac](/visualstudio/mac/update).

Ecco come aggiornare Visual &nbsp; Studio &nbsp; 2022.

## <a name="use-the-visual-studio-installer"></a>Usare il programma di installazione di Visual Studio

1. Individuare il **programma di installazione di Visual Studio** all'interno del computer in uso.

   Nel menu Start di Windows è possibile cercare "programma di installazione".

   ![Programma di installazione di Visual Studio](media/vs-2019/visual-studio-installer.png "Cercare il Programma di installazione di Visual Studio")

   Prima di continuare, potrebbe essere necessario aggiornare il programma di installazione. In questo caso, seguire i prompt.

1. Nel programma di installazione cercare l'edizione di Visual Studio installata.

   Ad esempio, se in precedenza è stato installato Visual &nbsp; Studio Community &nbsp; 2022  ed è disponibile un aggiornamento, nel programma di installazione viene visualizzato un messaggio Aggiorna disponibile.

     ![Selezionare l'edizione Visual Studio 2019 da aggiornare](media/vs-2019/vs-installer-update-visual-studio-community.png "Selezionare l'edizione Visual Studio 2019 da aggiornare")

1. Scegliere **Aggiorna** per installare gli aggiornamenti.

    ![Selezionare il pulsante Aggiorna per installare gli aggiornamenti](media/vs-2019/vs-installer-choose-update-visual-studio-community.png "Selezionare il pulsante Aggiorna per installare gli aggiornamenti")

1. Al termine dell'aggiornamento, potrebbe essere richiesto di riavviare il computer. In tal caso, eseguire questa operazione e quindi avviare Visual Studio come si fa normalmente.

   Se non viene richiesto di riavviare il computer, scegliere **Avvia** per avviare Visual Studio dal programma di installazione.

    ![Selezionare il pulsante Avvia per avviare Visual Studio](media/vs-2019/choose-launch-visual-studio-community.png "Selezionare il pulsante Avvia per avviare Visual Studio")

## <a name="use-the-ide"></a>Usare l'IDE

È possibile cercare un aggiornamento e quindi installarlo usando la barra dei menu o la casella di ricerca in Visual Studio 2022.

### <a name="open-visual-studio"></a>Aprire Visual Studio.

1. Dal menu **Start di** Windows scegliere Visual Studio **2022.**

    ![Open Visual Studio 2022](media/vs-2019/vs-installer-visual-studio-2019.png "Aprire Visual Studio 2019 da Windows")

1. Sotto **Inizia** scegliere un'opzione qualsiasi per aprire l'IDE.

    ![Aprire il Programma di installazione di Visual Studio](media/vs2019-choose-option-from-get-started.png "Aprire il Programma di installazione di Visual Studio")

    Viene aperto Visual Studio. Nell'IDE viene visualizzato **un Visual Studio di aggiornamento di 2022.**

    ![Messaggio "Aggiornamento Visual Studio 2019" nell'IDE](media/vs-2019/update-visual-studio-ide-message.png "Messaggio di Visual Studio 2019 nell'IDE")

1. Nel messaggio **Visual Studio aggiornamento 2022** scegliere **Visualizza dettagli**.

   ![Scegliere il pulsante Visualizza dettagli nel messaggio di aggiornamento dell Visual Studio IDE 2019](media/vs-2019/update-visual-studio-ide-view-details.png "Scegliere il pulsante Visualizza dettagli nel messaggio di aggiornamento Visual Studio 2019")

1. Nella finestra di dialogo **Aggiornamento scaricato e pronto per l'installazione** scegliere **Aggiorna**.

     ![Scegliere il pulsante Aggiorna nella finestra di dialogo "Aggiorna scaricato e pronto per l'installazione"](media/vs-2019/update-ready-install-visual-studio-community-from-ide.png "Scegliere il pulsante Aggiorna nella finestra di dialogo &quot;Aggiornamento scaricato e pronto per l'installazione&quot;")

   Visual Studio viene aggiornato, chiuso e quindi riaperto.

### <a name="in-visual-studio"></a>In Visual Studio

1. Dalla barra dei menu scegliere **?** e quindi scegliere **Controlla aggiornamenti**.

     ![Scegliere "Controlla aggiornamenti" dal menu ?](media/vs-2019/vs-ide-check-updates-help-menu.png "Scegliere &quot;Controlla aggiornamenti&quot; dal menu ?")

    > [!NOTE]
    > È anche possibile usare la casella di ricerca nell'IDE per controllare se sono disponibili aggiornamenti. Premere **CTRL** + **Q,** digitare "controlla la disponibilità di aggiornamenti" e quindi scegliere il risultato della ricerca corrispondente.

1. Nella finestra di dialogo **Aggiornamento disponibile** scegliere **Aggiorna**.

     ![Scegliere il pulsante Aggiorna nella finestra di dialogo "Aggiorna disponibile"](media/vs-2019/update-visual-studio-community-from-ide.png "Scegliere il pulsante Aggiorna nella finestra di dialogo &quot;Aggiorna disponibile&quot;")

   Visual Studio viene aggiornato, chiuso e quindi riaperto.

## <a name="use-the-notifications-hub"></a>Usare l'hub Notifiche

1. In Visual Studio salvare il lavoro.

1. Scegliere l'icona di notifica nell'angolo in basso a destra dell'IDE di Visual Studio per aprire l'hub **Notifiche**.

   ![Icona di notifica nell'IDE Visual Studio](media/vs-2019/notification-bar.png "Icona di notifica nell'IDE Visual Studio")

1. Nell'**hub Notifiche** scegliere l'aggiornamento che si vuole installare e quindi scegliere **Visualizza dettagli**.

     ![Hub di notifica in Visual Studio 2019](media/vs-2019/notification-hub-update.png "Hub di notifica in Visual Studio 2019")

      > [!TIP]
      > Un aggiornamento per un'edizione di Visual Studio 2022 è cumulativo, quindi scegliere sempre di installare quello con il numero di versione più recente.

1. Nella finestra di dialogo **Aggiornamento disponibile** scegliere **Aggiorna**.

   Visual Studio viene aggiornato, chiuso e quindi riaperto.

## <a name="customize-update-settings"></a>Personalizzare le impostazioni di aggiornamento

È possibile personalizzare le impostazioni di aggiornamento in Visual Studio in diversi modi, ad esempio modificando la modalità di installazione e selezionando i download automatici.

Esistono due modalità di installazione tra cui scegliere:

* **Installa durante il download**
* **Scarica tutto, quindi installa**

È anche possibile scegliere l'impostazione **Scarica automaticamente gli aggiornamenti** che consente il download degli aggiornamenti mentre il computer è inattivo.

Ecco come:

1. Sulla barra dei menu scegliere **Opzioni** > **strumenti**.

2. Espandere **Ambiente** e quindi scegliere **Aggiornamenti prodotto**.

    ![Impostazioni di aggiornamento in Visual Studio](media/vs-2019/update-settings-options.png)

3. Scegliere la modalità di installazione e le opzioni di download automatico desiderate per gli aggiornamenti di Visual Studio.
::: moniker-end

## <a name="administrator-updates"></a>Aggiornamenti dell'amministratore

Se si fa parte di un'organizzazione che centralizza la gestione delle installazioni software, l'amministratore dell'organizzazione può Visual Studio l'aggiornamento nel computer. Per altre informazioni su come controllare o configurare i tipi di aggiornamenti che il computer può accettare, vedere Using [Gestione configurazione to deploy Visual Studio Updates](../install/applying-administrator-updates.md#using-configuration-manager-to-deploy-visual-studio-updates).

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Vedi anche

* [Installare versioni di Visual Studio side-by-side](install-visual-studio-versions-side-by-side.md)
* [Aggiornare un'installazione di rete di Visual Studio](update-a-network-installation-of-visual-studio.md)
* [Guida di Visual Studio per le aziende](visual-studio-enterprise-guide.md)
* [Aggiornare Visual Studio secondo una baseline di manutenzione](update-servicing-baseline.md)
* [Controllare gli aggiornamenti delle distribuzioni di rete di Visual Studio](controlling-updates-to-visual-studio-deployments.md)
* [Modificare Visual Studio](modify-visual-studio.md)
* [Disinstallare Visual Studio](uninstall-visual-studio.md)
