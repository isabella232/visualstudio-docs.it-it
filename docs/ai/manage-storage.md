---
title: Esplorare lo spazio di archiviazione per caricare dati
description: Informazioni su come esplorare tutte le risorse di archiviazione nel computer remoto o nella condivisione file di Azure per abilitare il caricamento di dati o il download di modelli e log.
ms.custom: SEO-VS-2020
author: jillre
ms.author: jillfra
manager: jmartens
ms.technology: vs-ai-tools
monikerRange: vs-2017
ms.date: 11/13/2017
ms.topic: how-to
ms.workload:
- multiple
ms.openlocfilehash: 1b0e7098519374a41042f02f8ac8cba4b9071b15
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122053370"
---
# <a name="browse-storage-to-upload-data-or-download-models-and-logs"></a>Esplorare lo spazio di archiviazione per caricare dati o per scaricare modelli e log

È possibile esplorare tutto lo spazio di archiviazione nel computer remoto o in una condivisione file di Azure per abilitare il caricamento dei dati o il download di modelli e log. È anche possibile usare il browser processi per accedere ai log e all'output per un processo specifico.

## <a name="to-access-all-data-on-the-remote-machine-or-file-share"></a>Per accedere a tutti i dati nel computer remoto o nella condivisione file

1. Aprire il **Esplora server**.
2. Espandere il contesto di calcolo del computer remoto o di Batch per intelligenza artificiale.
3. Fare clic con il pulsante destro del mouse su **Archiviazione** e quindi scegliere **Sfoglia**.

    ![Screenshot della Esplora server con la cartella Computer remoti espansa. Archiviazione è evidenziato nell'albero delle cartelle e l'opzione Sfoglia è selezionata nel menu di scelta rapida.](media/manage-storage/browse-storage.png)

## <a name="to-access-job-specific-data-on-the-remote-machine-or-file-share"></a>Per accedere ai dati specifici di un processo nel computer remoto o nella condivisione file

1. Aprire [Cronologia processi](job-details.md)
2. Selezionare il processo.
3. Fare **clic su Cartella di** lavoro o su **StdOut/Stderr** per accedere rapidamente a questi importanti file di log.

    ![Screenshot della finestra Browser processi in Esplora server. Il train_mnist processo è selezionato e il collegamento Cartella di lavoro è selezionato in Dettagli processo.](media/manage-storage/job-workingfolder.png)
