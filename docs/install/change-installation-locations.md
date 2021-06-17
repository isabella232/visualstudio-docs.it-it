---
title: Selezionare i percorsi di installazione
description: Informazioni su come ridurre lo spazio occupato dall'installazione di Visual Studio nell'unità di sistema indicando un percorso in unità diverse per Download Cache, componenti condivisi, SDK e strumenti. Ad esempio, spostare alcuni file dall'unità C all'unità D.
ms.date: 03/30/2019
ms.custom: acquisition
ms.topic: how-to
helpviewer_keywords:
- change installation locations for Visual Studio
- select an installation location for Visual Studio files
- move installation files to different drives
- use the D drive
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 9e9ee5972a0f1acba37a6b6b417df00a925e5558
ms.sourcegitcommit: 1f27f33852112702ee35fbc0c02fba37899e4cf5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/15/2021
ms.locfileid: "112112488"
---
# <a name="select-the-installation-locations-in-visual-studio"></a>Selezionare i percorsi di installazione in Visual Studio

::: moniker range="vs-2019"

è possibile ridurre lo spazio occupato dall'installazione di Visual Studio nell'unità di sistema cambiando il percorso di alcuni file. In particolare è possibile usare un percorso diverso per la Download Cache, i componenti condivisi, i SDK e file degli strumenti.

::: moniker-end

::: moniker range="vs-2017"

**Novità della versione 15.7:** è possibile ridurre il footprint di installazione di Visual Studio nell'unità di sistema modificando il percorso di alcuni dei relativi file. In particolare è possibile usare un percorso diverso per la Download Cache, i componenti condivisi, i SDK e file degli strumenti.

::: moniker-end

   > [!NOTE]
   > Esistono alcuni strumenti e SDK con regole diverse riguardo al percorso di installazione. Questi strumenti e SDK vengono installati nell'unità di sistema anche se si sceglie un altro percorso.

Pronto per iniziare? Ecco come.

::: moniker range="vs-2017"

1. Quando si installa Visual Studio scegliere la scheda **Percorsi di installazione**.

   ![Visual Studio 2017: selezionare il percorso di installazione](media/vs-installation-locations.png "Selezionare il percorso di installazione.")

1. Nella sezione **IDE di Visual Studio** accettare il valore predefinito. Viene installato il prodotto principale e vengono inclusi file specifici per questa versione di Visual Studio.

   ![Visual Studio IDE della scheda Percorsi di installazione](media/vs-installation-locations-ide.png "Accettare il valore predefinito per la Visual Studio IDE della scheda Percorso installazioni.")

   > [!TIP]
   > Se l'unità di sistema è un'unità SSD è consigliabile accettare il percorso predefinito nell'unità di sistema. Motivo: quando si sviluppa con Visual Studio, si eseguono operazioni di lettura e scrittura in numerosi file, aumentando così le attività di input/output del disco. È opportuno scegliere l'unità più veloce per gestire il carico.

1. Nella sezione **Download Cache** decidere se si vuole mantenere la Download Cache e quindi scegliere dove archiviare i file corrispondenti.

     ![Sezione Download Cache della scheda Percorsi di installazione](media/vs-installation-locations-cache.png "Scegliere se mantenere la cache di download dopo l'installazione e quindi specificare l'unità in cui archiviare i file.")

    1. Selezionare o deselezionare **Mantieni la Download Cache dopo l'installazione**.

       Se si decide di non mantenere la Download Cache, il percorso viene usato solo temporaneamente. Questa azione non ha effetto sui file di installazioni precedenti né li elimina.

    1. Specificare l'unità in cui verranno archiviati i file di installazione e i manifesti dalla Download Cache.

        Ad esempio, se si seleziona il carico di lavoro "Sviluppo di applicazioni desktop con C++", le dimensioni richieste temporaneamente sono 1,58 GB nell'unità di sistema, spazio che verrà liberato non appena viene completata l'installazione.

       > [!IMPORTANT]
       > Il percorso viene impostato con la prima installazione e non può essere modificato in un secondo tempo dall'interfaccia utente del programma di installazione. È invece necessario usare [i parametri della riga di comando](use-command-line-parameters-to-install-visual-studio.md) per spostare la cache di download.

1. Nella sezione **Componenti condivisi, strumenti e SDK** specificare l'unità in cui si vogliono archiviare i file condivisi dalle installazioni side-by-side di Visual Studio. Anche i SDK e gli strumenti vengono archiviati in questa directory.

   ![Sezione Componenti condivisi, strumenti e SDK della scheda Percorsi di installazione](media/vs-installation-locations-shared.png "Specificare il percorso in cui archiviare componenti condivisi, strumenti e SDK.")

::: moniker-end

::: moniker range="vs-2019"

1. Quando si installa Visual Studio scegliere la scheda **Percorsi di installazione**.

   ![Visual Studio 2019: selezionare il percorso di installazione](media/vs-2019/vs-installer-installation-locations.png "Selezionare il percorso di installazione.")

1. Nella sezione **IDE di Visual Studio** accettare il valore predefinito. Viene installato il prodotto principale e vengono inclusi file specifici per questa versione di Visual Studio.

   > [!TIP]
   > Se l'unità di sistema è un'unità SSD è consigliabile accettare il percorso predefinito nell'unità di sistema. Motivo: quando si sviluppa con Visual Studio, si eseguono operazioni di lettura e scrittura in numerosi file, aumentando così le attività di input/output del disco. È opportuno scegliere l'unità più veloce per gestire il carico.

1. Nella sezione **Download Cache** decidere se si vuole mantenere la Download Cache e quindi scegliere dove archiviare i file corrispondenti.

    * Selezionare o deselezionare **Mantieni la Download Cache dopo l'installazione**.

       Se si decide di non mantenere la Download Cache, il percorso viene usato solo temporaneamente. Questa azione non ha effetto sui file di installazioni precedenti né li elimina.

    * Specificare l'unità in cui verranno archiviati i file di installazione e i manifesti dalla Download Cache.

        Ad esempio, se si seleziona il carico di lavoro "Sviluppo di applicazioni desktop con C++", le dimensioni richieste temporaneamente sono 1,58 GB nell'unità di sistema, spazio che verrà liberato non appena viene completata l'installazione.

       > [!IMPORTANT]
       > Il percorso viene impostato con la prima installazione e non può essere modificato in un secondo tempo dall'interfaccia utente del programma di installazione. È invece necessario usare [i parametri della riga di comando](use-command-line-parameters-to-install-visual-studio.md) per spostare la cache di download.

1. Nella sezione **Componenti condivisi, strumenti e SDK** viene usata la stessa unità scelta nella sezione "Download cache". La directory \Microsoft\VisualStudio\Condiviso archivia i file condivisi dalle installazioni side-by-side di Visual Studio. Anche i SDK e gli strumenti vengono archiviati in questa directory.

::: moniker-end

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Vedi anche

* [Installa Visual Studio](install-visual-studio.md)
* [Aggiornare Visual Studio](update-visual-studio.md)
* [Modificare Visual Studio](update-visual-studio.md)
* [Disinstallare Visual Studio](uninstall-visual-studio.md)
