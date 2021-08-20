---
title: Eseguire il debug di un'app che non fa parte di una Visual Studio soluzione
titleSuffix: ''
description: Informazioni su come eseguire il debug di un'app che non fa parte di una Visual Studio soluzione. Potrebbe essere possibile collegare il debugger Visual Studio remoto.
ms.custom: SEO-VS-2020
ms.date: 02/21/2020
ms.topic: how-to
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
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 7d93a34e0599495672437f086790bee1f02ccabe
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122120972"
---
# <a name="debug-an-app-that-isnt-part-of-a-visual-studio-solution-c-c-visual-basic-f"></a>Eseguire il debug di un'app che non fa parte di una soluzione Visual Studio (C++, C#, Visual Basic, F#)

È possibile eseguire il debug di un'app *(.exe* file) che non fa parte di una Visual Studio soluzione. Potrebbe trattarsi di [un progetto di](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md) cartella aperta oppure è possibile che l'app sia stata creata da un altro utente all'esterno di Visual Studio oppure che l'app sia stata creata da un'altra posizione.

- Per un progetto di cartella aperta in Visual Studio (senza file di progetto o soluzione), vedere Eseguire ed eseguire il [debug](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md#run-and-debug-your-code) del codice o, per C++, Configurare i parametri di debug con launch.vs.js[in](/cpp/build/open-folder-projects-cpp#configure-debugging-parameters-with-launchvsjson).

- Per un'app che non esiste in Visual Studio, il modo consueto per eseguire il debug è avviare l'app all'esterno di Visual Studio e quindi connettersi usando Collega a processo nel debugger di Visual Studio.  Per altre informazioni, vedere [Connettersi ai processi in esecuzione.](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)

   Il collegamento a un'app richiede passaggi manuali che richiedono alcuni secondi. A causa di questo ritardo, il collegamento non consente di eseguire il debug di un problema di avvio o di un'app che non attende l'input dell'utente e termina rapidamente.

   In queste situazioni è possibile creare un progetto EXE Visual Studio per l'app o importarlo in una soluzione C#, Visual Basic o C++esistente. I progetti EXE non sono supportati da tutti i linguaggi di programmazione.

>[!IMPORTANT]
>Le funzionalità di debug per un'app non Visual Studio sono limitate, indipendentemente dal fatto che si allegare all'app o aggiungerla a una Visual Studio soluzione.
>
>Se si ha il codice sorgente, l'approccio migliore consiste nell'importare il codice in un Visual Studio progetto. Eseguire quindi una build di debug dell'app.
>
>Se non si ha il codice sorgente e l'app non dispone di informazioni di [debug](../debugger/how-to-set-debug-and-release-configurations.md) in un formato compatibile, le funzionalità di debug disponibili sono molto poche.

### <a name="to-create-a-new-exe-project-for-an-existing-app"></a>Per creare un nuovo progetto EXE per un'app esistente

1. In Visual Studio selezionare **Apri file**  >  **Project**  >  .

1. Nella finestra **di dialogo Apri** Project selezionare Tutti Project **file**, se non è già selezionato, nell'elenco a discesa accanto a **Nome file**.

1. Passare al file *.exe,* selezionarlo e selezionare **Apri**.

   Il file viene visualizzato in una nuova soluzione Visual Studio temporanea.

1. Avviare il debug dell'app selezionando un comando di esecuzione, ad esempio **Avvia debug**, dal menu **Debug.**

### <a name="to-import-an-app-into-an-existing-visual-studio-solution"></a>Per importare un'app in una soluzione Visual Studio esistente

1. Con una soluzione C++, C# o Visual Basic aperta in Visual Studio selezionare **Aggiungi** file esistente  >    >  **Project**.

1. Nella finestra **di dialogo Apri** Project selezionare Tutti Project **file**, se non è già selezionato, nell'elenco a discesa accanto a **Nome file**.

1. Passare al file *.exe,* selezionarlo e selezionare **Apri**.

   Il file viene visualizzato come nuovo progetto nella soluzione corrente.

1. Con il nuovo file selezionato, avviare il debug dell'app selezionando un comando di esecuzione, ad esempio **Avvia debug**, dal menu **Debug.**

### <a name="see-also"></a>Vedi anche
- [Impostazioni del debugger e preparazione](../debugger/debugger-settings-and-preparation.md)
- [Sicurezza del debugger](../debugger/debugger-security.md)
- [File DBG](/previous-versions/visualstudio/visual-studio-2010/da528y14(v=vs.100))
