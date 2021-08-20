---
title: Generare override dei metodi Equals e GetHashCode C#
description: Informazioni su come usare il menu Azioni rapide e refactoring per generare metodi Equals e GetHashCode.
ms.custom: SEO-VS-2020
ms.date: 03/08/2021
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- dotnet
ms.openlocfilehash: 36f26e9ecbbd77cac7967f09d241f19ae158a36f
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122143937"
---
# <a name="generate-equals-and-gethashcode-method-overrides-in-visual-studio"></a>Generare override dei metodi Equals e GetHashCode in Visual Studio

Questa generazione di codice si applica a:

- C#

**Cosa:** consente di generare override dei metodi **Equals** e **GetHashCode**.

**Quando:** generare questi override quando si dispone di un tipo che deve essere confrontato in base a uno o più campi, invece che in base alla posizione dell'oggetto in memoria.

**Perché:**

- Se si implementa un tipo valore, è consigliabile eseguire l'override del **metodo Equals.** In questo caso, è possibile migliorare le prestazioni rispetto all'implementazione predefinita del metodo Equals in ValueType.

- Se si implementa un tipo riferimento, è consigliabile eseguire l'override del metodo **Equals** se il tipo è simile a un tipo di base, ad esempio Point, String, BigNumber e così via.

- Eseguire **l'override del metodo GetHashCode** per consentire il corretto funzionamento di un tipo in una tabella hash. Leggere ulteriori informazioni sugli [operatori di uguaglianza](/dotnet/standard/design-guidelines/equality-operators).

## <a name="how-to"></a>Procedure

1. Posizionare il cursore in un punto qualsiasi della riga della dichiarazione di tipo.

    ```csharp
    public class ImaginaryNumber
    {
        public double RealNumber { get; set; }
        public double ImaginaryUnit { get; set; }
    }
    ```

   Il codice dovrebbe essere simile allo screenshot seguente:

   ![Screenshot del codice evidenziato a cui applicare il metodo generato](media/overrides-highlight-cs.png)

   > [!TIP]
   > Se si fa doppio clic sul nome del tipo, la voce di menu non sarà disponibile. Posizionare semplicemente il cursore in un punto qualsiasi della riga.

1. Scegliere quindi una delle azioni seguenti:

   - Premere  + **CTRL.** per attivare il menu **Azioni rapide e refactoring**.

   - Fare clic con il pulsante destro del mouse e scegliere il menu **Azioni rapide e refactoring**.

   - Fare clic sull'icona ![Screenshot dell'icona del cacciavite azioni rapide in Visual Studio](../media/screwdriver-icon.png) che viene visualizzato nel margine sinistro.

1. Nel menu a discesa selezionare **Genera Equals(oggetto)** o **Genera equals e GetHashCode**.

   ![Screenshot del menu a discesa Genera sostituzioni](media/overrides-preview-cs.png)

1. Nella finestra di dialogo **Seleziona membri** selezionare i membri per cui si vogliono generare i metodi:

    ![Finestra di dialogo di generazione degli override](media/overrides-dialog-cs.png)

    > [!TIP]
    > È anche possibile scegliere di generare gli operatori da questa finestra di dialogo usando le caselle di controllo disponibili sotto la finestra di dialogo.

   I `Equals` metodi e vengono generati con `GetHashCode` implementazioni predefinite, come illustrato nel codice seguente:

    ```csharp
   public class ImaginaryNumber : IEquatable<ImaginaryNumber>
    {
        public double RealNumber { get; set; }
        public double ImaginaryUnit { get; set; }

        public override bool Equals(object obj)
        {
            return Equals(obj as ImaginaryNumber);
        }

        public bool Equals(ImaginaryNumber other)
        {
            return other != null &&
                   RealNumber == other.RealNumber &&
                   ImaginaryUnit == other.ImaginaryUnit;
        }

        public override int GetHashCode()
        {
            return HashCode.Combine(RealNumber, ImaginaryUnit);
        }
    }
    ```

   Il codice dovrebbe essere simile allo screenshot seguente:

   ![Screenshot del risultato del metodo generato](media/overrides-result-cs.png)

## <a name="see-also"></a>Vedi anche

- [Generazione del codice](../code-generation-in-visual-studio.md)
- [Anteprima modifiche](../../ide/preview-changes.md)
