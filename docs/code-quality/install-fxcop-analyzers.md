---
title: Installare gli analizzatori FXCop
ms.date: 08/03/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- fxcop analyzers
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 117bf47fb5a733dfba02da98b5cae610a0aab5c7
ms.sourcegitcommit: 95aedf723c6be5272c3c5a2911cb2bdec50e2148
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/26/2018
ms.locfileid: "47228853"
---
# <a name="install-fxcop-analyzers-in-visual-studio"></a>Installare gli analizzatori FxCop in Visual Studio

Microsoft ha creato un set di analizzatori, chiamato [fxcopanalyzers](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers), che contiene le regole "FxCop" più importanti da analisi statica del codice, convertito in analizzatori di Roslyn. Gli analizzatori controllare il codice per la sicurezza, prestazioni e problemi di progettazione, tra gli altri.

È possibile installare gli analizzatori FxCop come pacchetto NuGet o come estensione VSIX a Visual Studio. Per altre informazioni sui vantaggi e svantaggi di ognuno, vedere [NuGet package vs. Estensione VSIX](roslyn-analyzers-overview.md#nuget-package-versus-vsix-extension).

## <a name="to-install-fxcop-analyzers-as-a-nuget-package"></a>Per installare gli analizzatori FxCop come pacchetto NuGet

1. [Determinare quale versione del pacchetto analizzatore](#fxcopanalyzers-package-versions) da installare, in base alla versione di Visual Studio.

1. Installare il pacchetto in Visual Studio, usando il [Console di gestione pacchetti](/nuget/quickstart/install-and-use-a-package-in-visual-studio#package-manager-console) o nella [Package Manager UI](/nuget/quickstart/install-and-use-a-package-in-visual-studio#package-manager-console).

   > [!NOTE]
   > Nella pagina di nuget.org per ogni pacchetto dell'analizzatore vengono visualizzati è il comando per incollare il **Console di gestione pacchetti**. È anche disponibile un pulsante utile per copiare il testo negli Appunti.
   >
   > ![Pagina di NuGet.org che mostra comando della Console di gestione pacchetti](media/nuget-package-manager-command.png)

   Gli assembly dell'analizzatore vengono installati e visualizzati nella **Esplora soluzioni** sotto **riferimenti** > **analizzatori**.

   ![Nodo di analizzatori in Esplora soluzioni](media/solution-explorer-analyzers-node.png)

### <a name="fxcopanalyzers-package-versions"></a>Versioni dei pacchetti FxCopAnalyzers

Usare le linee guida seguenti per determinare quale versione del pacchetto da installare per la versione di Visual Studio gli analizzatori FxCop:

|Versione di Visual Studio|Versione del pacchetto analizzatore FxCop|
|-|-|
|Visual Studio 2017 versione 15.5 e versioni successive|2.6.2, ad esempio https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/2.6.2|
|Visual Studio 2017 versione 15.3 per 15.4|2.3.0-Beta1, ad esempio https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/2.3.0-beta1|
|Visual Studio 2017 versione 15.0 per 15.2|2.0.0-Beta2, ad esempio https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/2.0.0-beta2|
|Visual Studio 2015 update 2 e 3|Versione 1.2.0-beta2, ad esempio https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/1.2.0-beta2|
|Visual Studio 2015 Update 1|Versione 1.1.0, ad esempio https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/1.1.|
|Visual Studio 2015 RTW|Versione 1.0.1, ad esempio https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/1.0.1|

## <a name="to-install-fxcop-analyzers-as-a-vsix"></a>Per installare gli analizzatori FxCop come un'estensione VSIX

In Visual Studio 2017 versione 15.5 e successive, è possibile installare il [Microsoft Code Analysis 2017](https://marketplace.visualstudio.com/items?itemName=VisualStudioPlatformTeam.MicrosoftCodeAnalysis2017) estensione che contiene tutti gli analizzatori FxCop per i progetti gestiti.

1. In Visual Studio, selezionare **degli strumenti** > **estensioni e aggiornamenti**.

   Verrà visualizzata la finestra di dialogo **Estensioni e aggiornamenti**.

   > [!NOTE]
   > In alternativa, scaricare l'estensione direttamente dal [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=VisualStudioPlatformTeam.MicrosoftCodeAnalysis2017).

1. Espandere **Online** nel riquadro a sinistra e quindi selezionare **Visual Studio Marketplace**.

1. Nella casella di ricerca, digitare "analisi del codice" e cercare il **Microsoft Code Analysis 2017** estensione.

   ![Estensione di analisi del codice di Microsoft](media/extensions-and-updates-code-analysis.png)

1. Selezionare **scaricare**.

   L'estensione viene scaricata.

1. Selezionare **OK** per chiudere la finestra di dialogo, quindi chiudere tutte le istanze di Visual Studio per avviare la **programma di installazione VSIX**.

   Il **programma di installazione VSIX** verrà visualizzata la finestra di dialogo.

   ![Programma di installazione VSIX per l'analisi codice Microsoft](media/vsix-installer-code-analysis.png)

1. Selezionare **Modify** per avviare l'installazione.

1. Dopo un minuto o due, il completamento dell'installazione. Selezionare **Chiudi**.

1. Aprire di nuovo Visual Studio.

Se si vuole verificare se l'estensione è installata, selezionare **degli strumenti** > **estensioni e aggiornamenti**. Nel **estensioni e aggiornamenti** finestra di dialogo, seleziona la **installato** categorie a sinistra e quindi cercare l'estensione in base al nome.

## <a name="see-also"></a>Vedere anche

- [Panoramica degli analizzatori di Roslyn in Visual Studio](../code-quality/roslyn-analyzers-overview.md)
- [Usare gli analizzatori di Roslyn in Visual Studio](../code-quality/use-roslyn-analyzers.md)
- [Eseguire la migrazione da FxCop per gli analizzatori di Roslyn](../code-quality/fxcop-analyzers.yml)