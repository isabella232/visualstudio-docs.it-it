---
title: Eseguire il debug di un'app che non fa parte di una soluzione di Visual Studio
titleSuffix: ''
ms.custom: ''
ms.date: 02/21/2020
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
ms.openlocfilehash: 740af718a2928991d46bedbd6709337b9b20a254
ms.sourcegitcommit: bf2e9d4ff38bf5b62b8af3da1e6a183beb899809
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/22/2020
ms.locfileid: "77557908"
---
# <a name="debug-an-app-that-isnt-part-of-a-visual-studio-solution-c-c-visual-basic-f"></a>Eseguire il debug di un'app che non fa parte di unaC++soluzione C#di Visual Studio F#(,, Visual Basic,)

Potrebbe essere necessario eseguire il debug di un'app (file con*estensione exe* ) che non fa parte di una soluzione di Visual Studio. Potrebbe trattarsi di un progetto di [cartella aperta](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md) oppure è possibile che l'app sia stata creata all'esterno di Visual Studio oppure che l'app sia stata creata da un'altra posizione.

- Per un progetto di cartella aperta in Visual Studio (che non include alcun file di progetto o di soluzione), vedere [eseguire ed eseguire il debug del codice](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md#run-and-debug-your-code) oppure, per C++, [configurare i parametri di debug con Launch. vs. JSON](/cpp/build/open-folder-projects-cpp#configure-debugging-parameters-with-launchvsjson).

- Per un'app che non esiste in Visual Studio, il modo consueto per eseguire il debug è avviare l'app all'esterno di Visual Studio e quindi collegarla usando **Connetti a processo** nel debugger di Visual Studio. Per ulteriori informazioni, vedere [Connetti a processi in esecuzione](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).

   Per la connessione a un'app sono necessari passaggi manuali che richiedono alcuni secondi. A causa di questo ritardo, la connessione non consentirà di eseguire il debug di un problema di avvio o di un'app che non attende l'input dell'utente e termina rapidamente.

   In queste situazioni, è possibile creare un progetto EXE di Visual Studio per l'app oppure importarlo in una C#soluzione, Visual Basic o C++ esistente. I progetti EXE non sono supportati da tutti i linguaggi di programmazione.

>[!IMPORTANT]
>Le funzionalità di debug per un'app che non è stata compilata in Visual Studio sono limitate, indipendentemente dal fatto che ci si colleghi all'app o la si aggiunga a una soluzione di Visual Studio.
>
>Se si dispone del codice sorgente, l'approccio migliore consiste nell'importare il codice in un progetto di Visual Studio. Eseguire quindi una build di debug dell'app.
>
>Se non si dispone del codice sorgente e l'app non dispone di [informazioni di debug](../debugger/how-to-set-debug-and-release-configurations.md) in un formato compatibile, le funzionalità di debug disponibili sono pochissime.

### <a name="to-create-a-new-exe-project-for-an-existing-app"></a>Per creare un nuovo progetto EXE per un'app esistente

1. In Visual Studio selezionare **File** > **Apri** > **progetto**.

1. Nella finestra di dialogo **Apri progetto** selezionare **tutti i file di progetto**, se non è già selezionato, nell'elenco a discesa accanto a **nome file**.

1. Passare al file con *estensione exe* , selezionarlo e selezionare **Apri**.

   Il file viene visualizzato in una nuova soluzione temporanea di Visual Studio.

1. Avviare il debug dell'app selezionando un comando di esecuzione, ad esempio **Avvia debug**, dal menu **debug** .

### <a name="to-import-an-app-into-an-existing-visual-studio-solution"></a>Per importare un'app in una soluzione Visual Studio esistente

1. C++Con C#, o Visual Basic soluzione aperta in Visual Studio, selezionare **file** > **Aggiungi** > **progetto esistente**.

1. Nella finestra di dialogo **Apri progetto** selezionare **tutti i file di progetto**, se non è già selezionato, nell'elenco a discesa accanto a **nome file**.

1. Passare al file con *estensione exe* , selezionarlo e selezionare **Apri**.

   Il file viene visualizzato come nuovo progetto nella soluzione corrente.

1. Con il nuovo file selezionato, avviare il debug dell'app selezionando un comando di esecuzione, ad esempio **Avvia debug**, dal menu **debug** .

### <a name="see-also"></a>Vedere anche
- [Impostazioni del debugger e preparazione](../debugger/debugger-settings-and-preparation.md)
- [Sicurezza del debugger](../debugger/debugger-security.md)
- [File DBG](/previous-versions/visualstudio/visual-studio-2010/da528y14(v=vs.100))