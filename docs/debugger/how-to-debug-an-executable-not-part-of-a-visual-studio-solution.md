---
title: Eseguire il debug di un'app che non fa parte di una soluzione di Visual Studio
titleSuffix: ''
ms.custom: seodec18
ms.date: 11/19/2018
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- debugging [Visual Studio], executables
- executable files, importing
- executable files, debugging outside of projects
ms.assetid: 3ea176e8-1ce5-42c4-b7a2-abe3a2765033
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2db4cf8a678b6c20693dcc9c1e730d83f0d5ca7a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62848004"
---
# <a name="debug-an-app-that-isnt-part-of-a-visual-studio-solution-c-c-visual-basic-f"></a>Eseguire il debug di un'app che non fa parte di una soluzione di Visual Studio (C++, C#, Visual Basic, F#)

È possibile eseguire il debug di un'app (*.exe* file) che non fa parte di una soluzione di Visual Studio. Qualcuno potrebbe avere creato l'app all'esterno di Visual Studio o è stato creato l'app da altrove.

È il modo consueto per il debug di un'app che non esiste in Visual Studio per avviare l'app all'esterno di Visual Studio e quindi collegarli usando **Connetti a processo** nel debugger di Visual Studio. Per altre informazioni, vedere [Collega a processi in esecuzione](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).

Associazione a un'app richiede passaggi manuali che richiedono pochi secondi. A causa di questo ritardo, collegamento non aiuta a eseguire il debug di un problema di avvio, o un'app che non attende l'utente di input e viene completata rapidamente.

In queste situazioni, è possibile creare un progetto EXE di Visual Studio per l'app o importarla in un oggetto esistente C#, Visual Basic o C++ soluzione. I progetti EXE non sono supportati da tutti i linguaggi di programmazione.

>[!IMPORTANT]
>Funzionalità di debug per un'app che non è stato compilato in Visual Studio sono limitate, se si collega all'app o aggiungerlo a una soluzione di Visual Studio.
>
>Se si dispone del codice sorgente, l'approccio migliore consiste nell'importare il codice in un progetto di Visual Studio. Quindi, eseguire una build di debug dell'app.
>
>Se non hai il codice sorgente e l'app non dispone [le informazioni di debug](../debugger/how-to-set-debug-and-release-configurations.md) in un formato compatibile, funzionalità di debug disponibili sono un numero molto ridotto.

### <a name="to-create-a-new-exe-project-for-an-existing-app"></a>Per creare un nuovo progetto EXE per un'app esistente

1. In Visual Studio, selezionare **File** > **Open** > **progetto**.

1. Nel **Apri progetto** finestra di dialogo **tutti i file di progetto**, se non è già selezionata, nell'elenco a discesa accanto a **nomefile**.

1. Passare al *.exe* del file, selezionarlo e selezionare **Open**.

   Il file viene visualizzato in una nuova soluzione Visual Studio temporanea.

1. Avviare il debug dell'app selezionando un comando di esecuzione, ad esempio **Avvia debug**, dalle **Debug** menu.

### <a name="to-import-an-app-into-an-existing-visual-studio-solution"></a>Per importare un'app in una soluzione di Visual Studio esistente

1. Con un C++, C#, o Visual Basic soluzione aperta in Visual Studio, selezionare **File** > **Add** > **progetto esistente**.

1. Nel **Apri progetto** finestra di dialogo **tutti i file di progetto**, se non è già selezionata, nell'elenco a discesa accanto a **nomefile**.

1. Passare al *.exe* del file, selezionarlo e selezionare **Open**.

   Il file viene visualizzato come un nuovo progetto nella soluzione corrente.

1. Con il nuovo file selezionato, avviare il debug dell'app selezionando un comando di esecuzione, ad esempio **Avvia debug**, dalle **Debug** menu.

### <a name="see-also"></a>Vedere anche
- [Impostazioni del debugger e preparazione](../debugger/debugger-settings-and-preparation.md)
- [Sicurezza del debugger](../debugger/debugger-security.md)
- [File DBG](/previous-versions/visualstudio/visual-studio-2010/da528y14(v=vs.100))