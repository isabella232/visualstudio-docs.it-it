---
title: Generare Equals e GetHashCode (metodo) sostituzioni - la generazione di codice (c#) | Documenti Microsoft
ms.custom: 
ms.date: 11/27/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
author: kuhlenh
ms.author: kaseyu
manager: ghogen
ms.workload: dotnet
ms.openlocfilehash: ce415cd6b86d8a5bd9bc905f3bc6b395d06753f5
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="generate-equals-and-gethashcode-method-overrides-in-c"></a>Generare Equals e GetHashCode (metodo) esegue l'override in c# #

**Novità:** consente di generare **è uguale a** e **GetHashCode** metodi.

**Quando:** generare questi override quando si dispone di un tipo che rappresenta un "valore" che debba essere confrontato con alcuni campi, anziché dalla posizione dell'oggetto in memoria.

**Motivo:** se si implementa un tipo di valore, è consigliabile eseguire l'override del metodo Equals per aumentare le prestazioni rispetto all'implementazione predefinita del metodo Equals in ValueType.

Se si implementa un tipo riferimento, è consigliabile l'override del metodo Equals, se il tipo è simile a un tipo di base, ad esempio punto, stringa, BigNumber e così via.

Eseguire l'override del metodo GetHashCode per consentire a un tipo di funzionare correttamente in una tabella hash. Leggere informazioni aggiuntive su [gli operatori di uguaglianza](/dotnet/standard/design-guidelines/equality-operators).

**Procedura:**

1. Posizionare il cursore nella dichiarazione di tipo.

   ![Codice evidenziato](media/overrides_highlight.png)

1. Successivamente, eseguire una delle operazioni seguenti:
   * **Tastiera**
     * Premere **Ctrl +.** Per attivare il **azioni rapide e refactoring** dal menu **generare Equals(object)** o **generare Equals e GetHashCode** nel popup di finestra di anteprima.
   * **Mouse**
     * Mouse e scegliere il **azioni rapide e refactoring** dal menu **generare Equals(object)** o **generare Equals e GetHashCode** dalla finestra di anteprima Popup.
     * Fare clic sul pulsante ![Lampadina](media/bulb.png) icona che verrà visualizzata nel margine sinistro se il cursore di testo si trova già nella riga con la dichiarazione del tipo.

   ![Generare l'anteprima di sostituzioni](media/overrides_preview.png)

1. Selezionare i membri che si desidera generare i metodi di override per:

    ![Generare una finestra di dialogo sostituzioni](media/overrides_dialog.png)

    > [!TIP]
    > È anche possibile generare gli operatori da questa finestra di dialogo utilizzando le caselle di controllo sotto l'elenco dei membri.

1. Equals e GetHashCode sostituzioni verranno generate con le implementazioni predefinite automatico.

   ![Generare il risultato (metodo)](media/overrides_result.png)

## <a name="see-also"></a>Vedere anche

[Code Generation (C#)](../code-generation-csharp.md) (Generazione di codice (C#))  
[Visualizzare l'anteprima delle modifiche](../../ide/preview-changes.md)
