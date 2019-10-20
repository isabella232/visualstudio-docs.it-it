---
title: Installare gli analizzatori Roslyn
ms.date: 08/03/2018
ms.topic: conceptual
helpviewer_keywords:
- code analysis, managed code
- analyzers
- Roslyn analyzers
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: b204d6824f06037341420d27083c120e6e4b2a95
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72649296"
---
# <a name="install-net-compiler-platform-code-analyzers"></a>Installare gli analizzatori di codice .NET Compiler Platform

Visual Studio include un core set di analizzatori di .NET Compiler Platform (*Roslyn*). Questi analizzatori sono sempre attivati. È possibile installare altri analizzatori come pacchetti NuGet o come estensioni di Visual Studio nei file *VSIX* .

## <a name="to-install-nuget-analyzer-packages"></a>Per installare i pacchetti di NuGet Analyzer

1. Trovare il pacchetto dell'analizzatore che si vuole installare in www.nuget.org.

   È possibile, ad esempio, [installare gli analizzatori FxCop Microsoft](install-fxcop-analyzers.md#nuget-package) per verificare la presenza di problemi di sicurezza e prestazioni, tra gli altri. In alternativa, installare [StyleCopAnalyzers](https://www.nuget.org/packages/stylecop.analyzers/) per cercare problemi di stile nella codebase.

2. Installare il pacchetto in Visual Studio, usando la [console di gestione pacchetti](/nuget/quickstart/install-and-use-a-package-in-visual-studio#package-manager-console) o l' [interfaccia utente di gestione pacchetti](/nuget/quickstart/install-and-use-a-package-in-visual-studio#package-manager-console).

   > [!NOTE]
   > La pagina www.nuget.org per ogni pacchetto dell'analizzatore Mostra il comando da incollare nella **console di gestione pacchetti**. È anche disponibile un pulsante utile per copiare il testo negli Appunti.

   Gli assembly dell'analizzatore vengono installati e visualizzati in **Esplora soluzioni** in **riferimenti** > **analizzatori**.

## <a name="to-install-vsix-analyzers"></a>Per installare gli analizzatori VSIX

::: moniker range="vs-2017"

1. In Visual Studio selezionare **strumenti** > **estensioni e aggiornamenti**.

   Verrà visualizzata la finestra di dialogo **Estensioni e aggiornamenti**.

   > [!NOTE]
   > In alternativa, è possibile trovare e scaricare l'estensione dell'analizzatore direttamente da [Visual Studio Marketplace](https://marketplace.visualstudio.com).

::: moniker-end

::: moniker range=">=vs-2019"

1. In Visual Studio selezionare **estensioni** > **Gestisci estensioni**.

   Verrà visualizzata la finestra di dialogo **Gestisci estensioni** .

   > [!NOTE]
   > In alternativa, è possibile trovare e scaricare l'estensione dell'analizzatore direttamente da [Visual Studio Marketplace](https://marketplace.visualstudio.com).

::: moniker-end

2. Espandere **online** nel riquadro sinistro e quindi selezionare **Visual Studio Marketplace**.

3. Nella casella di ricerca digitare il nome dell'estensione dell'analizzatore che si desidera installare. È possibile, ad esempio, [installare gli analizzatori FxCop Microsoft](install-fxcop-analyzers.md#vsix) per verificare la presenza di problemi di sicurezza e prestazioni, tra gli altri.

4. Selezionare **download**.

   Viene scaricata l'estensione.

5. Selezionare **OK** per chiudere la finestra di dialogo e quindi chiudere tutte le istanze di Visual Studio per avviare il **programma di installazione VSIX**.

   Verrà visualizzata la finestra di dialogo **programma di installazione VSIX** .

   ![Programma di installazione VSIX per analisi codice Microsoft](media/vsix-installer-code-analysis.png)

6. Selezionare **modifica** per avviare l'installazione.

7. Dopo un minuto o due, l'installazione viene completata. Selezionare **Chiudi**.

8. Aprire di nuovo Visual Studio.

::: moniker range="vs-2017"

Se si vuole verificare se l'estensione è installata, selezionare **strumenti** > **estensioni e aggiornamenti**. Nella finestra di dialogo **estensioni e aggiornamenti** selezionare la categoria **installato** a sinistra e quindi cercare l'estensione in base al nome.

::: moniker-end

::: moniker range=">=vs-2019"

Se si vuole verificare se l'estensione è installata, selezionare **estensioni** > **Gestisci estensioni**. Nella finestra di dialogo **Gestisci estensioni** selezionare la categoria **installato** a sinistra e quindi cercare l'estensione in base al nome.

::: moniker-end

## <a name="next-steps"></a>Passaggi successivi

> [!div class="nextstepaction"]
> [Usare gli analizzatori del codice in Visual Studio](../code-quality/use-roslyn-analyzers.md)

## <a name="see-also"></a>Vedere anche

- [Panoramica degli analizzatori di codice in Visual Studio](../code-quality/roslyn-analyzers-overview.md)
- [Installare gli analizzatori FxCop](../code-quality/install-fxcop-analyzers.md)
