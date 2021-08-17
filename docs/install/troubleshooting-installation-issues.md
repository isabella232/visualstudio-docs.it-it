---
title: Risoluzione dei problemi di installazione o di aggiornamento
description: Non sempre tutto funziona correttamente. Se l'installazione o l'aggiornamento di Visual Studio ha esito negativo, questa pagina può risultare utile.
ms.date: 06/24/2020
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
ms.openlocfilehash: 75952c2fc827b5a4e37339e99615ae0447b916c9ac64d21718c59c147456197b
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121356661"
---
# <a name="troubleshoot-visual-studio-installation-and-upgrade-issues"></a>Risolvere i problemi di installazione e aggiornamento di Visual Studio

> [!IMPORTANT]
> Se si è verificato un problema di installazione, è possibile chiedere assistenza. È disponibile [**un'opzione di supporto**](https://visualstudio.microsoft.com/vs/support/#talktous) per chat di installazione (solo in lingua inglese).

Questa Guida alla risoluzione dei problemi include istruzioni dettagliate per risolvere la maggior parte dei problemi di installazione.

## <a name="online-installations"></a>Installazioni online

La procedura seguente è ottimizzata per un'installazione online tipica. Per un problema relativo a un'installazione offline, vedere [Come risolvere i problemi di un'installazione offline](#offline-installations).

### <a name="step-1---check-whether-this-problem-is-a-known-issue"></a>Passaggio 1: Verificare se il problema è noto

::: moniker range="vs-2017"

Esistono alcuni problemi noti relativi al programma di installazione di Visual Studio che Microsoft sta cercando di risolvere. Per scoprire se esiste una soluzione alternativa al problema, vedere la [sezione Problemi noti delle note sulla versione](/visualstudio/releasenotes/vs2017-relnotes#-known-issues).

::: moniker-end

::: moniker range=">=vs-2019"

Esistono alcuni problemi noti relativi al programma di installazione di Visual Studio che Microsoft sta cercando di risolvere. Per scoprire se esiste una soluzione alternativa al problema, vedere la [sezione Problemi noti delle note sulla versione](/visualstudio/releases/2019/release-notes#-known-issues).

::: moniker-end

### <a name="step-2---try-repairing-visual-studio"></a>Passaggio 2- Provare a ripristinare Visual Studio

La correzione corregge molti problemi comuni relativi all'aggiornamento. Per altre informazioni su quando e come usare la funzionalità di ripristino in Visual Studio, vedere [Repair Visual Studio](repair-visual-studio.md).

### <a name="step-3---check-with-the-developer-community"></a>Passaggio 3: Rivolgersi alla community degli sviluppatori

Cercare il messaggio di errore nella [community degli sviluppatori di Visual Studio](https://aka.ms/feedback/suggest?space=8). È possibile che altri membri della community abbiano documentato una soluzione per il problema.

### <a name="step-4---delete-the-visual-studio-installer-directory-to-fix-upgrade-problems"></a>Passaggio 4 - Eliminare la directory Programma di installazione di Visual Studio per risolvere i problemi di aggiornamento

Il programma di bootstrap dell'installazione di Visual Studio è un file eseguibile di piccole dimensioni che consente di installare gli elementi restanti del programma di installazione di Visual Studio. Eliminando i file del programma di installazione di Visual Studio ed eseguendo nuovamente il programma di bootstrap, è possibile risolvere alcuni problemi di aggiornamento.

> [!NOTE]
> Eseguendo le azioni seguenti vengono reinstallati i file del programma di installazione di Visual Studio e vengono reimpostati i metadati di installazione.

::: moniker range="vs-2017"

1. Chiudere il programma di installazione di Visual Studio.
2. Eliminare la directory del programma di installazione di Visual Studio. In genere, la directory è `C:\Program Files (x86)\Microsoft Visual Studio\Installer`.
3. Eseguire il programma di bootstrap dell'installazione di Visual Studio. Il programma di bootstrap è disponibile nella cartella Download con un nome file che segue il modello `vs_[Visual Studio edition]__*.exe`. Se l'applicazione non è stata individuata, è possibile scaricare il programma di avvio automatico dalla pagina dei download di [Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) e facendo clic su **Scarica** per l'edizione di Visual Studio. Eseguire il file eseguibile per reimpostare i metadati di installazione.
4. Provare di nuovo a installare o ad aggiornare Visual Studio. Se i problemi di installazione persistono, andare al passaggio successivo.

::: moniker-end

::: moniker range=">=vs-2019"

1. Chiudere il programma di installazione di Visual Studio.
2. Eliminare la directory del programma di installazione di Visual Studio. In genere, la directory è `C:\Program Files (x86)\Microsoft Visual Studio\Installer`.
3. Eseguire il programma di bootstrap dell'installazione di Visual Studio. Il programma di bootstrap è disponibile nella cartella Download con un nome file che segue il modello `vs_[Visual Studio edition]__*.exe`. Se l'applicazione non è stata individuata, è possibile scaricare il programma di avvio automatico dalla pagina dei download di [Visual Studio](https://visualstudio.microsoft.com/downloads) e facendo clic su **Scarica** per l'edizione di Visual Studio. Eseguire il file eseguibile per reimpostare i metadati di installazione.
4. Provare di nuovo a installare o ad aggiornare Visual Studio. Se i problemi di installazione persistono, andare al passaggio successivo.

::: moniker-end

### <a name="step-5---report-a-problem"></a>Passaggio 5: Segnalare un problema

In alcune situazioni, ad esempio quando sono presenti file danneggiati, può essere necessario esaminare i problemi singolarmente. Per consentirci di fornire il supporto ottimale, procedere come indicato di seguito:

::: moniker range="vs-2017"

1. Raccogliere i log di installazione. Per altre informazioni, vedere [Come ottenere i log di installazione di Visual Studio](#installation-logs).
2. Aprire il programma di installazione di Visual Studio e quindi fare clic su **Segnala un problema** per aprire Visual Studio Feedback Tool.
![È possibile usare il pulsante Commenti e suggerimenti per aprire lo strumento di feedback](media/report-a-problem.png)
3. Specificare un titolo per la segnalazione del problema e fornire i relativi dettagli. Fare clic su **Avanti** per accedere alla sezione **Allegati** e quindi allegare il file di log generato. In genere, il file è disponibile in `%TEMP%\vslogs.zip`.
4. Fare clic su **Avanti** per controllare la segnalazione del problema e quindi fare clic su **Invia**.

::: moniker-end

::: moniker range=">=vs-2019"

1. Raccogliere i log di installazione. Per altre informazioni, vedere [Come ottenere i log di installazione di Visual Studio](#installation-logs).
2. Aprire il programma di installazione di Visual Studio e quindi fare clic su **Segnala un problema** per aprire Visual Studio Feedback Tool.
![È possibile usare il pulsante Commenti e suggerimenti per aprire lo strumento di feedback](media/vs-2019/vs-installer-report-problem.png)
3. Specificare un titolo per la segnalazione del problema e fornire i relativi dettagli. Fare clic su **Avanti** per accedere alla sezione **Allegati** e quindi allegare il file di log generato. In genere, il file è disponibile in `%TEMP%\vslogs.zip`.
4. Fare clic su **Avanti** per controllare la segnalazione del problema e quindi fare clic su **Invia**.

::: moniker-end

### <a name="step-6---run-installcleanupexe-to-remove-installation-files"></a>Passaggio 6- Eseguire InstallCleanup.exe per rimuovere i file di installazione

Come ultima risorsa, è possibile [rimuovere Visual Studio](remove-visual-studio.md) per eliminare tutti i file di installazione e le informazioni sul prodotto.

1. Seguire le istruzioni in [Remove Visual Studio](remove-visual-studio.md) (Rimuovere Visual Studio).
2. Eseguire di nuovo il programma di avvio automatico descritto in [Passaggio 4:](#step-4---delete-the-visual-studio-installer-directory-to-fix-upgrade-problems)Eliminare la directory Programma di installazione di Visual Studio per risolvere i problemi di aggiornamento.
3. Provare di nuovo a installare o ad aggiornare Visual Studio.

### <a name="step-7---contact-us-optional"></a>Passaggio 7 - Contattaci (facoltativo)

Se le procedure indicate sopra non consentono di installare o aggiornare correttamente Visual Studio, è possibile contattare il supporto tecnico tramite l'opzione di supporto [**Chat attiva**](https://visualstudio.microsoft.com/vs/support/#talktous) (solo in lingua inglese) per ottenere ulteriore assistenza.

## <a name="offline-installations"></a>Installazioni offline

Di seguito è riportata una tabella di problemi noti e alcune soluzioni alternative che possono risultare utili quando si crea [un'installazione offline](create-an-offline-installation-of-visual-studio.md) e quindi si esegue l'installazione da un layout locale.

| Problema       | Elemento                   | Soluzione |
| ----------- | ---------------------- | -------- |
| Gli utenti non anno accesso ai file. | Autorizzazioni (ACL) | Assicurarsi di modificare le autorizzazioni (ACL) in modo che concedino l'accesso in lettura ad altri utenti  *prima* di condividere l'installazione offline. |
| Non è possibile installare nuovi carichi di lavoro, componenti o lingue.  | `--layout`  | Assicurarsi che sia disponibile l'accesso a Internet se si esegue l'installazione da un layout parziale e si selezionano carichi di lavoro, componenti o lingue non scaricati precedentemente nel layout parziale. |

Per altre informazioni su come risolvere i problemi relativi [a](create-a-network-installation-of-visual-studio.md)un'installazione di rete, vedere Risolvere gli errori correlati alla rete quando si installa o si usa [Visual Studio](troubleshooting-network-related-errors-in-visual-studio.md).

## <a name="installation-logs"></a>Log di installazione

I log di installazione sono necessari per risolvere la maggior parte dei problemi di installazione. Quando si invia un problema mediante l'opzione [Segnala un problema](../ide/how-to-report-a-problem-with-visual-studio.md) del programma di installazione di Visual Studio, questi log vengono automaticamente inclusi nel report.

Se si contatta il supporto tecnico Microsoft, è possibile che sia necessario fornire questi log di installazione usando lo [strumento di raccolta dei log di Microsoft Visual Studio e .NET Framework](https://www.microsoft.com/download/details.aspx?id=12493). Lo strumento di raccolta dei log raccoglie i log di installazione da tutti i componenti installati da Visual Studio, tra cui .NET Framework, Windows SDK e SQL Server. Raccoglie anche informazioni sul computer, oltre a un inventario di Windows Installer e a informazioni sul registro eventi di Windows per il programma di installazione di Visual Studio, Windows Installer e Ripristino configurazione di sistema.

Per raccogliere i log:

1. [Scaricare lo strumento](https://www.microsoft.com/download/details.aspx?id=12493).
2. Aprire un prompt dei comandi amministrativo.
3. Eseguire `Collect.exe` dalla directory in cui è stato salvato lo strumento.
4. Trovare il file `vslogs.zip` risultante nella directory `%TEMP%`, ad esempio, `C:\Users\YourName\AppData\Local\Temp\vslogs.zip`.

> [!NOTE]
> Lo strumento deve essere eseguito usando lo stesso account utente con cui è stata eseguita l'installazione che ha avuto esito negativo. Se si esegue lo strumento da un account utente diverso, impostare l'opzione `–user:<name>` in modo da specificare l'account utente con cui è stata eseguita l'installazione che ha avuto esito negativo. Per altre informazioni sull'utilizzo e sulle opzioni disponibili, eseguire `Collect.exe -?` da un prompt dei comandi amministrativo.

## <a name="live-help"></a>Guida in tempo reale

Se le soluzioni fornite in questa Guida alla risoluzione dei problemi non consentono di installare o aggiornare correttamente Visual Studio, è possibile usare l'opzione di supporto [**Chat attiva**](https://visualstudio.microsoft.com/vs/support/#talktous) (solo in lingua inglese) per ottenere ulteriore assistenza.

## <a name="see-also"></a>Vedi anche

* [Ripristinare Visual Studio](repair-visual-studio.md)
* [Remove Visual Studio ](remove-visual-studio.md) (Rimuovere Visual Studio)
* [Installare e usare Visual Studio e i servizi di Azure protetti da un firewall o un server proxy](install-and-use-visual-studio-behind-a-firewall-or-proxy-server.md)
* [Strumenti per il rilevamento e la gestione di istanze di Visual Studio](tools-for-managing-visual-studio-instances.md)
* [Guida di Visual Studio Administrator](visual-studio-administrator-guide.md)
