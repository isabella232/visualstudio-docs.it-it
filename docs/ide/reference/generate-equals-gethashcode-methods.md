---
title: Generare override dei metodi Equals e GetHashCode C#
ms.date: 01/26/2018
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: bbe04ac7a28666f32aa1da3bebe5ed50f96fb900
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62790592"
---
# <a name="generate-equals-and-gethashcode-method-overrides-in-visual-studio"></a>Generare override dei metodi Equals e GetHashCode in Visual Studio

Questa generazione di codice si applica a:

- C#

**Cosa:** consente di generare override dei metodi **Equals** e **GetHashCode**.

**Quando:** generare questi override quando si dispone di un tipo che deve essere confrontato in base a uno o più campi, invece che in base alla posizione dell'oggetto in memoria.

**Perché?:**

- se si implementa un tipo valore, è consigliabile valutare la possibilità di eseguire l'override del metodo **Equals** per ottenere migliori prestazioni rispetto all'implementazione predefinita del metodo Equals su ValueType.

- Se si implementa un tipo riferimento, è consigliabile eseguire l'override del metodo **Equals**, se il tipo è simile a un tipo di base, ad esempio Point, String, BigNumber e così via.

- Eseguire l'override del metodo **GetHashCode** per consentire il funzionamento corretto di un tipo in una tabella hash. Leggere ulteriori informazioni sugli [operatori di uguaglianza](/dotnet/standard/design-guidelines/equality-operators).

## <a name="how-to"></a>Procedura

1. Posizionare il cursore in un punto qualsiasi della riga della dichiarazione di tipo.

   ![Codice evidenziato](media/overrides-highlight-cs.png)

   > [!TIP]
   > Se si fa doppio clic sul nome del tipo, la voce di menu non sarà disponibile. Posizionare semplicemente il cursore in un punto qualsiasi della riga.

1. Eseguire quindi una delle operazioni seguenti:

   - Premere **CTRL**+**.** per attivare il menu **Azioni rapide e refactoring**.

   - Fare clic con il pulsante destro del mouse e scegliere il menu **Azioni rapide e refactoring**.

   - Fare clic sul pulsante ![cacciavite](../media/screwdriver-icon.png) che viene visualizzato nel margine sinistro.

   ![Anteprima della generazione di override](media/overrides-preview-cs.png)

1. Scegliere **Genera Equals(oggetto)** o **Genera Equals e GetHashCode** dal menu a discesa.

1. Nella finestra di dialogo **Seleziona membri** selezionare i membri per cui si vogliono generare i metodi:

    ![Finestra di dialogo di generazione degli override](media/overrides-dialog-cs.png)

    > [!TIP]
    > È anche possibile scegliere di generare gli operatori da questa finestra di dialogo usando le caselle di controllo disponibili sotto la finestra di dialogo.

   I metodi `Equals` e `GetHashCode` vengono generati con implementazioni predefinite.

   ![Risultato della generazione del metodo](media/overrides-result-cs.png)

## <a name="see-also"></a>Vedere anche

- [Generazione codice](../code-generation-in-visual-studio.md)
- [Visualizzare l'anteprima delle modifiche](../../ide/preview-changes.md)