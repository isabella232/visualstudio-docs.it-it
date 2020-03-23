---
title: Installare gli analizzatori FXCop
ms.date: 08/03/2018
ms.topic: conceptual
helpviewer_keywords:
- fxcop analyzers
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 1d734ea4d87dc5d1b8f2ca7f1a1891a4cf7d512b
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/18/2020
ms.locfileid: "79508771"
---
# <a name="install-fxcop-analyzers-in-visual-studio"></a>Installare analizzatori FxCop in Visual StudioInstall FxCop analyzers in Visual Studio

Microsoft ha creato un set di analizzatori, denominato [Microsoft.CodeAnalysis.FxCopAnalyzers](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers), che contiene le regole "FxCop" più importanti dall'analisi legacy. Questi analizzatori controllano il codice per problemi di sicurezza, prestazioni e progettazione, tra gli altri.

È possibile installare questi analizzatori FxCop come un pacchetto NuGet o come estensione VSIX in Visual Studio.You can install these FxCop analyzers either as a NuGet package or as a VSIX extension to Visual Studio. Per informazioni sui pro e i contro di ognuno, vedere [Pacchetto NuGet e estensione VSIX](roslyn-analyzers-overview.md#nuget-package-versus-vsix-extension).

## <a name="nuget-package"></a>Pacchetto NuGet

::: moniker range=">=vs-2019"

In Visual Studio 2019 versione 16.3 e successive, è possibile installare il pacchetto Microsoft.CodeAnalysis.FxCopAnalyzers NuGet direttamente dalla pagina delle proprietà di analisi del codice del progetto:In Visual Studio 2019 version 16.3 and later, you can install the [Microsoft.CodeAnalysis.FxCopAnalyzers](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers) NuGet package directly from the project's Code Analysis properties page:

1. Fare clic con il pulsante destro del mouse sul nodo del progetto in **Esplora soluzioni,** scegliere **Proprietà**, quindi selezionare la scheda **Analisi codice.**

   ![Installare il pacchetto analizzatori FxCop dalla pagina delle proprietà in Visual StudioInstall FxCop analyzers package from properties page in Visual Studio](media/install-fxcop-properties-page.png)

2. Selezionare **Installa**.

   Visual Studio installa la versione più recente del pacchetto Microsoft.CodeAnalysis.FxCopAnalyzers. Gli assembly vengono visualizzati in **Esplora soluzioni** in**Analizzatori** **riferimenti** > .

   ![Nodo Analizzatori in Esplora soluzioni](media/solution-explorer-analyzers-node.png)

Se si usa una versione precedente di Visual Studio 2019, installare il pacchetto utilizzando la [Console di gestione pacchetti](/nuget/quickstart/install-and-use-a-package-in-visual-studio#package-manager-console) o l'interfaccia utente di Gestione [pacchetti.](/nuget/quickstart/install-and-use-a-package-in-visual-studio#package-manager-console)

::: moniker-end

::: moniker range="vs-2017"

1. Determinare la versione del [pacchetto dell'analizzatore](#fxcopanalyzers-package-versions) da installare, in base alla versione di Visual Studio.Determine which analyzer package version to install, based on your version of Visual Studio.

2. Installare il pacchetto in Visual Studio utilizzando la [Console di gestione pacchetti](/nuget/quickstart/install-and-use-a-package-in-visual-studio#package-manager-console) o l'interfaccia utente di Gestione [pacchetti.](/nuget/quickstart/install-and-use-a-package-in-visual-studio#package-manager-console)

   > [!NOTE]
   > La pagina nuget.org per ogni pacchetto analizzatore mostra il comando da incollare nella console di **Gestione pacchetti.** C'è anche un comodo pulsante per copiare il testo negli appunti.
   >
   > ![NuGet.org pagina con il comando Console di Gestione pacchetti](media/nuget-package-manager-command.png)

   Gli assembly dell'analizzatore vengono installati e vengono visualizzati in **Esplora soluzioni** in **Analizzatori** **riferimenti** > .

::: moniker-end

### <a name="custom-installation"></a>Installazione personalizzata

Per l'installazione personalizzata, ad esempio per specificare una versione diversa del pacchetto, selezionare il pulsante con i puntini di sospensione (...) nella pagina delle proprietà dell'analisi del codice del progetto. Questo pulsante consente di aprire gestione pacchetti NuGet con "Microsoft.CodeAnalysis.FxCopAnalyzers" come stringa di ricerca.

![Installare il pacchetto di analizzatori FxCop personalizzati dalla pagina delle proprietà in Visual StudioInstall custom FxCop analyzers package from properties page in Visual Studio](media/install-fxcop-properties-page-ellipsis.png)

> [!TIP]
> Determinare la versione del [pacchetto dell'analizzatore](#fxcopanalyzers-package-versions) da installare, in base alla versione di Visual Studio.Determine which analyzer package version to install, based on your version of Visual Studio. È anche possibile installare il pacchetto dall'interfaccia utente di [Gestione pacchetti.](/nuget/quickstart/install-and-use-a-package-in-visual-studio#package-manager-console)

### <a name="fxcopanalyzers-package-versions"></a>Versioni del pacchetto FxCopAnalyzersFxCopAnalyzers package versions

Usare le linee guida seguenti per determinare la versione del pacchetto fxCop degli analizzatori da installare per la versione di Visual Studio in uso:

| Versione di Visual Studio | Versione del pacchetto analizzatore FxCop |
| - | - |
| Visual Studio 2019 (tutte le versioni)<br />Visual Studio 2017 versione 15.8 e successive | [Ultima](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/) |
| Visual Studio 2017 versione 15.5 a 15.7 | [2.6.3](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/2.6.3) |
| Visual Studio 2017 versione 15.3 a 15.4 | [2.3.0-beta1](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/2.3.0-beta1) |
| Visual Studio 2017 versione 15.0 a 15.2 | [2.0.0-beta2](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/2.0.0-beta2) |
| Aggiornamento di Visual Studio 2015 2 e 3 | [Versione 1.2.0-beta2](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/1.2.0-beta2) |
| Visual Studio 2015 Update 1 | [1.1.0](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/1.1.0) |
| Visual Studio 2015 RTW | [1.0.1](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/1.0.1) |

## <a name="vsix"></a>VSIX

::: moniker range="vs-2017"

In Visual Studio 2017 versione 15.5 e successive, è possibile installare l'estensione [Microsoft Code Analysis 2017](https://marketplace.visualstudio.com/items?itemName=VisualStudioPlatformTeam.MicrosoftCodeAnalysis2017) che contiene tutti gli analizzatori FxCop per i progetti gestiti.

1. In Visual Studio selezionare **Estensioni e aggiornamenti degli** **strumenti** > .

   Verrà visualizzata la finestra di dialogo **Estensioni e aggiornamenti**.

   > [!NOTE]
   > In alternativa, scaricare l'estensione direttamente da [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=VisualStudioPlatformTeam.MicrosoftCodeAnalysis2017).

2. Espandere **Online** nel riquadro sinistro e quindi selezionare **Visual Studio Marketplace**.

3. Nella casella di ricerca digitare "analisi del codice" e cercare l'estensione **Microsoft Code Analysis 2017.**

   ![Estensione Microsoft Code Analysis 2017](media/extensions-and-updates-code-analysis.png)

::: moniker-end

::: moniker range=">=vs-2019"

L'estensione [Microsoft Code Analysis 2019](https://marketplace.visualstudio.com/items?itemName=VisualStudioPlatformTeam.MicrosoftCodeAnalysis2019) contiene tutti gli analizzatori FxCop per i progetti gestiti. Per installare questa estensione:

1. In Visual Studio selezionare **Estensioni** > **per la gestione delle estensioni.**

   Verrà visualizzata la finestra di dialogo **Gestisci estensioni.**

   > [!NOTE]
   > In alternativa, scaricare l'estensione direttamente da [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=VisualStudioPlatformTeam.MicrosoftCodeAnalysis2019).

2. Espandere **Online** nel riquadro sinistro e quindi selezionare **Visual Studio Marketplace**.

3. Nella casella di ricerca digitare "analisi del codice" e cercare l'estensione **Microsoft Code Analysis 2019.**

   ![Estensione 2019 analisi del codice Microsoft](media/manage-extensions-code-analysis.png)

::: moniker-end

4. Selezionare **Download**.

   L'estensione viene scaricata.

5. Selezionare **OK** per chiudere la finestra di dialogo, quindi chiudere tutte le istanze di Visual Studio per avviare il **programma di installazione VSIX**.

   Verrà visualizzata la finestra di dialogo Programma di installazione **VSIX.**

   ::: moniker range="vs-2017"

   ![Programma di installazione VSIX per l'analisi del codice Microsoft](media/vsix-installer-code-analysis.png)

   ::: moniker-end

6. Selezionare **Modifica** per avviare l'installazione.

   Dopo un minuto o due, l'installazione viene completata.

7. Selezionare Chiudi , quindi aprire di nuovo Visual Studio.Select **Close**, then open Visual Studio again.

::: moniker range="vs-2017"

Se si desidera verificare se l'estensione è installata, selezionare**Estensioni e aggiornamenti degli** **strumenti** > . Nella finestra di dialogo **Estensioni e aggiornamenti** selezionare la categoria **Installato** a sinistra e quindi cercare l'estensione in base al nome.

::: moniker-end

::: moniker range=">=vs-2019"

Se si desidera verificare se l'estensione è installata, selezionare **Estensioni** > **Gestisci estensioni**. Nella finestra di dialogo **Gestisci estensioni** selezionare la categoria **Installato** a sinistra e quindi cercare l'estensione in base al nome.

::: moniker-end

## <a name="see-also"></a>Vedere anche

- [Panoramica degli analizzatori di codice in Visual StudioOverview of code analyzers in Visual Studio](../code-quality/roslyn-analyzers-overview.md)
- [Usare gli analizzatori del codice in Visual Studio](../code-quality/use-roslyn-analyzers.md)
- [Eseguire la migrazione dall'analisi legacy agli analizzatori di codiceMigrate from legacy analysis to code analyzers](../code-quality/migrate-from-legacy-analysis-to-fxcop-analyzers.md)
