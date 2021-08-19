---
title: Impostare le autorizzazioni | Microsoft Docs
description: Informazioni su come un amministratore di un computer concede le autorizzazioni di sicurezza necessarie per la profilatura a un utente o a un gruppo che non dispone delle autorizzazioni di amministratore.
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- profiling, setting permissions
- security [Visual Studio ALM], setting permissions
- permissions [Visual Studio ALM], profiling
- profiling tools, setting profiling permissions
- performance tools, setting profiling permissions
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 56dee60e63ce2f6d3d298c3c70e57f59910a16ab
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122150222"
---
# <a name="how-to-set-permissions"></a>Procedura: Impostare le autorizzazioni

Questo articolo descrive il modo in cui un amministratore di un computer concede le autorizzazioni di sicurezza necessarie per la profilatura a un utente o un gruppo che non dispone di autorizzazioni di amministratore per quel computer.

Secondo un principio di base della sicurezza, le applicazioni devono essere eseguite con le autorizzazioni strettamente necessarie. Questo principio vale anche per gli utenti. Se gli utenti sono in grado di operare in modo efficace con i privilegi del gruppo Users anziché con quelli del gruppo Administrators, non è necessario concedere loro le autorizzazioni specifiche degli amministratori. La prima procedura, "Per creare un account utente con autorizzazioni utente", descrive come creare un account utente per un membro del gruppo Users.

I membri del gruppo Users dovranno accedere alle cartelle e ai file presenti sul disco che vengono condivisi con altri membri del team. Nella seconda procedura, "Per concedere l'accesso ai file di progetto condivisi", viene descritto come garantire questo tipo di accesso.

I membri del gruppo Users possono eseguire gli strumenti di profilatura se viene concesso loro di accedere al driver software per tali strumenti. L'ultima procedura, "Per concedere l'accesso al driver di profilatura", descrive come garantire l'accesso al driver in questione.

> [!NOTE]
> Per eseguire le operazioni previste da queste procedure sono necessarie autorizzazioni di amministratore.

## <a name="to-create-a-user-account-that-has-user-permissions"></a>Per creare un account utente con autorizzazioni utente

1. Fare clic con il **pulsante destro Computer locale** e quindi scegliere **Gestisci.**

     Verrà aperta la finestra **Gestione computer**.

2. Espandere **Utenti e gruppi locali**.

3. Fare clic con il pulsante destro del mouse sulla cartella **Utenti** e quindi fare clic su **Nuovo utente**.

     Verrà visualizzata la finestra di dialogo **New User** (Nuovo utente).

4. Completare i campi di questa finestra di dialogo con le informazioni relative all'account utente che si sta creando. Consente di specificare una password. Facoltativamente, selezionare la casella di controllo che richiede all'utente di cambiare la password al successivo accesso.

5. Fare **clic su** Crea e quindi su **Chiudi.**

     Il nuovo utente verrà visualizzato nel gruppo Users, ovvero un gruppo di utenti che non dispone di autorizzazioni di amministratore.

## <a name="to-grant-access-to-shared-project-files"></a>Per concedere l'accesso ai file di progetto condivisi

1. In Esplora risorse (o Esplora file) individuare la radice dell'albero delle cartelle relativa ai file di progetto usati dall'utente e condivisi dal team del progetto.

     Il percorso della cartella potrebbe essere simile al seguente:

    ```cmd
    D:\ourProject
    ```

2. Fare clic con il pulsante destro del mouse sulla cartella e quindi fare clic su **Proprietà**.

     Verrà **\<folder name> visualizzata la finestra** di dialogo Proprietà .

3. Fare clic sulla scheda **Security** (Sicurezza).

4. Fare clic sul nome dell'account utente nella casella **Utenti e gruppi**.

5. Nella casella **Autorizzazioni per \<user name>** selezionare la casella di controllo Controllo **completo**.

6. Fare clic su **OK**.

     In questo modo all'utente vengono concesse le autorizzazioni per l'albero delle cartelle condiviso che ha inizio con la cartella selezionata nel passaggio 5.

## <a name="to-grant-access-to-the-profiling-driver"></a>Per concedere l'accesso al driver di profilatura

1. Aprire un prompt dei comandi come amministratore.

2. Passare alla directory seguente:

    ```cmd
    <drive>:\Program Files\Microsoft Visual Studio 14\Team Tools\Performance Tools
    ```

3. Eseguire il comando seguente:

    ```cmd
    vsperfcmd /admin:driver,start /admin:service,start
    ```

     Questo comando consente di installare e avviare il driver per gli strumenti di profilatura.

     Questo comando avvia il driver e il servizio di profilatura in modo che gli utenti non amministratori possano usare le funzionalità di profilatura disponibili nello spazio di processo utente. Solo un amministratore può eseguire il comando, che non avrà effetto se eseguito da utenti senza privilegi di amministratore.

     Gli effetti derivanti dall'esecuzione di questa operazione vengono annullati dopo il riavvio del computer, a meno che non venga eseguito anche l'ultimo passaggio di questa procedura.

4. Eseguire il comando per consentire a un utente o un gruppo che non dispone dell'accesso di amministratore al computer di accedere alla funzionalità del driver di profilatura:

    ```cmd
    vsperfcmd /admin:security,allow,<right[,right],<user name|group name>
    ```

     Questo comando concede \<user name> all'account o \<group name> l'accesso agli strumenti di profilatura. \<right>L'opzione determina la funzionalità di profilatura a cui l'utente può accedere. \<right>L'opzione può essere uno o più dei valori seguenti:

    - FullAccess: consente l'accesso a tutti i metodi di profilatura, inclusa la raccolta dei dati sulle prestazioni della profilatura dei servizi, tra sessioni e mediante campionamento.

    - SampleProfiling: consente l'accesso ai metodi di profilatura dei campioni.

    - CrossSession: consente l'accesso alla profilatura tra sessioni richiesta per la profilatura dei servizi.

5. (Facoltativo) Per conservare i risultati di uno dei passaggi precedenti dopo il riavvio del computer, eseguire il comando seguente:

    ```cmd
    vsperfcmd /admin:driver,autostart,on
    ```

   Dopo aver effettuato l'accesso, gli utenti specificati saranno in grado di usare gli strumenti di profilatura senza autorizzazioni di amministratore.

## <a name="see-also"></a>Vedi anche

[Configurare le sessioni di prestazioni](../profiling/configuring-performance-sessions.md) 
 [VSPerfCmd](../profiling/vsperfcmd.md) 
 [Profilatura e Windows vista](../profiling/profiling-and-windows-vista-security.md)
