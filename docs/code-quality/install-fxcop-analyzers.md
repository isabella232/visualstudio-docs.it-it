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
ms.openlocfilehash: b5cb0fa5985cbc923713330289d7f83ed1fd954e
ms.sourcegitcommit: 209ed0fcbb8daa1685e8d6b9a97f3857a4ce1152
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/16/2019
ms.locfileid: "69551100"
---
# <a name="install-fxcop-analyzers-in-visual-studio"></a>Installare gli analizzatori FxCop in Visual Studio

Microsoft ha creato un set di analizzatori, denominato [Microsoft. CodeAnalysis. FxCopAnalyzers](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers), che contiene le regole "FxCop" più importanti dell'analisi legacy. Questi analizzatori controllano il codice per i problemi di sicurezza, prestazioni e progettazione, tra gli altri.

È possibile installare questi analizzatori FxCop come pacchetto NuGet o come estensione VSIX in Visual Studio. Per informazioni sui vantaggi e gli svantaggi di ognuno di essi [, vedere confronto tra pacchetti NuGet e Estensione](roslyn-analyzers-overview.md#nuget-package-versus-vsix-extension)VSIX.

## <a name="to-install-fxcop-analyzers-as-a-nuget-package"></a>Per installare gli analizzatori FxCop come pacchetto NuGet

1. [Determinare la versione del pacchetto](#fxcopanalyzers-package-versions) dell'analizzatore da installare, in base alla versione di Visual Studio.

2. Installare il pacchetto in Visual Studio, usando la [console di gestione pacchetti](/nuget/quickstart/install-and-use-a-package-in-visual-studio#package-manager-console) o l' [interfaccia utente di gestione pacchetti](/nuget/quickstart/install-and-use-a-package-in-visual-studio#package-manager-console).

   > [!NOTE]
   > La pagina nuget.org per ogni pacchetto dell'analizzatore Mostra il comando da incollare nella **console di gestione pacchetti**. È anche disponibile un pulsante utile per copiare il testo negli Appunti.
   >
   > ![Pagina NuGet.org che Visualizza il comando console di gestione pacchetti](media/nuget-package-manager-command.png)

   Gli assembly dell'analizzatore sono installati e vengono visualizzati in **Esplora soluzioni** in **riferimenti** > **analizzatori**.

   ![Nodo analizzatori in Esplora soluzioni](media/solution-explorer-analyzers-node.png)

### <a name="fxcopanalyzers-package-versions"></a>Versioni del pacchetto FxCopAnalyzers

Usare le linee guida seguenti per determinare la versione del pacchetto di analizzatori FxCop da installare per la versione di Visual Studio:

| Versione di Visual Studio | Versione del pacchetto dell'analizzatore FxCop |
| - | - |
| Visual Studio 2019 (tutte le versioni)<br />Visual Studio 2017 versione 15,8 e successive | [2.9.3](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/2.9.3) |
| Visual Studio 2017 versione 15,5 a 15,7 | [2.6.3](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/2.6.3) |
| Visual Studio 2017 versione 15,3 a 15,4 | [2.3.0-beta1](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/2.3.0-beta1) |
| Visual Studio 2017 versione 15,0 a 15,2 | [2.0.0-beta2](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/2.0.0-beta2) |
| Visual Studio 2015 Update 2 e 3 | [1.2.0-beta2](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/1.2.0-beta2) |
| Visual Studio 2015 Update 1 | [1.1.0](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/1.1.0) |
| Visual Studio 2015 RTW | [1.0.1](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/1.0.1) |

## <a name="to-install-fxcop-analyzers-as-a-vsix"></a>Per installare gli analizzatori FxCop come VSIX

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
- [Usare gli analizzatori di codice in Visual Studio](../code-quality/use-roslyn-analyzers.md)
- [Eseguire la migrazione dall'analisi legacy agli analizzatori di codice](../code-quality/fxcop-analyzers.yml)
