---
title: Esplorare lo spazio di archiviazione per caricare dati
author: jillre
ms.author: jillfra
manager: jillfra
monikerRange: vs-2017
ms.date: 11/13/2017
ms.topic: conceptual
ms.workload:
- multiple
ms.openlocfilehash: ece3ffa3a273e903f403fd7df7005bfb54172f62
ms.sourcegitcommit: 9c1cecaff4d9955276eee7865b78d47679dd1e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/03/2020
ms.locfileid: "80638448"
---
# <a name="browse-storage-to-upload-data-or-download-models-and-logs"></a>Esplorare lo spazio di archiviazione per caricare dati o per scaricare modelli e log

È possibile esplorare tutto lo spazio di archiviazione nel computer remoto o in una condivisione file di Azure per abilitare il caricamento dei dati o il download di modelli e log. È anche possibile usare il browser processi per accedere ai log e all'output per un processo specifico.

## <a name="to-access-all-data-on-the-remote-machine-or-file-share"></a>Per accedere a tutti i dati nel computer remoto o nella condivisione file

1. Aprire **Esplora server**.
2. Espandere il contesto di calcolo del computer remoto o di Batch per intelligenza artificiale.
3. Fare clic con il pulsante destro del mouse su **Archiviazione** e quindi scegliere **Sfoglia**.

    ![storage](media/manage-storage/browse-storage.png)

## <a name="to-access-job-specific-data-on-the-remote-machine-or-file-share"></a>Per accedere ai dati specifici di un processo nel computer remoto o nella condivisione file

1. Aprire [Cronologia processi](job-details.md)
2. Selezionare il processo.
3. Fare clic su **Cartella di lavoro** o su **StdOut / Stderr** per accedere rapidamente a questi importanti file di registro.

    ![storage](media/manage-storage/job-workingfolder.png)
