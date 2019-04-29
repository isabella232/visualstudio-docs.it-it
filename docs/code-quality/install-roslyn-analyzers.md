---
title: Installare gli analizzatori Roslyn
ms.date: 08/03/2018
ms.topic: conceptual
helpviewer_keywords:
- code analysis, managed code
- analyzers
- Roslyn analyzers
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 1afeb6f75648ce2ab1687fa9262ab28b658b0d70
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62820822"
---
# <a name="install-net-compiler-platform-analyzers"></a>Installare gli analizzatori .NET Compiler Platform

Visual Studio include un set di base di .NET Compiler Platform (*Roslyn*) gli analizzatori. Gli analizzatori sono sempre attivati. È possibile installare altri analizzatori come pacchetti NuGet o come estensioni di Visual Studio in *VSIX* file.

## <a name="to-install-nuget-analyzer-packages"></a>Per installare i pacchetti dell'analizzatore NuGet

1. Trovare il pacchetto dell'analizzatore che si desidera installare in www.nuget.org.

   Ad esempio, desideri [installare gli analizzatori Microsoft FxCop](install-fxcop-analyzers.md#to-install-fxcop-analyzers-as-a-nuget-package) per controllare il codice per i problemi di sicurezza e prestazioni, tra gli altri. In alternativa, installare [StyleCopAnalyzers](https://www.nuget.org/packages/stylecop.analyzers/) per individuare i problemi di stile nella codebase.

2. Installare il pacchetto in Visual Studio, usando il [Console di gestione pacchetti](/nuget/quickstart/install-and-use-a-package-in-visual-studio#package-manager-console) o nella [Package Manager UI](/nuget/quickstart/install-and-use-a-package-in-visual-studio#package-manager-console).

   > [!NOTE]
   > La pagina www.nuget.org per ogni pacchetto analyzer Mostra è il comando per incollare il **Console di gestione pacchetti**. È anche disponibile un pulsante utile per copiare il testo negli Appunti.

   Gli assembly dell'analizzatore sono installati e visualizzati **Esplora soluzioni** sotto **riferimenti** > **analizzatori**.

## <a name="to-install-vsix-analyzers"></a>Per installare gli analizzatori VSIX

::: moniker range="vs-2017"

1. In Visual Studio, selezionare **degli strumenti** > **estensioni e aggiornamenti**.

   Verrà visualizzata la finestra di dialogo **Estensioni e aggiornamenti**.

   > [!NOTE]
   > In alternativa, è possibile trovare e scaricare l'estensione di Analizzatore direttamente dal [Visual Studio Marketplace](https://marketplace.visualstudio.com).

::: moniker-end

::: moniker range=">=vs-2019"

1. In Visual Studio, selezionare **Extensions** > **Gestisci estensioni**.

   Il **gestire le estensioni** verrà visualizzata la finestra di dialogo.

   > [!NOTE]
   > In alternativa, è possibile trovare e scaricare l'estensione di Analizzatore direttamente dal [Visual Studio Marketplace](https://marketplace.visualstudio.com).

::: moniker-end

2. Espandere **Online** nel riquadro a sinistra e quindi selezionare **Visual Studio Marketplace**.

3. Nella casella di ricerca, digitare il nome dell'estensione dell'analizzatore che si desidera installare. Ad esempio, desideri [installare gli analizzatori Microsoft FxCop](install-fxcop-analyzers.md#to-install-fxcop-analyzers-as-a-vsix) per controllare il codice per i problemi di sicurezza e prestazioni, tra gli altri.

4. Selezionare **scaricare**.

   L'estensione viene scaricata.

5. Selezionare **OK** per chiudere la finestra di dialogo, quindi chiudere tutte le istanze di Visual Studio per avviare la **programma di installazione VSIX**.

   Il **programma di installazione VSIX** verrà visualizzata la finestra di dialogo.

   ![Programma di installazione VSIX per l'analisi codice Microsoft](media/vsix-installer-code-analysis.png)

6. Selezionare **Modify** per avviare l'installazione.

7. Dopo un minuto o due, il completamento dell'installazione. Selezionare **Chiudi**.

8. Aprire di nuovo Visual Studio.

::: moniker range="vs-2017"

Se si vuole verificare se l'estensione è installata, selezionare **degli strumenti** > **estensioni e aggiornamenti**. Nel **estensioni e aggiornamenti** finestra di dialogo, seleziona la **installato** categorie a sinistra e quindi cercare l'estensione in base al nome.

::: moniker-end

::: moniker range=">=vs-2019"

Se si vuole verificare se l'estensione è installata, selezionare **Extensions** > **Gestisci estensioni**. Nel **gestire le estensioni** finestra di dialogo, seleziona la **installato** categorie a sinistra e quindi cercare l'estensione in base al nome.

::: moniker-end

## <a name="next-steps"></a>Passaggi successivi

> [!div class="nextstepaction"]
> [Usare gli analizzatori di Roslyn in Visual Studio](../code-quality/use-roslyn-analyzers.md)

## <a name="see-also"></a>Vedere anche

- [Panoramica degli analizzatori di Roslyn in Visual Studio](../code-quality/roslyn-analyzers-overview.md)
- [Installare gli analizzatori FxCop](../code-quality/install-fxcop-analyzers.md)