---
title: Installare analizzatori di terze parti
ms.date: 08/27/2020
description: Informazioni su come installare analizzatori di terze parti in Visual Studio. Vedere come installare gli analizzatori nei file con estensione vsix e nei NuGet analyzer.
ms.custom: SEO-VS-2020
ms.topic: conceptual
helpviewer_keywords:
- code analysis, managed code
- analyzers
- Roslyn analyzers
author: mikadumont
ms.author: midumont
manager: jmartens
ms.technology: vs-ide-code-analysis
ms.workload:
- dotnet
ms.openlocfilehash: a31fbbc8a0e655418425416ffdcae3aa16810788
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126631907"
---
# <a name="install-third-party-analyzers"></a>Installare analizzatori di terze parti

Visual Studio include un set di .NET Compiler Platform (*Roslyn*) analizzatori. Questi analizzatori sono sempre disponibili. È possibile installare analizzatori aggiuntivi come NuGet pacchetti o come Visual Studio estensioni nei *file VSIX.*

## <a name="to-install-nuget-analyzer-packages"></a>Per installare i NuGet analyzer

1. Trovare il pacchetto dell'analizzatore che si vuole installare www.nuget.org.

   Ad esempio, è possibile installare [StyleCop.Analyzers](https://www.nuget.org/packages/stylecop.analyzers/) per cercare i problemi di stile nella codebase.

2. Installare il pacchetto in Visual Studio, usando la [console Gestione pacchetti o](/nuget/quickstart/install-and-use-a-package-in-visual-studio#package-manager-console) l'interfaccia Gestione pacchetti interfaccia [utente](/nuget/quickstart/install-and-use-a-package-in-visual-studio#package-manager-console).

   > [!NOTE]
   > La www.nuget.org per ogni pacchetto dell'analizzatore mostra il comando da incollare **nella console Gestione pacchetti .** È anche presente un pratico pulsante per copiare il testo negli Appunti.

   Gli assembly dell'analizzatore vengono installati e visualizzati **Esplora soluzioni** in   >  **Analizzatori riferimenti**.

## <a name="to-install-vsix-analyzers"></a>Per installare gli analizzatori VSIX

::: moniker range="vs-2017"

1. In Visual Studio selezionare **Estensioni** > **e aggiornamenti degli strumenti**.

   Verrà visualizzata la finestra di dialogo **Estensioni e aggiornamenti**.

   > [!NOTE]
   > In alternativa, è possibile trovare e scaricare l'estensione dell'analizzatore direttamente [da Visual Studio Marketplace.](https://marketplace.visualstudio.com)

::: moniker-end

::: moniker range=">=vs-2019"

1. In Visual Studio selezionare **Estensioni** > **Gestisci estensioni**.

   Verrà **visualizzata la finestra di** dialogo Gestisci estensioni .

   > [!NOTE]
   > In alternativa, è possibile trovare e scaricare l'estensione dell'analizzatore direttamente [da Visual Studio Marketplace.](https://marketplace.visualstudio.com)

::: moniker-end

2. Espandere **Online** nel riquadro sinistro e quindi selezionare Visual Studio **Marketplace.**

3. Nella casella di ricerca digitare il nome dell'estensione dell'analizzatore da installare.

4. Selezionare **Download**.

   L'estensione viene scaricata.

5. Selezionare **OK** per chiudere la finestra di dialogo e quindi chiudere tutte le istanze di Visual Studio avviare il programma **di installazione VSIX.**

   Verrà visualizzata la finestra di dialogo Programma di installazione **VSIX.**

   ![Programma di installazione VSIX per Microsoft Code Analysis](media/vsix-installer-code-analysis.png)

6. Selezionare **Modifica** per avviare l'installazione.

7. Dopo uno o due minuti, l'installazione viene completata. Selezionare **Chiudi**.

8. Aprire Visual Studio nuovo.

::: moniker range="vs-2017"

Per verificare se l'estensione è installata, selezionare **Estensioni**  >  **e aggiornamenti degli strumenti**. Nella finestra **di dialogo Estensioni e** aggiornamenti selezionare la categoria **Installato** a sinistra e quindi cercare l'estensione in base al nome.

::: moniker-end

::: moniker range=">=vs-2019"

Per verificare se l'estensione è installata, selezionare **Estensioni**  >  **Gestisci estensioni**. Nella finestra **di dialogo Gestisci** estensioni selezionare la categoria **Installato** a sinistra e quindi cercare l'estensione in base al nome.

::: moniker-end

## <a name="next-steps"></a>Passaggi successivi

> [!div class="nextstepaction"]
> [Usare gli analizzatori del codice in Visual Studio](../code-quality/use-roslyn-analyzers.md)

## <a name="see-also"></a>Vedi anche

- [Panoramica degli analizzatori del codice in Visual Studio](../code-quality/roslyn-analyzers-overview.md)
- [Installare gli analizzatori .NET](../code-quality/install-net-analyzers.md)
