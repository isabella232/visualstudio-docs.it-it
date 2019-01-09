---
title: Rimuovere Visual Studio
titleSuffix: ''
description: Informazioni sulla procedura dettagliata di rimozione completa di Visual Studio dal computer in uso.
ms.date: 09/12/2017
ms.custom: seodec18
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
ms.openlocfilehash: 26d29ccf0bfa834ec7581fea11a606ce0558cf74
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53985667"
---
# <a name="remove-visual-studio-2017"></a>Rimuovere Visual Studio 2017

Se si verifica un errore irreversibile e non è possibile ripristinare o disinstallare Visual Studio, è possibile eseguire lo strumento `InstallCleanup.exe` per rimuovere i file di installazione e le informazioni sul prodotto per tutte le istanze installate di Visual Studio 2017 e versioni successive. L'esecuzione di questo strumento deve essere considerata come ultima risorsa in caso di esito negativo della riparazione o della disinstallazione e potrebbe causare la disinstallazione di funzionalità da altre installazioni di Visual Studio o altri prodotti che devono essere riparati.

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

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Vedere anche

* [Installare Visual Studio 2017](install-visual-studio.md)
* [Aggiornare Visual Studio 2017](update-visual-studio.md)
* [Modificare Visual Studio 2017](modify-visual-studio.md)
* [Disinstallare Visual Studio 2017](uninstall-visual-studio.md)
