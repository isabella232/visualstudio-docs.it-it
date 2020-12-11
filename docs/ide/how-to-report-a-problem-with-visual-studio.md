---
title: Come segnalare un problema con Visual Studio
description: Informazioni su come segnalare un problema con Visual Studio
ms.date: 03/11/2018
ms.topic: how-to
ms.assetid: bee01179-cde5-4419-9095-190ee0ba5902
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2956372882d4449345d026e691a12afb2988054a
ms.sourcegitcommit: 6ef4e46c786c5bbcc52cd9c30e5ddfca12ea8b3c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/10/2020
ms.locfileid: "97050827"
---
# <a name="how-to-report-a-problem-with-visual-studio-or-visual-studio-installer"></a>Come segnalare un problema con Visual Studio o il programma di installazione di Visual Studio

> [!NOTE]
> Per Visual Studio per Mac, vedere [Come segnalare un problema in Visual Studio per Mac](/visualstudio/mac/report-a-problem).

È possibile segnalare un problema da Visual Studio o dal programma di installazione. Lo strumento di feedback integrato consente di aggiungere facilmente informazioni di diagnostica che consentono ai team di Visual Studio di diagnosticare e risolvere i problemi. Questa è la procedura per segnalare un problema.

1. **In Visual Studio**, selezionare l'icona di feedback nell'angolo superiore destro e selezionare Segnala un problema. È anche possibile accedere allo strumento per il feedback dal menu **Guida**  >  **Invia commenti e suggerimenti**  >  **segnala un problema**.
![Elemento popup per la segnalazione di un problema nella community degli sviluppatori di Visual Studio](media/feedback-button.png) In alternativa, segnalare un problema nel **programma di installazione di Visual Studio** se non è possibile installare Visual Studio o non è possibile accedere allo strumento di feedback all'interno di Visual Studio.  Nel programma di installazione selezionare l'icona di feedback nell'angolo superiore destro e selezionare Segnala un problema.
![Elemento popup per la segnalazione di un problema nella community degli sviluppatori di Visual Studio](media/installer.png)

1. Se si fa clic su **segnala un problema** , si aprirà il browser predefinito e si effettuerà l'accesso con lo stesso account usato per accedere a Visual Studio

   ![Accedere per segnalare un problema](../ide/media/feedback-browser-top.png)

1. Per iniziare, immettere il titolo descrittivo del report sui bug. Deve avere una lunghezza di almeno 25 caratteri.

    ![Segnalare un problema](../ide/media/feedback-report.png)

1. Quando si inizia a digitare, i duplicati possibili vengono visualizzati nel campo titolo

    ![Cerca duplicati](../ide/media/feedback-search.png)

1. Selezionare le possibili segnalazioni di bug duplicati per verificare se esiste un problema corrispondente. Se è presente, votarlo invece di creare un ticket personalizzato.

    ![Vota i duplicati](../ide/media/feedback-duplicate.png)

2. Se non è stato trovato alcun duplicato, continuare inserendo una descrizione del problema. È importante essere il più chiaro possibile per aumentare le probabilità che Microsoft possa riprodurre il bug. Assicurarsi di includere i passaggi della riproduzione Cancella.

3. Se pertinente per il report sui bug, scattare una schermata selezionando la casella di controllo *Includi schermata di Visual Studio* .

    ![Acquisisci uno screenshot ](../ide/media/feedback-screenshot.png) *solo i tecnici Microsoft possono visualizzare lo screenshot*

    È anche possibile ritagliare lo screenshot direttamente nel browser per rimuovere tutte le parti sensibili o non correlate.

4. Uno dei modi migliori per consentire al team di progettazione di Visual Studio di risolvere il problema consiste nel fornire un file di traccia e di dump di heap da esaminare. Questa operazione può essere eseguita facilmente registrando i passaggi che hanno generato il bug.

    ![Registrare le azioni ](../ide/media/feedback-recording.png) *solo i tecnici Microsoft possono visualizzare la registrazione*

5. Esaminare i file allegati e caricare i file aggiuntivi se si ritiene che possano essere utili per diagnosticare il problema.

    ![File allegati ](../ide/media/feedback-attachments.png) *solo i tecnici Microsoft possono visualizzare i file allegati*

6. L'ultimo passaggio consiste nell'premere il pulsante **Submit (Invia** ). L'invio del report lo invierà direttamente al sistema interno di segnalazione dei bug di Visual Studio in attesa di valutazione.

## <a name="when-further-information-is-needed"></a>Quando sono necessarie altre informazioni

Quando in un problema mancano informazioni importanti, viene assegnato lo stato **needs more info (altre informazioni** ). Il problema viene commentato con le informazioni specifiche necessarie e si riceverà una notifica tramite posta elettronica. Se le informazioni non vengono ricevute entro sette giorni, viene inviato un promemoria. Successivamente, il ticket viene chiuso dopo 14 giorni di inattività.

1. Per visualizzare tutti i report nello stato **needs more info (ulteriori informazioni** ), seguire il collegamento nel messaggio di posta elettronica al report relativo al problema o passare alla Home page.

    ![Commenti e suggerimenti](../ide/media/feedback-my-feedback.png)

1. Selezionando il collegamento fornire altre informazioni nel report problema si passa a una nuova schermata. Da qui è possibile visualizzare le informazioni richieste.

   ![Commenti e suggerimenti](../ide/media/feedback-need-more-info.png)

1. È possibile specificare altre informazioni aggiungendo commenti o allegati oppure registrando la procedura. Questa esperienza è simile alla segnalazione di un nuovo problema o all'inserimento di informazioni aggiuntive quando si vota un problema.

1. Il tecnico di Microsoft richiedente riceve la notifica dell'aggiunta di nuove informazioni. Se le informazioni sono sufficienti per l'analisi del problema, lo stato del problema viene modificato. In caso contrario, il tecnico richiede ancora più informazioni.

È possibile visualizzare queste richieste nella schermata **My feedback** insieme a tutti gli altri **problemi** e **suggerimenti**.

## <a name="search-for-solutions-or-provide-feedback"></a>Cercare soluzioni o fornire commenti e suggerimenti

Se non si vuole o non si può usare Visual Studio per segnalare un problema, tenere presente che il problema potrebbe essere già stato segnalato e potrebbe essere stata pubblicata una soluzione nella pagina della [community degli sviluppatori di Visual Studio](https://developercommunity.visualstudio.com/).

Se non si ha un problema da segnalare ma si vuole suggerire una funzionalità, è disponibile un posto anche per questa operazione. Per altre informazioni, vedere la pagina [Suggerire una funzionalità](https://developercommunity.visualstudio.com/content/idea/post.html?space=8).

## <a name="see-also"></a>Vedere anche

* [Linee guida della community degli sviluppatori](./developer-community-guidelines.md)
* [Opzioni per commenti e suggerimenti in Visual Studio](../ide/feedback-options.md)
* [Segnala un problema con Visual Studio per Mac](/visualstudio/mac/report-a-problem)
* [Segnalare un problema con C++](/cpp/how-to-report-a-problem-with-the-visual-cpp-toolset)
* [Community degli sviluppatori di Visual Studio](https://developercommunity.visualstudio.com/)
* [Privacy dei dati della community degli sviluppatori](developer-community-privacy.md)