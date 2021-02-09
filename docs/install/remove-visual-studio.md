---
title: Rimuovere Visual Studio
titleSuffix: ''
description: Informazioni dettagliate su come rimuovere completamente Visual Studio dal computer.
ms.date: 12/19/2019
ms.custom: seodec18
ms.topic: how-to
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
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 751f87075d4e9dcbb7daa94f39a2f38c5083fb3c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99878448"
---
# <a name="remove-visual-studio"></a>Rimuovere Visual Studio

Se si verifica un errore irreversibile e non è possibile ripristinare o disinstallare Visual Studio, è possibile eseguire lo `InstallCleanup.exe` strumento per rimuovere i file di installazione e le informazioni sul prodotto per tutte le istanze installate di Visual studio 2017 o Visual studio 2019.

> [!WARNING]
> Usare lo strumento InstallCleanup **solo come ultima risorsa** se il ripristino o la disinstallazione ha esito negativo. Questo strumento potrebbe disinstallare le funzionalità di altre installazioni di Visual Studio o altri prodotti, che potrebbero anche dover essere ripristinati o reinstallati.

## <a name="run-installcleanupexe"></a>Esegui InstallCleanup.exe

Con lo strumento è possibile usare una delle opzioni della riga di comando seguenti `InstallCleanup.exe` :

| Opzione | Comportamento |
| ------ | -------- |
| `-i`   | Questa opzione è l'impostazione predefinita se non viene passata nessun'altra opzione. Rimuove solo la directory di installazione principale e le informazioni sul prodotto. Usare questa opzione se si prevede di reinstallare la stessa versione di Visual Studio dopo aver eseguito lo `InstallCleanup.exe` strumento. |
| `-f`   | Questa opzione rimuove la directory di installazione principale, le informazioni sul prodotto e la maggior parte delle altre funzionalità installate all'esterno della directory di installazione, che potrebbero anche essere condivise con altre installazioni di Visual Studio o altri prodotti. Usare questa opzione se si intende rimuovere Visual Studio senza reinstallarlo in un secondo momento. |

Ecco come eseguire lo `InstallCleanup.exe` strumento:

1. Chiudere il programma di installazione di Visual Studio.
1. Aprire un prompt dei comandi dell'amministratore. Per aprire un prompt dei comandi dell'amministratore, seguire questa procedura:
   * Digitare **cmd** nella casella "Digitare qui il testo di ricerca".
   * Fare clic con il pulsante destro del mouse su **Prompt dei comandi** e quindi scegliere **Esegui come amministratore**.
1. Immettere il percorso completo dello `InstallCleanup.exe` strumento e aggiungere l'opzione della riga di comando che si preferisce. Per impostazione predefinita, il percorso dello strumento è il seguente. Le virgolette doppie racchiudono un comando contenente spazi:

   ```
   "C:\Program Files (x86)\Microsoft Visual Studio\Installer\resources\app\layout\InstallCleanup.exe"
   ```

   > [!NOTE]
   > Se non è possibile trovare `InstallCleanup.exe` nella directory programma di installazione di Visual Studio, che si trova sempre in `%ProgramFiles(x86)%\Microsoft Visual Studio` , ecco cosa fare successivamente. Seguire le istruzioni per [installare Visual Studio](install-visual-studio.md). Quindi, quando viene visualizzata la schermata di selezione del carico di lavoro, chiudere la finestra e seguire di nuovo la procedura riportata in questa pagina.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Vedi anche

* [Installa Visual Studio](install-visual-studio.md)
* [Aggiornare Visual Studio](update-visual-studio.md)
* [Modificare Visual Studio](modify-visual-studio.md)
* [Disinstallare Visual Studio](uninstall-visual-studio.md)
