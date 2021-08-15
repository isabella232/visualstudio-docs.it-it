---
title: Misurare le prestazioni del codice Python
description: Usare il profiler di Visual Studio per verificare le prestazioni del codice Python quando si usano interpreti basati su CPython.
ms.date: 11/12/2018
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.technology: vs-python
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 1b607c0530efcb8846e765dd3019f7a03c98476d4137b03af9f13056e6a4cd5b
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121441729"
---
# <a name="profile-python-code"></a>Profilare il codice Python

È possibile eseguire la profilatura di un'applicazione Python quando si usano interpreti basati su CPython. (Vedere [Matrice delle funzionalità - Profilatura](overview-of-python-tools-for-visual-studio.md#matrix-profiling) per informazioni sulla disponibilità di questa funzionalità per le diverse versioni di Visual Studio.)

## <a name="profiling-for-cpython-based-interpreters"></a>Profilatura per interpreti basati su CPython

La profilatura viene avviata tramite il **comando di** menu Debug  >  **Avvia profilatura Python,** che apre una finestra di dialogo di configurazione:

![Finestra di dialogo di configurazione della profilatura](media/profiling-start.png)

Quando si fa clic su **OK**, viene eseguito il profiler e si apre un report di prestazioni che illustra in che modo viene impiegato il tempo nell'applicazione:

![Report di prestazioni del profiler](media/profiling-results.png)

> [!Note]
> Quando si profila un'applicazione Python Visual Studio raccoglie i dati per la durata del processo. Al momento non è possibile sospendere la profilatura. Microsoft vuole ricevere commenti e suggerimenti sulle funzionalità future. Usare il pulsante **Commenti sul prodotto** nella parte inferiore della pagina.

## <a name="profiling-for-ironpython"></a>Profilatura per IronPython

Dal momento che IronPython non è un interprete basato su CPython, la funzionalità di profilatura illustrata sopra non funziona.

Usare invece il profiler di Visual Studio .NET avviando direttamente *ipy.exe* come applicazione di destinazione e usando gli argomenti appropriati per eseguire lo script di avvio. Includere `-X:Debug` nella riga di comando per assicurarsi che sia possibile eseguire il debug e la profilatura per tutto il codice Python. Questo argomento genera un report di prestazioni che include il tempo impiegato sia nel runtime di IronPython che nel codice. Per identificare il codice, vengono usati nomi modificati.

In alternativa, IronPython presenta alcune funzionalità di profilatura incorporate, per le quali però non esiste ancora alcun visualizzatore adeguato. Per informazioni sulle opzioni disponibili, vedere [An IronPython Profiler](/archive/blogs/curth/an-ironpython-profiler) (Profiler per IronPython) nei blog di MSDN.