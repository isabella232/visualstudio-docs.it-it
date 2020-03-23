---
title: Rimuovere Visual Studio
titleSuffix: ''
description: Informazioni su come rimuovere completamente Visual Studio dal computer, passo dopo passo.
ms.date: 12/19/2019
ms.custom: seodec18
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
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: b0e8c8fe10451e9e5906eabf7f4f65086d147904
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/18/2020
ms.locfileid: "76113715"
---
# <a name="remove-visual-studio"></a>Rimuovere Visual Studio

Se si verifica un errore irreversibile e non è possibile ripristinare o `InstallCleanup.exe` disinstallare Visual Studio, è possibile eseguire lo strumento per rimuovere i file di installazione e le informazioni sul prodotto per tutte le istanze installate di Visual Studio 2017 o Visual Studio 2019.

> [!WARNING]
> Utilizzare lo strumento InstallCleanup **solo come ultima risorsa** se il ripristino o la disinstallazione non riescono. Questo strumento potrebbe disinstallare funzionalità da altre installazioni di Visual Studio o altri prodotti, che quindi potrebbe essere necessario ripristinare o reinstallare.

## <a name="run-installcleanupexe"></a>Eseguire InstallCleanup.exe

Con lo `InstallCleanup.exe` strumento è possibile utilizzare una delle seguenti opzioni della riga di comando:

| Opzione | Comportamento |
| ------ | -------- |
| `-i`   | Questa opzione è l'impostazione predefinita se non viene passata altre opzioni. Rimuove solo la directory di installazione principale e le informazioni sul prodotto. Utilizzare questa opzione se si intende reinstallare la stessa `InstallCleanup.exe` versione di Visual Studio dopo aver eseguito lo strumento. |
| `-f`   | Questa opzione rimuove la directory di installazione principale, le informazioni sui prodotti e la maggior parte delle altre funzionalità installate all'esterno della directory di installazione, che potrebbero essere condivise anche con altre installazioni di Visual Studio o altri prodotti. Utilizzare questa opzione se si intende rimuovere Visual Studio senza reinstallarlo in un secondo momento. |

Ecco come eseguire lo `InstallCleanup.exe` strumento:

1. Chiudere il programma di installazione di Visual Studio.
1. Aprire un prompt dei comandi dell'amministratore. Per aprire un prompt dei comandi dell'amministratore, seguire questa procedura:
   * Digitare **cmd** nella casella "Digitare qui il testo di ricerca".
   * Fare clic con il pulsante destro del mouse su **Prompt dei comandi** e quindi scegliere **Esegui come amministratore**.
1. Immettere il percorso `InstallCleanup.exe` completo dello strumento e aggiungere l'opzione della riga di comando preferita. Per impostazione predefinita, il percorso dello strumento è il seguente:

   ```
   C:\Program Files (x86)\Microsoft Visual Studio\Installer\resources\app\layout\InstallCleanup.exe
   ```

   > [!NOTE]
   > Se non riesci `InstallCleanup.exe` a trovare nella directory del programma `%ProgramFiles(x86)%\Microsoft Visual Studio`di installazione di Visual Studio, che si trova sempre in , ecco cosa fare dopo. Seguire le istruzioni per [installare Visual Studio](install-visual-studio.md). Quindi, quando viene visualizzata la schermata di selezione del carico di lavoro, chiudere la finestra e seguire nuovamente i passaggi in questa pagina.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Vedere anche

* [Installare Visual Studio](install-visual-studio.md)
* [Aggiornare Visual Studio](update-visual-studio.md)
* [Modificare Visual Studio](modify-visual-studio.md)
* [Disinstallare Visual Studio](uninstall-visual-studio.md)
