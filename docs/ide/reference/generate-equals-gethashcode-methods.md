---
title: Generare override dei metodi Equals e GetHashCode C#
ms.date: 01/26/2018
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: f9b1a639dd655f4f75b21555396866858b144010
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/18/2020
ms.locfileid: "75569283"
---
# <a name="generate-equals-and-gethashcode-method-overrides-in-visual-studio"></a>Generare override dei metodi Equals e GetHashCode in Visual Studio

Questa generazione di codice si applica a:

- C#

**Cosa:** consente di generare override dei metodi **Equals** e **GetHashCode**.

**Quando:** generare questi override quando si dispone di un tipo che deve essere confrontato in base a uno o più campi, invece che in base alla posizione dell'oggetto in memoria.

**Perché:**

- se si implementa un tipo valore, è consigliabile valutare la possibilità di eseguire l'override del metodo **Equals** per ottenere migliori prestazioni rispetto all'implementazione predefinita del metodo Equals su ValueType.

- Se si implementa un tipo di riferimento, è consigliabile eseguire l'override del metodo **Equals** se il tipo è simile a un tipo di base, ad esempio Point, String, BigNumber e così via.

- Eseguire l'override di **GetHashCode** metodo per consentire a un tipo di funzionare correttamente in una tabella hash. Leggere ulteriori informazioni sugli [operatori di uguaglianza](/dotnet/standard/design-guidelines/equality-operators).

## <a name="how-to"></a>Procedure

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

- [Generazione di codice](../code-generation-in-visual-studio.md)
- [Anteprima delle modifiche](../../ide/preview-changes.md)
