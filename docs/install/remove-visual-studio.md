---
title: Rimuovere Visual Studio
titleSuffix: ''
description: Informazioni dettagliate su come rimuovere completamente Visual Studio dal computer.
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
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: fec652e0089a8baae79b6fa9446249710ea2f40d
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/01/2020
ms.locfileid: "75594513"
---
# <a name="remove-visual-studio"></a>Rimuovere Visual Studio

Se si verifica un errore irreversibile e non è possibile ripristinare o disinstallare Visual Studio, è possibile eseguire lo strumento `InstallCleanup.exe` per rimuovere i file di installazione e le informazioni sul prodotto per tutte le istanze installate di Visual Studio 2017 o Visual Studio 2019.

> [!WARNING]
> Usare lo strumento InstallCleanup **solo come ultima risorsa** se il ripristino o la disinstallazione ha esito negativo. Questo strumento potrebbe disinstallare le funzionalità di altre installazioni di Visual Studio o altri prodotti, che potrebbero anche dover essere ripristinati o reinstallati.

## <a name="run-installcleanupexe"></a>Eseguire InstallCleanup. exe

Con lo strumento `InstallCleanup.exe` è possibile utilizzare una delle opzioni della riga di comando seguenti:

| Opzione | Comportamento di |
| ------ | -------- |
| `-i`   | Questa opzione è l'impostazione predefinita se non viene passata nessun'altra opzione. Rimuove solo la directory di installazione principale e le informazioni sul prodotto. Usare questa opzione se si prevede di reinstallare la stessa versione di Visual Studio dopo aver eseguito lo strumento `InstallCleanup.exe`. |
| `-f`   | Questa opzione rimuove la directory di installazione principale, le informazioni sul prodotto e la maggior parte delle altre funzionalità installate all'esterno della directory di installazione, che potrebbero anche essere condivise con altre installazioni di Visual Studio o altri prodotti. Usare questa opzione se si intende rimuovere Visual Studio senza reinstallarlo in un secondo momento. |

Ecco come eseguire lo strumento di `InstallCleanup.exe`:

1. Chiudere il programma di installazione di Visual Studio.
1. Aprire un prompt dei comandi dell'amministratore. Per aprire un prompt dei comandi dell'amministratore, seguire questa procedura:
   * Digitare **cmd** nella casella "Digitare qui il testo di ricerca".
   * Fare clic con il pulsante destro del mouse su **Prompt dei comandi** e quindi scegliere **Esegui come amministratore**.
1. Immettere il percorso completo dello strumento `InstallCleanup.exe` e aggiungere l'opzione della riga di comando che si preferisce. Per impostazione predefinita, il percorso dello strumento è il seguente:

   ```
   C:\Program Files (x86)\Microsoft Visual Studio\Installer\resources\app\layout\InstallCleanup.exe
   ```

   > [!NOTE]
   > Se non si riesce a trovare `InstallCleanup.exe` nella directory Programma di installazione di Visual Studio, che si trova sempre in `%ProgramFiles(x86)%\Microsoft Visual Studio`, ecco cosa fare successivamente. Seguire le istruzioni per [installare Visual Studio](install-visual-studio.md). Quindi, quando viene visualizzata la schermata di selezione del carico di lavoro, chiudere la finestra e seguire di nuovo la procedura riportata in questa pagina.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Vedere anche

* [Install Visual Studio](install-visual-studio.md) (Installare Visual Studio)
* [Aggiornare Visual Studio](update-visual-studio.md)
* [Modificare Visual Studio](modify-visual-studio.md)
* [Disinstallare Visual Studio](uninstall-visual-studio.md)
