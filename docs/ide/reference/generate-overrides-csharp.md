---
title: Generare override dei metodi Equals e GetHashCode - Generazione del codice (C#) | Microsoft Docs
ms.custom: 
ms.date: 11/27/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
author: kuhlenh
ms.author: kaseyu
manager: ghogen
ms.workload:
- dotnet
ms.openlocfilehash: 56b1753dbdcfbf8ce318e964a16879f02b1482c4
ms.sourcegitcommit: b01406355e3b97547b7cbf8ce3960f101b165cec
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/06/2018
---
# <a name="generate-equals-and-gethashcode-method-overrides-in-c"></a>Generare override dei metodi Equals e GetHashCode in C# #

**Cosa:** consente di generare override dei metodi **Equals** e **GetHashCode**.

**Quando:** generare questi override quando si dispone di un tipo che rappresenta un "valore" che deve essere confrontato in base ad alcuni campi, invece che in base alla posizione dell'oggetto in memoria.

**Perché:** se si implementa un tipo valore, è consigliabile valutare la possibilità di eseguire l'override del metodo Equals per ottenere migliori prestazioni rispetto all'implementazione predefinita del metodo Equals su ValueType.

Se si implementa un tipo riferimento, è consigliabile eseguire l'override del metodo Equals, se il tipo è simile a un tipo di base, ad esempio Point, String, BigNumber e così via.

Eseguire l'override del metodo GetHashCode per consentire il funzionamento corretto di un tipo in una tabella hash. Leggere ulteriori informazioni sugli [operatori di uguaglianza](/dotnet/standard/design-guidelines/equality-operators).

**Come:**

1. Posizionare il cursore nella dichiarazione del tipo.

   ![Codice evidenziato](media/overrides-highlight-cs.png)

1. Eseguire quindi una delle operazioni seguenti:
   * **Tastiera**
     * Premere **CTRL+.** per attivare il menu **Azioni rapide e refactoring** e selezionare **Genera Equals(oggetto)** oppure **Genera Equals e GetHashCode** dal popup della finestra di anteprima.
   * **Mouse**
     * Fare clic con il pulsante destro del mouse e scegliere il menu **Azioni rapide e refactoring**, quindi selezionare **Genera Equals(oggetto)** oppure **Genera Equals e GetHashCode** dal popup della finestra di anteprima.
     * Fare clic sul pulsante ![lampadina](media/bulb-cs.png) che viene visualizzata nel margine sinistro se il cursore del testo si trova già nella riga con la dichiarazione del tipo.

   ![Anteprima della generazione di override](media/overrides-preview-cs.png)

1. Selezionare i membri per i quali si vogliono generare i metodi di override:

    ![Finestra di dialogo di generazione degli override](media/overrides-dialog-cs.png)

    > [!TIP]
    > È anche possibile scegliere di generare gli operatori da questa finestra di dialogo usando le caselle di controllo sotto l'elenco dei membri.

1. Gli override per Equals e GetHashCode verranno generati con le implementazioni predefinite automatiche.

   ![Risultato della generazione del metodo](media/overrides-result-cs.png)

## <a name="see-also"></a>Vedere anche

[Generazione codice](../code-generation-in-visual-studio.md)  
[Visualizzare l'anteprima delle modifiche](../../ide/preview-changes.md)
