---
title: Creare un progetto di unit test
ms.date: 01/29/2019
ms.topic: conceptual
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: ca83689628f02a8c7a2e0166b390d5b277086c1d
ms.sourcegitcommit: 489aca71046fb6e4aafd0a4509cd7dc149d707b1
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2019
ms.locfileid: "58416136"
---
# <a name="create-a-unit-test-project"></a>Creare un progetto di unit test

Gli unit test spesso simulano la struttura del codice sottoposto a test. Ad esempio, si crea un progetto unit test per ogni progetto di codice del prodotto. Il progetto test può essere nella stessa soluzione del codice di produzione o in una soluzione separata. È possibile avere più progetti unit test in una soluzione.

> [!NOTE]
> Il percorso degli unit test per un codice nativo e la struttura del progetto test possono essere diversi da quelli descritti in questo articolo. Per altre informazioni, vedere [Scrittura di unit test per C/C++](writing-unit-tests-for-c-cpp.md).

## <a name="to-create-a-unit-test-project"></a>Per creare un progetto di unit test

1. Nel menu **File** scegliere **Nuovo** > **Progetto** o premere **CTRL**+**MAIUSC**+**N**.

::: moniker range="vs-2017"

2. Nella finestra di dialogo **Nuovo progetto** espandere il nodo **Installato**, scegliere il linguaggio da usare per il progetto di test, quindi scegliere **Test**.

3. Per usare uno dei framework per unit test Microsoft, scegliere **Progetto unit test** dall'elenco di modelli di progetto. In alternativa, scegliere il modello di progetto del framework per unit test che si vuole usare. Assegnare il nome al progetto e scegliere **OK**.

::: moniker-end

::: moniker range=">=vs-2019"

2. Nella casella di ricerca nella pagina **Crea un nuovo progetto** digitare **unit test**. Selezionare il modello di progetto **Progetto unit test (.NET Framework)** e quindi fare clic su **Avanti**.

3. Nella pagina **Configura il nuovo progetto** immettere un nome per il progetto e quindi fare clic su **Crea**.

::: moniker-end

4. Nel progetto unit test, aggiungere un riferimento al codice sottoposto a test. Per aggiungere un riferimento a un progetto nella stessa soluzione:

   1. Selezionare il progetto di test in **Esplora soluzioni**.

   2. Scegliere **Aggiungi riferimento** dal menu **Progetto**.

   3. In **Gestione riferimenti** selezionare il nodo **Soluzione** in **Progetti**. Selezionare il progetto di codice da testare, quindi selezionare **OK**.

   Se il codice che si vuole testare è in un altro percorso, vedere [Gestione dei riferimenti in un progetto](../ide/managing-references-in-a-project.md) per informazioni sull'aggiunta di riferimenti.

## <a name="next-steps"></a>Passaggi successivi

Vedere una delle sezioni seguenti:

**Scrittura di unit test**

- [Eseguire unit test del codice](../test/unit-test-your-code.md)

- [Scrittura di unit test per C/C++](writing-unit-tests-for-c-cpp.md)

- [Usare il framework MSTest negli unit test](using-microsoft-visualstudio-testtools-unittesting-members-in-unit-tests.md)

**Esecuzione di unit test**

- [Eseguire unit test con Esplora test](../test/run-unit-tests-with-test-explorer.md)