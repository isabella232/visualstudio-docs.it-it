---
title: Creare un progetto di unit test
description: Informazioni su come creare un unit test progetto. Il progetto test può essere nella stessa soluzione del codice di produzione o in una soluzione separata.
ms.custom: SEO-VS-2020
ms.date: 01/29/2019
ms.topic: how-to
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-test
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: 81dcaf5bee778c3330f504030634db7b24030c5bf360528b7c23f3c472242811
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121395357"
---
# <a name="create-a-unit-test-project"></a>Creare un progetto di unit test

Gli unit test spesso simulano la struttura del codice sottoposto a test. Ad esempio, si crea un progetto unit test per ogni progetto di codice del prodotto. Il progetto test può essere nella stessa soluzione del codice di produzione o in una soluzione separata. È possibile avere più progetti unit test in una soluzione.

> [!NOTE]
> Il percorso degli unit test per un codice nativo e la struttura del progetto test possono essere diversi da quelli descritti in questo articolo. Per altre informazioni, vedere [Scrittura di unit test per C/C++.](writing-unit-tests-for-c-cpp.md)

## <a name="to-create-a-unit-test-project"></a>Per creare un progetto di unit test

1. Nel menu **File** scegliere **Nuovo** > **Progetto** o premere **CTRL**+**MAIUSC**+**N**.

::: moniker range="vs-2017"

2. Nella finestra **di dialogo Nuovo Project**  espandere il nodo Installato, scegliere la lingua da usare per il progetto di test e quindi **scegliere Test**.

3. Selezionare il modello di progetto per il framework di test che si vuole usare, ad esempio **Progetto di test MSTest** o **Progetto di test NUnit**. Assegnare un nome al progetto e quindi scegliere **OK**.

   ![Modelli di progetto di test in Visual Studio 2017](media/test-project-templates.png)

::: moniker-end

::: moniker range=">=vs-2019"

2. Nella casella di ricerca nella pagina **Crea un nuovo progetto** digitare **unit test**. Selezionare il modello di progetto per il framework di test che si vuole usare, ad esempio **Progetto di test MSTest** o **Progetto di test NUnit**, e quindi scegliere **Avanti**.

   ![Modelli di progetto di test in Visual Studio 2019](media/vs-2019/test-project-templates.png)

3. Nella pagina **Configura il nuovo progetto** immettere un nome per il progetto e quindi fare clic su **Crea**.

::: moniker-end

4. Nel progetto unit test, aggiungere un riferimento al codice sottoposto a test. Per aggiungere un riferimento a un progetto nella stessa soluzione:

   1. Selezionare il progetto di test in **Esplora soluzioni**.

   2. Nel menu **Project** scegliere **Aggiungi riferimento**.

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
