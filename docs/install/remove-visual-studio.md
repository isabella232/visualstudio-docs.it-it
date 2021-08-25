---
title: Rimuovere Visual Studio
titleSuffix: ''
description: Informazioni dettagliate su Visual Studio rimuovere completamente i dati dal computer.
ms.date: 08/24/2021
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
author: anandmeg
ms.author: meghaanand
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 4662eb0470811e3cf4047e1d51106734369ddf34
ms.sourcegitcommit: aef3e3f99e022675d339b7fe381cb37202be5be2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/24/2021
ms.locfileid: "122785728"
---
# <a name="remove-visual-studio"></a>Rimuovere Visual Studio

Se si verifica un errore irreversibile e non è possibile ripristinare o disinstallare Visual Studio, è possibile eseguire lo strumento per rimuovere i file di installazione e le informazioni sul prodotto per tutte le istanze installate di `InstallCleanup.exe` Visual Studio 2017, Visual Studio 2019 o Visual Studio 2022.

> [!WARNING]
> Usare lo strumento InstallCleanup solo **come ultima** risorsa se il ripristino o la disinstallazione non riesce. Questo strumento potrebbe disinstallare le funzionalità Visual Studio altre installazioni o altri prodotti, che potrebbe anche essere necessario ripristinare o reinstallare.

## <a name="run-installcleanupexe"></a>Eseguire InstallCleanup.exe

Con lo strumento è possibile usare una delle opzioni della riga di `InstallCleanup.exe` comando seguenti:

| Commutatore | Comportamento |
|-----------------|--------------------|
|  `-i [version]`   | Questa opzione è l'impostazione predefinita se non viene passata nessun'altra opzione. Rimuove solo la directory di installazione principale e le informazioni sul prodotto. Usare questa opzione se si intende reinstallare la stessa versione di Visual Studio dopo l'esecuzione dello `InstallCleanup.exe` strumento. Se viene specificato un valore , verranno rimossi solo i prodotti con una versione che inizia con `[version]` questo valore stringa. |
|   `-f`           | Questa opzione rimuove la directory di installazione principale, le informazioni sul prodotto e la maggior parte delle altre funzionalità installate all'esterno della directory di installazione, che potrebbero essere condivise anche con altre installazioni di Visual Studio o altri prodotti. Usare questa opzione se si prevede di rimuovere Visual Studio senza reinstallarla in un secondo momento. |

Ecco come eseguire lo `InstallCleanup.exe` strumento:

1. Chiudere il programma di installazione di Visual Studio.
1. Aprire un prompt dei comandi dell'amministratore. Per aprire un prompt dei comandi dell'amministratore, seguire questa procedura:
   * Digitare **cmd** nella casella "Digitare qui il testo di ricerca".
   * Fare clic con il pulsante destro del mouse su **Prompt dei comandi** e quindi scegliere **Esegui come amministratore**.
1. Immettere il percorso completo dello strumento `InstallCleanup.exe` e aggiungere l'opzione della riga di comando preferita. Per impostazione predefinita, il percorso dello strumento è il seguente. Le virgolette doppie racchiudno un comando contenente spazi:

   ```shell
   "C:\Program Files (x86)\Microsoft Visual Studio\Installer\InstallCleanup.exe"
   ```

   > [!NOTE]
   > Se non è possibile trovare nella directory Programma di installazione di Visual Studio, che si trova sempre in , ecco `InstallCleanup.exe` `%ProgramFiles(x86)%\Microsoft Visual Studio` cosa fare. Seguire le istruzioni per [installare Visual Studio](install-visual-studio.md). Quindi, quando viene visualizzata la schermata di selezione del carico di lavoro, chiudere la finestra e seguire di nuovo i passaggi in questa pagina.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Vedi anche

* [Installa Visual Studio](install-visual-studio.md)
* [Aggiornare Visual Studio](update-visual-studio.md)
* [Modificare Visual Studio](modify-visual-studio.md)
* [Disinstallare Visual Studio](uninstall-visual-studio.md)
