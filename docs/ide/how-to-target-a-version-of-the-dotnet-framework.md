---
title: Destinare una versione di .NET
ms.date: 03/21/2019
ms.topic: conceptual
helpviewer_keywords:
- targeting .NET [Visual Studio]
- .NET version [Visual Studio]
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 2c316610fc007e3e8642567c01a5172feb461bda
ms.sourcegitcommit: 12f2851c8c9bd36a6ab00bf90a020c620b364076
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/06/2019
ms.locfileid: "66747127"
---
# <a name="how-to-target-a-version-of-net"></a>Procedura: Destinare una versione di .NET

Questo articolo descrive come specificare come destinazione una versione specifica di .NET Framework quando si crea un progetto .NET Framework. Descrive inoltre come modificare la versione di destinazione in progetto Visual Basic, C# o F# esistente.

> [!IMPORTANT]
> Per informazioni su come modificare la versione di destinazione per progetti C++, vedere [Procedura: Modificare il framework di destinazione e il set di strumenti della piattaforma](/cpp/build/how-to-modify-the-target-framework-and-platform-toolset).

## <a name="target-a-version-when-you-create-a-project"></a>Scegliere una versione di destinazione durante la creazione di un progetto

Quando si crea un progetto .NET Framework, le versioni di .NET Framework disponibili dipendono dalle quali versioni sono installate e dal modello di progetto selezionato.

1. Nella barra dei menu scegliere **File** > **Nuovo** > **Progetto**.

1. Scegliere un modello di .NET Framework per il tipo di progetto che si desidera creare.

1. Nell'elenco a discesa **Framework** nella parte inferiore della finestra di dialogo scegliere la versione di .NET Framework a cui si vuole destinare il progetto.

   L'elenco dei framework mostra solo le versioni applicabili al modello scelto.

   > [!NOTE]
   > Alcuni tipi di progetto, ad esempio .NET Core, non vengono visualizzate le **Framework** elenco a discesa.

   ::: moniker range="vs-2017"

   ![Framework elenco a discesa nella finestra di dialogo Nuovo progetto Visual Studio 2017](media/vside-newproject-framework.png)

   ::: moniker-end

   ::: moniker range=">=vs-2019"

   ![Selettore di Framework in Visual Studio 2019](media/vs-2019/configure-new-project-framework.png)

   ::: moniker-end

1. Continuare con la [creazione del progetto](create-new-project.md).

## <a name="change-the-targeted-version"></a>Cambiare la versione di destinazione

È possibile modificare la versione di destinazione di .NET in un Visual Basic, C#, o F# progetto seguendo questa procedura.

1. In **Esplora soluzioni** aprire il menu di scelta rapida del progetto che si vuole modificare e scegliere **Proprietà**.

    ![Proprietà Esplora soluzioni di Visual Studio](../ide/media/vs_slnexplorer_properties.png)

1. Nella colonna sinistra della finestra **Proprietà** scegliere la scheda **Applicazione**.

    ![Scheda Applicazione delle proprietà app in Visual Studio](../ide/media/vs_slnexplorer_properties_applicationtab.png)

    > [!NOTE]
    > Dopo aver creato un'app UWP, è possibile modificare la versione di destinazione di .NET o Windows.

1. Nell'elenco **Framework di destinazione** selezionare la versione appropriata.

1. Nella finestra di dialogo di verifica visualizzata scegliere **Sì**.

    Il progetto verrà scaricato. Quando ricarica, ha come destinazione la versione di .NET che si è scelto.

    > [!NOTE]
    > Se il codice contiene riferimenti a una versione diversa di .NET rispetto a quello di destinazione, messaggi di errore vengono visualizzati quando si compila o si esegue il codice. Per risolvere questi errori è necessario modificare i riferimenti. Visualizzare [risolvere i .NET targeting errori](../msbuild/troubleshooting-dotnet-framework-targeting-errors.md).

## <a name="see-also"></a>Vedere anche

- [Framework come destinazione di panoramica](../ide/visual-studio-multi-targeting-overview.md)
- [Risolvere i problemi relativi agli errori di impostazione di .NET Framework come destinazione](../msbuild/troubleshooting-dotnet-framework-targeting-errors.md)
- [Applicazione (pagina), Creazione progetti (C#)](../ide/reference/application-page-project-designer-csharp.md)
- [Pagina Applicazione, Creazione progetti (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md)
- [Procedura: Modificare il framework di destinazione e il set di strumenti della piattaforma (C++)](/cpp/build/how-to-modify-the-target-framework-and-platform-toolset)