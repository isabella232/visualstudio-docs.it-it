---
title: Riga di comando di profilatura - Creare file di dati portabili
description: Per semplificare la condivisione dei dati di profilatura, usare lo strumento VSPerfReport.exe da riga di comando per incorporare i simboli per un'esecuzione della profilatura nel file con estensione vsp.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 2ceb63a7-b835-4988-b756-2afc3fcc4808
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 7eadad8efebfa673a7e6c12e7dc67fb8b601f884
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126637235"
---
# <a name="create-portable-profiling-data-files-from-the-command-line"></a>Creare file dei dati di profilatura portabili dalla riga di comando
Per semplificare la condivisione dei dati di profilatura, è possibile usare lo strumento da riga di comando [VSPerfReport](../profiling/vsperfreport.md) per incorporare i simboli di un'esecuzione della profilatura nel file con estensione *vsp*.

 È anche possibile creare un file di dati di profilatura preanalizzato (con estensione *vsps*), più piccolo e più rapido da caricare nell'IDE.

> [!NOTE]
> Verificare che i file di simboli (con estensione *pdb*) siano disponibili per **VSPerfReport**. Per altre informazioni, vedere [Procedura: Specificare percorsi dei file di simboli dalla riga di comando](../profiling/how-to-specify-symbol-file-locations-from-the-command-line.md).
>
> Per informazioni sul percorso di **VSReport**, vedere [Specificare il percorso degli strumenti da riga di comando](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).
>
> Non è possibile filtrare i dati di profilatura di un file con estensione *vsps*.

### <a name="to-embed-the-symbols-for-a-profiling-run-into-a-profiling-data-vsp-file"></a>Per incorporare i simboli per un'esecuzione della profilatura in un file di dati di profilatura (con estensione *vsp*)

- In una finestra del prompt dei comandi, digitare il comando seguente:

   \<Path><strong>VsPerfReport \<</strong> VSP File> **/PackSymbols**

   Per impostazione predefinita, il file con estensione *vsps* è denominato con il nome base del file con estensione *vsp*. È possibile specificare un nome alternativo con l'opzione **Output**.

### <a name="to-create-a-summary-profiling-data-file"></a>Per creare un file di riepilogo dati di profilatura

- In una finestra del prompt dei comandi, digitare il comando seguente:

   \<Path><strong>VSPerfReport \<</strong> VSP File> **/SummaryFile** [**/Output:** \<File Name> ]

   Per impostazione predefinita, il file con estensione *vsps* è denominato con il nome base del file con estensione *vsp*. È possibile specificare un nome alternativo con l'opzione **Output**.
