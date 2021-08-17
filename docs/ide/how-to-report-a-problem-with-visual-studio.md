---
title: Come segnalare un problema con Visual Studio
description: Informazioni su come segnalare un problema con Visual Studio
ms.date: 03/11/2018
ms.topic: how-to
ms.assetid: bee01179-cde5-4419-9095-190ee0ba5902
author: madskristensen
ms.author: madsk
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 354153eb2a468b7b42373dbf05315275d4ed745c
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122028176"
---
# <a name="how-to-report-a-problem-with-visual-studio-or-visual-studio-installer"></a>Come segnalare un problema con Visual Studio o il programma di installazione di Visual Studio

> [!NOTE]
> Per Visual Studio per Mac, vedere [Come segnalare un problema in Visual Studio per Mac](/visualstudio/mac/report-a-problem).

È possibile segnalare un problema da un Visual Studio o dal relativo programma di installazione. Lo strumento di feedback incorporato consente di aggiungere facilmente informazioni di diagnostica che consentono ai Visual Studio team di diagnosticare e risolvere i problemi. Questa è la procedura per segnalare un problema.

1. **In Visual Studio**, selezionare l'icona di feedback nell'angolo superiore destro e selezionare Segnala un problema. È anche possibile accedere al feedback tool dal menu **Help**  >  **Send Feedback** Report a  >  **Problem**.
![Screenshot che mostra l'icona di feedback selezionata nell'angolo superiore destro della finestra Visual Studio e Segnala un problema selezionata nel menu di scelta rapida.](media/feedback-button.png)
In alternativa, segnalare un problema in **Programma di installazione di Visual Studio** se non è possibile installare Visual Studio o non è possibile accedere allo strumento di feedback all'interno di Visual Studio.  Nel programma di installazione selezionare l'icona di feedback nell'angolo superiore destro e selezionare Segnala un problema.
![Screenshot che mostra l'icona di feedback selezionata nell'angolo superiore destro del Programma di installazione di Visual Studio e Segnala un problema selezionata nel menu di scelta rapida.](media/installer.png)

1. Facendo **clic su Segnala** un problema si aprirà il browser predefinito e si accede usando lo stesso account che si usa per accedere a Visual Studio

   ![Accedere per segnalare un problema](../ide/media/feedback-browser-top.png)

1. Per iniziare, immettere il titolo descrittivo del report sui bug. Deve contenere almeno 25 caratteri.

    ![Segnalare un problema](../ide/media/feedback-report.png)

1. Dopo aver avviato la digitazione, i possibili duplicati vengono visualizzati sotto il campo del titolo

    ![Cercare duplicati](../ide/media/feedback-search.png)

1. Selezionare i possibili report di bug duplicati per verificare se ne esiste uno corrispondente al proprio problema. In caso contrario, votare invece di creare un ticket personalizzato.

    ![Votare i duplicati](../ide/media/feedback-duplicate.png)

2. Se non sono stati trovati duplicati, continuare immettendo una descrizione del problema. È importante essere il più chiari possibile per aumentare le probabilità di riprodurre il bug. Assicurarsi di includere passaggi di riproduzione chiari.

3. Se pertinente per il report sui bug, acquisire uno screenshot selezionando la casella di controllo Includi Visual Studio *screenshot.*

    ![Acquisire uno screenshot ](../ide/media/feedback-screenshot.png) *Solo i tecnici Microsoft possono visualizzare lo screenshot*

    È anche possibile ritagliare lo screenshot direttamente nel browser per rimuovere eventuali parti sensibili o non correlate.

4. Uno dei modi migliori per aiutare il team di progettazione Visual Studio risolvere il problema, è fornire un file di traccia e di dump dell'heap da esaminare. È possibile eseguire facilmente questa operazione registrando i passaggi che hanno restituito il bug.

    ![Registrare le azioni ](../ide/media/feedback-recording.png) *solo i tecnici Microsoft possono visualizzare la registrazione*

5. Esaminare i file allegati e caricare file aggiuntivi se si ritiene che sia utile diagnosticare il problema.

    ![File allegati ](../ide/media/feedback-attachments.png) *Solo i tecnici Microsoft possono visualizzare i file allegati*

6. L'ultimo passaggio consiste nel premere il **pulsante** Invia. L'invio del report lo invierà direttamente al sistema Visual Studio di segnalazione dei bug in attesa di analisi.

## <a name="when-further-information-is-needed"></a>Quando sono necessarie altre informazioni

Quando un problema non contiene informazioni importanti, viene assegnato lo **stato Altre** informazioni necessarie. Si commenta il problema con le informazioni specifiche necessarie e si riceverà una notifica tramite posta elettronica. Se le informazioni non vengono ricevute entro sette giorni, verrà inviato un promemoria. Successivamente, il ticket viene chiuso dopo 14 giorni di inattività.

1. Seguire il collegamento nel messaggio di posta elettronica al report del problema o passare al home page per visualizzare tutti i report nello **stato Needs More Info (Altre** informazioni necessarie).

    ![Screenshot della home page della finestra Visual Studio Feedback. Viene elencato un elemento di feedback, contrassegnato con l'etichetta "Need More Info" in rosso.](../ide/media/feedback-my-feedback.png)

1. Selezionando il collegamento Fornisci altre informazioni nel report del problema si passa a una nuova schermata. Da qui è possibile visualizzare le informazioni richieste.

   ![Screenshot della finestra Visual Studio commenti e suggerimenti che mostra le informazioni richieste da Microsoft per la risoluzione del problema.](../ide/media/feedback-need-more-info.png)

1. È possibile specificare altre informazioni aggiungendo commenti o allegati oppure registrando la procedura. Questa esperienza è simile alla segnalazione di un nuovo problema o all'inserimento di informazioni aggiuntive quando si vota un problema.

1. Il tecnico di Microsoft richiedente riceve la notifica dell'aggiunta di nuove informazioni. Se le informazioni sono sufficienti per l'analisi del problema, lo stato del problema viene modificato. In caso contrario, il tecnico richiede ancora più informazioni.

È possibile visualizzare queste richieste nella **schermata Commenti e suggerimenti** insieme a tutti gli altri **problemi** e **suggerimenti.**

## <a name="search-for-solutions-or-provide-feedback"></a>Cercare soluzioni o fornire commenti e suggerimenti

Se non si vuole o non si può usare Visual Studio per segnalare un problema, tenere presente che il problema potrebbe essere già stato segnalato e potrebbe essere stata pubblicata una soluzione nella pagina della [community degli sviluppatori di Visual Studio](https://developercommunity2.visualstudio.com/search?space=8).

Se non si ha un problema da segnalare ma si vuole suggerire una funzionalità, è anche possibile farlo. Per altre informazioni, vedere la pagina [Suggerire una funzionalità](https://aka.ms/feedback/suggest?space=8).

## <a name="see-also"></a>Vedi anche

* [Linee guida per Community per sviluppatori](./developer-community-guidelines.md)
* [Opzioni per commenti e suggerimenti in Visual Studio](../ide/feedback-options.md)
* [Segnalare un problema con Visual Studio per Mac](/visualstudio/mac/report-a-problem)
* [Segnalare un problema con C++](/cpp/how-to-report-a-problem-with-the-visual-cpp-toolset)
* [Visual Studio Strumenti Community](https://aka.ms/feedback/suggest?space=8)
* [Privacy dei dati della community degli sviluppatori](developer-community-privacy.md)
