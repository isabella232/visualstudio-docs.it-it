---
title: Risoluzione dei problemi di installazione o di aggiornamento
description: Non sempre tutto funziona correttamente. Se l'installazione o l'aggiornamento di Visual Studio ha esito negativo, questa pagina può risultare utile.
ms.date: 09/14/2021
ms.custom: vs-acquisition
ms.topic: troubleshooting
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 556EDD3F-E365-43EE-B3DD-03AA4353F75B
author: anandmeg
ms.author: meghaanand
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 7aa65f747907181bdca40833f7a705a054a9b451
ms.sourcegitcommit: 8e74969ff61b609c89b3139434dff5a742c18ff4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/24/2021
ms.locfileid: "128428770"
---
# <a name="troubleshoot-visual-studio-installation-and-upgrade-issues"></a>Risolvere i problemi di installazione e aggiornamento di Visual Studio

> [!IMPORTANT]
> Se si è verificato un problema di installazione, è possibile chiedere assistenza. È disponibile [**un'opzione di supporto**](https://visualstudio.microsoft.com/vs/support/#talktous) per chat di installazione (solo in lingua inglese).

Questa Guida alla risoluzione dei problemi include istruzioni dettagliate per risolvere la maggior parte dei problemi di installazione.

## <a name="online-installations"></a>Installazioni online

I passaggi seguenti si applicano a un'installazione online tipica. Per un'installazione offline, vedere [Come risolvere i problemi relativi a un'installazione offline.](#offline-installations)

### <a name="step-1---check-whether-the-problem-is-a-known-issue"></a>Passaggio 1: Verificare se il problema è noto

::: moniker range="vs-2017"

Esistono alcuni problemi noti relativi al programma di installazione di Visual Studio che Microsoft sta cercando di risolvere. Per scoprire se esiste una soluzione alternativa al problema, vedere la [sezione Problemi noti delle note sulla versione](/visualstudio/releasenotes/vs2017-relnotes#-known-issues).

::: moniker-end

::: moniker range="vs-2019"

Esistono alcuni problemi noti relativi al programma di installazione di Visual Studio che Microsoft sta cercando di risolvere. Per scoprire se esiste una soluzione alternativa al problema, vedere la [sezione Problemi noti delle note sulla versione](/visualstudio/releases/2019/release-notes#-known-issues).

::: moniker-end

::: moniker range=">=vs-2022"

Esistono alcuni problemi noti relativi al programma di installazione di Visual Studio che Microsoft sta cercando di risolvere. Controllare se il problema è già stato risolto o trovare soluzioni alternative nella [sezione Problemi noti delle note sulla versione.](/visualstudio/releases/2022/release-notes-preview#-known-issues)

::: moniker-end

### <a name="step-2---try-repairing-visual-studio"></a>Passaggio 2- Provare a ripristinare Visual Studio

La correzione corregge molti problemi comuni relativi all'aggiornamento. Per altre informazioni su quando e come ripristinare Visual Studio, vedere [Ripristinare Visual Studio](repair-visual-studio.md).

### <a name="step-3---check-with-the-developer-community"></a>Passaggio 3: Rivolgersi alla community degli sviluppatori

Cercare il messaggio di errore nel [canale Visual Studio Developer Community.](https://aka.ms/feedback/suggest?space=8) Altri membri della community potrebbero aver trovato una soluzione o una soluzione alternativa per il problema.

### <a name="step-4---delete-the-visual-studio-installer-folder-to-fix-upgrade-problems"></a>Passaggio 4 - Eliminare la cartella Programma di installazione di Visual Studio per risolvere i problemi di aggiornamento

Il Programma di installazione di Visual Studio bootstrap è un eseguibile leggero che avvia l'installazione del Programma di installazione di Visual Studio. L'eliminazione Programma di installazione di Visual Studio file e quindi la rieseguizione del programma di avvio automatico risolve alcuni errori di aggiornamento.

> [!NOTE]
> Eseguendo le azioni seguenti vengono reinstallati i file del programma di installazione di Visual Studio e vengono reimpostati i metadati di installazione.

::: moniker range="vs-2017"

1. Chiudere il programma di installazione di Visual Studio.
1. Eliminare la directory Programma di installazione di Visual Studio di installazione. In genere, la directory è `C:\Program Files (x86)\Microsoft Visual Studio\Installer`.
1. Eseguire il programma di bootstrap dell'installazione di Visual Studio. Il programma di bootstrap è disponibile nella cartella Download con un nome file che segue il modello `vs_[Visual Studio edition]__*.exe`. Se l'applicazione non è stata individuata, è possibile scaricare il programma di avvio automatico dalla pagina dei download di [Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) e facendo clic su **Scarica** per l'edizione di Visual Studio. Eseguire il file eseguibile per reimpostare i metadati di installazione.
1. Provare di nuovo a installare o ad aggiornare Visual Studio. Se i problemi di installazione persistono, andare al passaggio successivo.

::: moniker-end

::: moniker range="vs-2019"

1. Chiudere il programma di installazione di Visual Studio.
1. Eliminare la directory del programma di installazione di Visual Studio. In genere, la directory è `C:\Program Files (x86)\Microsoft Visual Studio\Installer`.
1. Eseguire il programma di bootstrap dell'installazione di Visual Studio. È possibile trovare il programma di avvio automatico nella cartella Download con un nome file che corrisponde a un `vs_[Visual Studio edition]__*.exe` modello. Se l'applicazione non è stata individuata, è possibile scaricare il programma di avvio automatico dalla pagina dei download di [Visual Studio](https://visualstudio.microsoft.com/downloads) e facendo clic su **Scarica** per l'edizione di Visual Studio. Eseguire il file eseguibile per reimpostare i metadati di installazione.
1. Provare di nuovo a installare o ad aggiornare Visual Studio. Se i problemi di installazione persistono, andare al passaggio successivo.

::: moniker-end

::: moniker range=">=vs-2022"

1. Chiudere il programma di installazione di Visual Studio.
1. Eliminare la Programma di installazione di Visual Studio cartella. In genere, il percorso della cartella è `C:\Program Files (x86)\Microsoft Visual Studio\Installer` .
1. Eseguire il programma di bootstrap dell'installazione di Visual Studio. È possibile trovare il programma di avvio automatico **nella cartella Download** con un nome file che corrisponde a un `vs_[Visual Studio edition]__*.exe` modello. In caso contrario, è possibile scaricare il programma di avvio automatico per l'edizione Visual Studio dalla [pagina Visual Studio download.](https://visualstudio.microsoft.com/downloads) Eseguire il file eseguibile per reimpostare i metadati di installazione.
1. Provare di nuovo a installare o ad aggiornare Visual Studio. Se il Programma di installazione di Visual Studio continua a non riuscire, procedere con il passaggio [Segnalare un](#step-5---report-a-problem) problema.

::: moniker-end

### <a name="step-5---report-a-problem"></a>Passaggio 5: Segnalare un problema

In alcune situazioni, ad esempio quando sono presenti file danneggiati, i problemi potrebbero richiedere la risoluzione dei problemi caso per caso. Per assistenza, seguire questa procedura:

::: moniker range="vs-2017"

1. Raccogliere i log di installazione. Per altre informazioni, vedere [Come ottenere i log di installazione di Visual Studio](#installation-logs).
1. Aprire il programma di installazione di Visual Studio e quindi fare clic su **Segnala un problema** per aprire Visual Studio Feedback Tool.
![Screenshot che mostra il pulsante Commenti e suggerimenti nella Programma di installazione di Visual Studio.](media/report-a-problem.png)
1. Specificare un titolo per la segnalazione del problema e fornire i relativi dettagli. Fare clic su **Avanti** per accedere alla sezione **Allegati** e quindi allegare il file di log generato. In genere, il file è disponibile in `%TEMP%\vslogs.zip`.
1. Fare **clic su** Avanti per esaminare la segnalazione del problema e quindi fare clic su **Invia.**

::: moniker-end

::: moniker range="vs-2019"

1. Raccogliere i log di installazione. Per altre informazioni, vedere [Come ottenere i log di installazione di Visual Studio](#installation-logs).
1. Aprire il programma di installazione di Visual Studio e quindi fare clic su **Segnala un problema** per aprire Visual Studio Feedback Tool.
![Screenshot che mostra il pulsante Commenti e suggerimenti nella Programma di installazione di Visual Studio.](media/vs-2019/vs-installer-report-problem.png)
1. Specificare un titolo per la segnalazione del problema e fornire i relativi dettagli. Fare clic su **Avanti** per accedere alla sezione **Allegati** e quindi allegare il file di log generato. In genere, il file è disponibile in `%TEMP%\vslogs.zip`.
1. Fare clic su **Avanti** per controllare la segnalazione del problema e quindi fare clic su **Invia**.

::: moniker-end

::: moniker range=">=vs-2022"

1. Raccogliere i log di installazione. Per altre informazioni, vedere [Come ottenere i log di installazione di Visual Studio](#installation-logs).
1. Aprire il Programma di installazione di Visual Studio e quindi scegliere Segnala un **problema** per aprire lo strumento Visual Studio Commenti e suggerimenti.
![Screenshot che mostra il pulsante Commenti e suggerimenti nella Programma di installazione di Visual Studio.](media/vs-2022/vs-installer-report-problem.png)
1. Assegnare un titolo alla segnalazione del problema e specificare i dettagli pertinenti. Il log di installazione più recente per il Programma di installazione di Visual Studio viene aggiunto automaticamente alla **sezione Allegati** aggiuntivi della segnalazione del problema.
1. Scegliere **Invia**.

::: moniker-end

### <a name="step-6---remove-visual-studio-installation-files"></a>Passaggio 6: Rimuovere i Visual Studio di installazione

Come ultima risorsa, è possibile rimuovere tutti i file Visual Studio di installazione e le informazioni sul prodotto:

1. Seguire i passaggi nella [pagina Rimuovi Visual Studio.](remove-visual-studio.md)
1. Eseguire nuovamente il programma Programma di installazione di Visual Studio bootstrap. È possibile trovare il programma di avvio automatico **nella cartella Download** con un nome file che corrisponde a un `vs_[Visual Studio edition]__*.exe` modello. In caso contrario, è possibile scaricare il programma di avvio automatico per l'edizione Visual Studio dalla [pagina Visual Studio download.](https://visualstudio.microsoft.com/downloads)
1. Provare a reinstallare Visual Studio.

### <a name="step-7---contact-us-optional"></a>Passaggio 7 - Contattaci (facoltativo)

Se le procedure indicate sopra non consentono di installare o aggiornare correttamente Visual Studio, è possibile contattare il supporto tecnico tramite l'opzione di supporto [**Chat attiva**](https://visualstudio.microsoft.com/vs/support/#talktous) (solo in lingua inglese) per ottenere ulteriore assistenza.

## <a name="offline-installations"></a>Installazioni offline

Di seguito sono riportati alcuni problemi noti e soluzioni alternative che possono risultare utili quando si crea [un'installazione offline](create-an-offline-installation-of-visual-studio.md) e si esegue l'installazione da un layout locale.

| Problema       | Soluzione |
| ----------- | -------- |
| Gli utenti non possono accedere ai file | Assicurarsi di modificare le autorizzazioni (ACL) in modo che concedino l'accesso **in** lettura ad altri utenti *prima* di condividere l'installazione offline. |
| Non è possibile installare nuovi carichi di lavoro, componenti o Language Pack | Assicurarsi di avere accesso a Internet se si installa da un layout parziale e se si selezionano carichi di lavoro, componenti o lingue che non sono stati scaricati in precedenza per tale layout parziale. |

Per risolvere i problemi relativi a [un'installazione di](create-a-network-installation-of-visual-studio.md)rete, vedere [Risolvere gli errori correlati](troubleshooting-network-related-errors-in-visual-studio.md)alla rete quando si installa o si usa Visual Studio .

## <a name="installation-logs"></a>Log di installazione

I log di installazione consentono di risolvere la maggior parte dei problemi di installazione. Quando si invia un [](../ide/how-to-report-a-problem-with-visual-studio.md) problema usando Segnala un problema nel Programma di installazione di Visual Studio, il log di installazione più recente per il Programma di installazione di Visual Studio viene aggiunto automaticamente al report.

Se si contatta Supporto tecnico Microsoft, potrebbe essere richiesto di raccogliere i log di installazione usando lo strumento di Microsoft Visual Studio e .NET Framework [raccolta dei log.](https://www.microsoft.com/download/details.aspx?id=12493) Lo strumento di raccolta dei log raccoglie i log di installazione da tutti i componenti installati da Visual Studio, tra cui .NET Framework, Windows SDK e SQL Server. Raccoglie inoltre informazioni sul computer, un inventario del programma di installazione di Windows e informazioni del registro eventi Windows per Programma di installazione di Visual Studio, Windows Installer e Ripristino configurazione di sistema.

Per raccogliere i log:

1. [Scaricare lo strumento](https://www.microsoft.com/download/details.aspx?id=12493).
1. Aprire un prompt dei comandi amministrativo.
1. Eseguire `Collect.exe` nella cartella in cui è stato salvato lo strumento.
1. Lo strumento genera un `vslogs.zip` file nella cartella , in genere in `%TEMP%` `C:\Users\YourName\AppData\Local\Temp\vslogs.zip` .

> [!NOTE]
> Lo strumento deve essere eseguito usando lo stesso account utente con cui è stata eseguita l'installazione che ha avuto esito negativo. Se si esegue lo strumento da un account utente diverso, impostare l'opzione `–user:<name>` in modo da specificare l'account utente con cui è stata eseguita l'installazione che ha avuto esito negativo. Per altre informazioni sull'utilizzo e sulle opzioni disponibili, eseguire `Collect.exe -?` da un prompt dei comandi amministrativo.

## <a name="live-help"></a>Guida in tempo reale

Se le soluzioni elencate in questa guida alla risoluzione dei problemi non consentono di installare o aggiornare correttamente Visual Studio, usare l'opzione di supporto [**live chat**](https://visualstudio.microsoft.com/vs/support/#talktous) (solo in lingua inglese) per ulteriore assistenza.

## <a name="see-also"></a>Vedi anche

* [Ripristinare Visual Studio](repair-visual-studio.md)
* [Remove Visual Studio ](remove-visual-studio.md) (Rimuovere Visual Studio)
* [Installare e usare Visual Studio e i servizi di Azure protetti da un firewall o un server proxy](install-and-use-visual-studio-behind-a-firewall-or-proxy-server.md)
* [Strumenti per il rilevamento e la gestione di istanze di Visual Studio](tools-for-managing-visual-studio-instances.md)
* [Guida di Visual Studio Administrator](visual-studio-administrator-guide.md)
