---
title: Rimuovere Visual Studio 2017 | Microsoft Docs
description: Informazioni sulla procedura dettagliata di rimozione completa di Visual Studio dal computer in uso.
ms.custom: ''
ms.date: 09/12/2017
ms.technology: vs-acquisition
ms.prod: visual-studio-dev15
ms.topic: conceptual
f1_keywords:
- uninstall
- uninstall Visual Studio
- remove
- remove Visual Studio
- cleanup
- cleanup Visual Studio
- clean up
- clean up Visual Studio
ms.assetid: 9c81a777-9c95-4934-b517-c60c6dc78799
author: heaths
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: db775eb56a8328e3688e20ce07ce7d045c97c3c7
ms.sourcegitcommit: 4667e6ad223642bc4ac525f57281482c9894daf4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/20/2018
ms.locfileid: "36280019"
---
# <a name="remove-visual-studio"></a>Rimuovere Visual Studio

Se si verifica un errore irreversibile e non è possibile ripristinare o disinstallare Visual Studio, è possibile eseguire lo strumento `InstallCleanup.exe` per rimuovere i file di installazione e le informazioni sul prodotto. L'esecuzione di questo strumento deve essere considerata come ultima risorsa in caso di esito negativo della riparazione o della disinstallazione e potrebbe causare la disinstallazione di funzionalità da altre installazioni di Visual Studio o altri prodotti che devono essere riparati.

Nelle istruzioni seguenti, è possibile eseguire lo strumento con diverse opzioni della riga di comando con il seguente comportamento:

| Opzione | Comportamento |
| ------ | -------- |
| `-i`   | Questa opzione rappresenta l'impostazione predefinita se non vengono passate altre opzioni e consente di rimuovere solo la directory di installazione principale e le informazioni sul prodotto. Questo comportamento è preferibile se si prevede di reinstallare la stessa versione dopo aver eseguito lo strumento `InstallCleanup.exe`. |
| `-f`   | Con questa opzione vengono rimosse la directory di installazione principale, le informazioni sul prodotto e la maggior parte delle altre funzionalità installate all'esterno della directory di installazione che potrebbero essere condivise con altre installazioni di Visual Studio o altri prodotti. Questo comportamento è preferibile se si intende rimuovere Visual Studio senza reinstallarlo in un secondo momento. |

1. Chiudere il programma di installazione di Visual Studio.
2. Aprire un prompt dei comandi dell'amministratore. Per aprire un prompt dei comandi dell'amministratore, seguire questa procedura:
   * Fare clic sul menu **Start**
   * Digitare **cmd**.
   * Fare clic con il pulsante destro del mouse su **Prompt dei comandi**, quindi scegliere **Esegui come amministratore**.
3. Digitare il percorso completo dell'utilità `InstallCleanup.exe` e passare a qualsiasi opzione della riga di comando desiderata. Per impostazione predefinita, il percorso dell'utilità è il seguente:
   ```
   C:\Program Files (x86)\Microsoft Visual Studio\Installer\resources\app\layout\InstallCleanup.exe
   ```

Se non si trova `InstallCleanup.exe` nella directory del programma di installazione di Visual Studio (sempre in `%ProgramFiles(x86)%\Microsoft Visual Studio`), seguire le istruzioni per [installare Visual Studio](install-visual-studio.md) e quando viene visualizzata la schermata di selezione dei carichi di lavoro, chiudere la finestra e seguire di nuovo la procedura precedente.

## <a name="get-support"></a>Supporto

Non sempre tutto funziona correttamente. Se l'installazione di Visual Studio non riesce, vedere la pagina [Risoluzione degli errori di installazione e aggiornamento di Visual Studio 2017](troubleshooting-installation-issues.md). Se nessuna delle procedure di risoluzione dei problemi risulta utile, contattare Microsoft tramite chat in tempo reale per richiedere assistenza per l'installazione (solo in lingua inglese). Per informazioni dettagliate, vedere la [pagina del supporto di Visual Studio](https://visualstudio.microsoft.com/vs/support/#talktous).

Ecco alcune altre opzioni di supporto:

* È possibile segnalare i problemi del prodotto a Microsoft tramite lo strumento [Segnala un problema](../ide/how-to-report-a-problem-with-visual-studio-2017.md) che viene visualizzato sia nel programma di installazione di Visual Studio che nell'IDE di Visual Studio.
* È possibile condividere un suggerimento per il prodotto con Microsoft in [UserVoice](https://visualstudio.uservoice.com/forums/121579).
* È possibile visualizzare lo stato dei problemi del prodotto e trovare una risposta nella [community degli sviluppatori di Visual Studio](https://developercommunity.visualstudio.com/).
* È anche possibile comunicare con gli sviluppatori Microsoft e altri sviluppatori di Visual Studio partecipando alla [conversazione dedicata a Visual Studio nella community di Gitter](https://gitter.im/Microsoft/VisualStudio). Per questa opzione è necessario un account [GitHub](https://github.com/).

## <a name="see-also"></a>Vedere anche

* [Installare Visual Studio 2017](install-visual-studio.md)
* [Aggiornare Visual Studio 2017](update-visual-studio.md)
* [Modificare Visual Studio 2017](modify-visual-studio.md)
* [Disinstallare Visual Studio 2017](uninstall-visual-studio.md)
