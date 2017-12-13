---
title: Misurazione delle prestazioni del codice Python in Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 07/13/2017
ms.reviewer: 
ms.suite: 
ms.technology: devlang-python
ms.devlang: python
ms.tgt_pltfrm: 
ms.topic: article
caps.latest.revision: "1"
author: kraigb
ms.author: kraigb
manager: ghogen
ms.openlocfilehash: 1f873ab7b8954f9ac8ebf089a3719e34be8e03ba
ms.sourcegitcommit: b7d3b90d0be597c9d01879338dd2678c881087ce
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/01/2017
---
# <a name="profiling-python-code"></a>Profilatura del codice Python

In Visual Studio è possibile eseguire la profilatura di un'applicazione Python quando si usano interpreti basati su CPython.

Per avviare la profilatura, si usa il comando di menu **Analizza > Avvia profilatura Python**, che consente di aprire una finestra di dialogo di configurazione:

![Finestra di dialogo di configurazione della profilatura](media/profiling-start.png)

Quando si fa clic su **OK**, viene eseguito il profiler e si apre un report di prestazioni che illustra in che modo viene impiegato il tempo nell'applicazione:

![Report di prestazioni del profiler](media/profiling-results.png)

Per una dimostrazione, vedere il video [Profiling Python](https://mva.microsoft.com/en-US/training-courses/python-tools-for-visual-studio-2017-18121?l=hb46k6LWE_405918567) (Profilatura di Python) (Microsoft Virtual Academy, 3m00s).

> [!VIDEO https://mva.microsoft.com/en-US/training-courses-embed/python-tools-for-visual-studio-2017-18121/Video-Testing-Python-hb46k6LWE_405918567]


## <a name="profiling-for-ironpython"></a>Profilatura per IronPython

Dal momento che IronPython non è un interprete basato su CPython, la funzionalità di profilatura illustrata sopra non funziona.

Usare invece il profiler di Visual Studio .NET avviando direttamente `ipy.exe` come applicazione di destinazione e usando gli argomenti appropriati per eseguire lo script di avvio. Includere `-X:Debug` nella riga di comando per forzare il debug e la profilatura per tutto il codice Python. Questo argomento genera un report di prestazioni che include il tempo impiegato sia nel runtime di IronPython che nel codice. Per identificare il codice, vengono usati nomi modificati.

In alternativa, IronPython presenta alcune funzionalità di profilatura incorporate, per le quali però non esiste ancora alcun visualizzatore adeguato. Per informazioni sulle opzioni disponibili, vedere [An IronPython Profiler](http://blogs.msdn.com/b/curth/archive/2009/03/29/an-ironpython-profiler.aspx) (Profiler per IronPython) nei blog di MSDN.