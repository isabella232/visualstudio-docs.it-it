---
title: Installare gli analizzatori FXCop
ms.date: 08/03/2018
ms.topic: conceptual
helpviewer_keywords:
- fxcop analyzers
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: fec188ba61a7e4d3f27caad03f0a5d32b6758a32
ms.sourcegitcommit: 39a04f42d23597b70053686d7e927ba78f38a9a8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/05/2019
ms.locfileid: "71974998"
---
# <a name="install-fxcop-analyzers-in-visual-studio"></a>Installare gli analizzatori FxCop in Visual Studio

Microsoft ha creato un set di analizzatori, denominato [Microsoft. CodeAnalysis. FxCopAnalyzers](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers), che contiene le regole "FxCop" più importanti dell'analisi legacy. Questi analizzatori controllano il codice per i problemi di sicurezza, prestazioni e progettazione, tra gli altri.

È possibile installare questi analizzatori FxCop come pacchetto NuGet o come estensione VSIX in Visual Studio. Per informazioni sui vantaggi e gli svantaggi di ognuno di essi, vedere [NuGet package VS. Estensione VSIX @ no__t-0.

## <a name="nuget-package"></a>Pacchetto NuGet

È possibile installare il pacchetto NuGet [Microsoft. CodeAnalysis. FxCopAnalyzers](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers) direttamente dalla pagina delle proprietà di analisi del codice del progetto:

1. Fare clic con il pulsante destro del mouse sul nodo del progetto in **Esplora soluzioni**, scegliere **Proprietà**, quindi selezionare la scheda **analisi codice** .

   ![Installare il pacchetto degli analizzatori FxCop dalla pagina delle proprietà in Visual Studio](media/install-fxcop-properties-page.png)

2. Selezionare **Installa**.

   Visual Studio installa la versione più recente del pacchetto Microsoft. codeanalyzers. FxCopAnalyzers. Gli assembly vengono visualizzati in **Esplora soluzioni** in **riferimenti** > **analizzatori**.

   ![Nodo analizzatori in Esplora soluzioni](media/solution-explorer-analyzers-node.png)

### <a name="custom-installation"></a>Installazione personalizzata

Per l'installazione personalizzata, ad esempio per specificare una versione diversa del pacchetto, selezionare il pulsante con i puntini di sospensione (...) nella pagina delle proprietà di analisi del codice del progetto. Questo pulsante apre Gestione pacchetti NuGet con "Microsoft. CodeAnalysis. FxCopAnalyzers" come stringa di ricerca.

![Installare il pacchetto degli analizzatori FxCop personalizzati dalla pagina delle proprietà in Visual Studio](media/install-fxcop-properties-page-ellipsis.png)

> [!TIP]
> Determinare la [versione del pacchetto dell'analizzatore](#fxcopanalyzers-package-versions) da installare, in base alla versione di Visual Studio. È anche possibile installare il pacchetto dall' [interfaccia utente di gestione pacchetti](/nuget/quickstart/install-and-use-a-package-in-visual-studio#package-manager-console).

### <a name="fxcopanalyzers-package-versions"></a>Versioni del pacchetto FxCopAnalyzers

Usare le linee guida seguenti per determinare la versione del pacchetto di analizzatori FxCop da installare per la versione di Visual Studio:

| Versione di Visual Studio | Versione del pacchetto dell'analizzatore FxCop |
| - | - |
| Visual Studio 2019 (tutte le versioni)<br />Visual Studio 2017 versione 15,8 e successive | [latest](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/) |
| Visual Studio 2017 versione 15,5 a 15,7 | [2.6.3](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/2.6.3) |
| Visual Studio 2017 versione 15,3 a 15,4 | [2.3.0-beta1](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/2.3.0-beta1) |
| Visual Studio 2017 versione 15,0 a 15,2 | [2.0.0-beta2](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/2.0.0-beta2) |
| Visual Studio 2015 Update 2 e 3 | [1.2.0-beta2](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/1.2.0-beta2) |
| Visual Studio 2015 Update 1 | [1.1.0](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/1.1.0) |
| Visual Studio 2015 RTW | [1.0.1](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/1.0.1) |

## <a name="vsix"></a>VSIX

::: moniker range="vs-2017"

In Visual Studio 2017 versione 15,5 e versioni successive è possibile installare l'estensione [Microsoft Code Analysis 2017](https://marketplace.visualstudio.com/items?itemName=VisualStudioPlatformTeam.MicrosoftCodeAnalysis2017) che contiene tutti gli analizzatori FxCop per i progetti gestiti.

1. In Visual Studio selezionare **strumenti** > **estensioni e aggiornamenti**.

   Verrà visualizzata la finestra di dialogo **Estensioni e aggiornamenti**.

   > [!NOTE]
   > In alternativa, scaricare l'estensione direttamente da [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=VisualStudioPlatformTeam.MicrosoftCodeAnalysis2017).

2. Espandere **online** nel riquadro sinistro e quindi selezionare **Visual Studio Marketplace**.

3. Nella casella di ricerca digitare "analisi codice" e cercare l'estensione **Microsoft code analysis 2017** .

   ![Estensione Microsoft Code Analysis 2017](media/extensions-and-updates-code-analysis.png)

::: moniker-end

::: moniker range=">=vs-2019"

L'estensione [Microsoft Code Analysis 2019](https://marketplace.visualstudio.com/items?itemName=VisualStudioPlatformTeam.MicrosoftCodeAnalysis2019) contiene tutti gli analizzatori FxCop per i progetti gestiti. Per installare questa estensione:

1. In Visual Studio selezionare **estensioni** > **Gestisci estensioni**.

   Verrà visualizzata la finestra di dialogo **Gestisci estensioni** .

   > [!NOTE]
   > In alternativa, scaricare l'estensione direttamente da [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=VisualStudioPlatformTeam.MicrosoftCodeAnalysis2019).

2. Espandere **online** nel riquadro sinistro e quindi selezionare **Visual Studio Marketplace**.

3. Nella casella di ricerca digitare "analisi codice" e cercare l'estensione **Microsoft code analysis 2019** .

   ![Estensione Microsoft Code Analysis 2019](media/manage-extensions-code-analysis.png)

::: moniker-end

4. Selezionare **download**.

   Viene scaricata l'estensione.

5. Selezionare **OK** per chiudere la finestra di dialogo e quindi chiudere tutte le istanze di Visual Studio per avviare il **programma di installazione VSIX**.

   Verrà visualizzata la finestra di dialogo **programma di installazione VSIX** .

   ::: moniker range="vs-2017"

   ![Programma di installazione VSIX per analisi codice Microsoft](media/vsix-installer-code-analysis.png)

   ::: moniker-end

6. Selezionare **modifica** per avviare l'installazione.

   Dopo un minuto o due, l'installazione viene completata.

7. Selezionare **Chiudi**, quindi aprire di nuovo Visual Studio.

::: moniker range="vs-2017"

Se si vuole verificare se l'estensione è installata, selezionare **strumenti** > **estensioni e aggiornamenti**. Nella finestra di dialogo **estensioni e aggiornamenti** selezionare la categoria **installato** a sinistra e quindi cercare l'estensione in base al nome.

::: moniker-end

::: moniker range=">=vs-2019"

Se si vuole verificare se l'estensione è installata, selezionare **estensioni** > **Gestisci estensioni**. Nella finestra di dialogo **Gestisci estensioni** selezionare la categoria **installato** a sinistra e quindi cercare l'estensione in base al nome.

::: moniker-end

## <a name="see-also"></a>Vedere anche

- [Panoramica degli analizzatori di codice in Visual Studio](../code-quality/roslyn-analyzers-overview.md)
- [Usare gli analizzatori del codice in Visual Studio](../code-quality/use-roslyn-analyzers.md)
- [Eseguire la migrazione dall'analisi legacy agli analizzatori di codice](../code-quality/fxcop-analyzers.yml)
