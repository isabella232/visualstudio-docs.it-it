---
title: Come segnalare un problema con Visual Studio 2017
description: Informazioni su come segnalare un problema con Visual Studio 2017 a Microsoft in modo che sia possibile diagnosticarlo e risolverlo.
ms.custom: ''
ms.date: 03/11/2018
ms.prod: visual-studio-dev15
ms.technology: vs-acquisition
ms.topic: conceptual
ms.assetid: bee01179-cde5-4419-9095-190ee0ba5902
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a059e25546abf0d1624d3c8bc08a531d3fc4b382
ms.sourcegitcommit: c57ae28181ffe14a30731736661bf59c3eff1211
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/11/2018
ms.locfileid: "36755924"
---
# <a name="how-to-report-a-problem-with-visual-studio-2017"></a>Come segnalare un problema con Visual Studio 2017

Se si verifica un problema con Visual Studio, è importante segnalarlo a Microsoft. Di seguito viene descritto come segnalare il problema alla [community degli sviluppatori](https://developercommunity.visualstudio.com/) in modo che Microsoft possa diagnosticarlo e risolverlo.

## <a name="report-a-problem-by-using-visual-studio"></a>Segnalare un problema tramite Visual Studio

Per segnalare un problema relativo a Visual Studio, è necessario avviare la segnalazione da Visual Studio o dal programma di installazione di Visual Studio. Non è possibile farlo direttamente tramite il sito Web della [community degli sviluppatori](https://developercommunity.visualstudio.com/). La segnalazione tramite Visual Studio consente di includere automaticamente nel report le informazioni di diagnostica.

![Elemento popup per la segnalazione di un problema nella community degli sviluppatori di Visual Studio](media/report-an-issue.png)

1. In Visual Studio selezionare **Guida** > **Invia commenti e suggerimenti** > **Segnala un problema**.

   > [!TIP]
   > Se non è possibile completare l'installazione di Visual Studio o non si riesce ad accedere allo strumento per il feedback all'interno di Visual Studio, è possibile segnalare un problema tramite il **programma di installazione di Visual Studio**. A tale scopo, scegliere l'icona per il feedback nell'angolo in alto a destra del **programma di installazione di Visual Studio**.

1. Se non si è eseguito l'accesso, fare clic su **Accedi** sul lato destro dello strumento, come illustrato nello screenshot seguente. Seguire le istruzioni visualizzate per accedere.

   ![Accedere per segnalare un problema](../ide/media/sign-in-new-ux.png)

   Quando si accede, è possibile segnalare un problema che si verifica. È anche possibile votare o commentare qualsiasi altro problema pubblicato.

1. Dopo l'accesso, i **problemi** e le **attività** segnalate sono visualizzabili nella schermata **Elementi seguiti**

    ![Elementi seguiti](../ide/media/items-i-follow.png)

1. Visual Studio offre un'interfaccia che consente di cercare un problema e vedere se è stato segnalato da altri utenti. Se è già stato segnalato, è necessario contrassegnarlo per inviare a Microsoft la notifica.
   > [!NOTE]
   > Per eseguire una ricerca, immettere il testo desiderato nella casella di ricerca e premere Invio o fare clic sull'icona Ricerca.

   ![Cercare e contrassegnare problemi simili](../ide/media/search-and-vote.png)

1. Se il problema riscontrato non viene trovato, scegliere **Segnala un nuovo problema** nella parte inferiore della schermata.

   > [!NOTE]
   > Il pulsante **Segnala un nuovo problema** viene visualizzato solo nell'interfaccia di Visual Studio per la community degli sviluppatori. Non è possibile segnalare un problema direttamente nel sito Web della [community degli sviluppatori](https://developercommunity.visualstudio.com/).

1. Creare un titolo descrittivo per il problema in modo da consentirne l'invio al team di Visual Studio corretto.

1. Fornire eventuali dettagli aggiuntivi e, se possibile, descrivere la procedura per riprodurre il problema.

   ![Segnalare un problema nuovo](../ide/media/report-new-problem.png)

1. Selezionare **Avanti** per passare alla scheda **Allegati**, dove è possibile acquisire la schermata corrente per inviarla a Microsoft. Per allegare screenshot aggiuntivi o altri file, scegliere **Allega altri file**.

   ![Allegare uno screenshot alla segnalazione di un problema di Visual Studio](media/report-a-problem-screenshot.png)

1. Se non si vuole allegare uno screenshot o [registrare una procedura di riproduzione](#record-a-repro), selezionare **Avanti** per passare alla scheda **Riepilogo**.

1. Selezionare **Invia** per inviare il report, insieme a eventuali immagini, tracce o file dump. Se il pulsante **Invia** è disattivato, verificare di aver specificato un titolo e una descrizione per il report.

   Per informazioni sui dati raccolti, vedere [Data we collect](developer-community-privacy.md#data-we-collect) (Dati raccolti).

## <a name="record-a-repro"></a>Registrare una procedura di riproduzione

I file di traccia e di dump di heap sono utili per diagnosticare i problemi. Siamo grati agli utenti che usano lo strumento **Segnala un problema** per registrare la procedura che consente di riprodurre il problema e inviare i dati a Microsoft. Ecco come eseguire questa operazione:

1. Dopo avere immesso un titolo e una descrizione per il problema, selezionare **Avanti** per passare alla scheda **Allegati**.

1. Selezionare la scheda **Registra**.

1. In **Registra le azioni** selezionare l'istanza corrente di Visual Studio, se è possibile riprodurre il problema all'interno di essa. Se non è possibile, ad esempio se Visual Studio è bloccato, selezionare  **\<Crea una nuova istanza>** per registrare le azioni in una nuova istanza di Visual Studio.

1. Selezionare **Avvia registrazione**. Concedere le autorizzazioni per eseguire lo strumento.

   ![Scegliere "Avvia registrazione" per inviare un file di traccia e un file dump dell'heap all'interno della segnalazione del problema di Visual Studio](../ide/media/record-dialog-box.png)

1. Quando lo strumento **Registrazione azioni utente** viene visualizzato, seguire la procedura per riprodurre il problema.

1. Al termine, scegliere il pulsante **Arresta registrazione**.

1. Attendere alcuni minuti mentre Visual Studio raccoglie e comprime le informazioni registrate.

   Per informazioni sui dati raccolti, vedere [Data we collect](developer-community-privacy.md#data-we-collect) (Dati raccolti).

## <a name="when-further-information-is-needed-need-more-info"></a>Se sono necessarie altre informazioni (Servono altre info)

A partire da Visual Studio 2017 versione 15.5, è presente un nuovo flusso di lavoro che consente agli utenti di fornire informazioni aggiuntive nelle segnalazioni di problemi.

1. Quando nella [community di sviluppatori di Visual Studio](https://developercommunity.visualstudio.com/) un tecnico Microsoft imposta lo stato del problema su **Servono altre info**, tutti gli utenti che hanno aggiunto un post o un commento sul problema o hanno votato o seguito il problema stesso ricevono una notifica nello strumento **Segnala un problema** in Visual Studio.

   ![Notifica Servono altre info in Visual Studio](../ide/media/nmi-notification.png)

1. Fare clic sul collegamento **Visualizza problemi** per filtrare e ordinare la visualizzazione in base ai problemi che richiedono attenzione. Accanto a questi problemi è anche presente un indicatore che li differenzia nelle ricerche generiche.

1. Fare clic su un problema per visualizzare i dettagli del problema stesso.

   ![Notifica Servono altre info](../ide/media/nmi-details-view.png)

1. Per visualizzare la richiesta **Notifica Servono altre info**, fare clic sul collegamento **Visualizza la richiesta e rispondi** nella visualizzazione dei dettagli del problema. La richiesta viene visualizzata in una finestra di dialogo.

   ![Notifica Servono altre info](../ide/media/nmi-request.png)

1. È possibile specificare altre informazioni aggiungendo commenti o allegati oppure registrando la procedura. Questa esperienza è simile alla segnalazione di un nuovo problema o all'inserimento di informazioni aggiuntive quando si vota un problema.

1. Il tecnico di Microsoft richiedente riceve la notifica dell'aggiunta di nuove informazioni. Se le informazioni sono sufficienti per l'analisi del problema, lo stato del problema viene modificato. In caso contrario, il tecnico richiede ancora più informazioni.

   > [!NOTE]
   > * Quando si risponde, la notifica viene chiusa. Al suo posto viene visualizzato un banner che ringrazia l'utente e facilita l'inserimento di altre informazioni.
   > * Dopo la modifica dello stato del problema, la notifica viene chiusa per tutti gli utenti che lo seguono.
   > * Alla stessa richiesta **Servono altre info** possono rispondere più persone.
   > * Quando si accede alla [community degli sviluppatori](https://developercommunity.visualstudio.com/) direttamente da un Web browser, il flusso di lavoro **Servono altre info** non è disponibile, ma è comunque possibile aggiungere commenti e allegati.

## <a name="search-for-solutions-or-provide-feedback"></a>Cercare soluzioni o fornire commenti e suggerimenti

Se non si vuole o non si può usare Visual Studio per segnalare un problema, tenere presente che il problema potrebbe essere già stato segnalato e potrebbe essere stata pubblicata una soluzione nella [community degli sviluppatori di Visual Studio](https://developercommunity.visualstudio.com/).

Se non si vuole segnalare un problema, ma fornire commenti o suggerimenti per il prodotto, esiste una pagina specifica anche per questi scopi. Per altre informazioni, vedere la pagina [UserVoice](https://visualstudio.uservoice.com/forums/121579-visual-studio-ide).

## <a name="see-also"></a>Vedere anche

* [Comunicazioni con Microsoft](../ide/talk-to-us.md)
* [Segnalare un problema con Visual Studio per Mac](/visualstudio/mac/report-a-problem)
* [Segnalare un problema con C++](/cpp/how-to-report-a-problem-with-the-visual-cpp-toolset)
* [Community di sviluppatori di Visual Studio](https://developercommunity.visualstudio.com/)
* [Privacy dei dati della community degli sviluppatori](developer-community-privacy.md)