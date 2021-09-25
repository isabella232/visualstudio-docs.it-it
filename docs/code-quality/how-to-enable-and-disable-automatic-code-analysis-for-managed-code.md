---
title: Disabilitare l'analisi del codice legacy
ms.date: 10/04/2019
description: Informazioni su come attivare e disattivare l'analisi del codice binario in Visual Studio. Vedere come configurare questa funzionalità nei progetti di codice gestito.
ms.custom: SEO-VS-2020
ms.topic: how-to
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-code-analysis
ms.openlocfilehash: 785ac247f3c1343dc5133cc9d0e3c8c8b4d66a34
ms.sourcegitcommit: 8e74969ff61b609c89b3139434dff5a742c18ff4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/24/2021
ms.locfileid: "128427434"
---
# <a name="how-to-enable-and-disable-binary-code-analysis-for-managed-code"></a>Procedura: Abilitare e disabilitare l'analisi del codice binario per il codice gestito

È possibile configurare l'analisi del codice legacy (analisi binaria) da eseguire dopo ogni compilazione di un progetto di codice gestito. È anche possibile avere impostazioni diverse per ogni configurazione della build, ad esempio debug e rilascio.

> [!NOTE]
> L'analisi legacy non è disponibile per i tipi di progetto più recenti, ad esempio .NET Core e .NET Standard app. Questi progetti usano [.NET Compiler Platform analizzatori di codice](roslyn-analyzers-overview.md) basati su compilazione per analizzare il codice, sia in tempo reale che in fase di compilazione. Per informazioni sulla disabilitazione dell'analisi del codice sorgente in questi progetti, vedere [Come disabilitare l'analisi del codice sorgente.](disable-code-analysis.md)

Per abilitare o disabilitare l'analisi del codice legacy:

1. In **Esplora soluzioni** selezionare e tenere premuto (o fare clic con il pulsante destro del mouse) il progetto e quindi **scegliere Proprietà.**

2. Nella finestra di dialogo delle proprietà del progetto passare alla **scheda Code Analysis** proprietà.

3. Specificare il tipo di compilazione in **Configurazione** e la piattaforma di destinazione in **Piattaforma**. (Non-.NET solo progetti core/.NET Standard.

::: moniker range="vs-2017"

4. Per abilitare o disabilitare l'analisi automatica del codice, selezionare o deselezionare la **casella di controllo Code Analysis alla** compilazione .

::: moniker-end

::: moniker range=">=vs-2019"

4. Per abilitare o disabilitare l'analisi automatica del codice, selezionare o deselezionare la casella di **controllo** Esegui in fase di compilazione nella **sezione Analizzatori binari.**

   ![Eseguire l'analisi del codice binario sull'opzione di compilazione in Visual Studio](media/run-on-build-binary-analyzers.png)

5. Se è necessario disabilitare l'analisi legacy, verificare che l'analisi del codice legacy sia disabilitata nel file di progetto. Impostare la `RunCodeAnalysis` proprietà su false:

   `<RunCodeAnalysis>false</RunCodeAnalysis>`

::: moniker-end

> [!NOTE]
> La disabilitazione dell'analisi del codice binario in fase di compilazione non influisce sugli analizzatori di codice basati su [.NET Compiler Platform](roslyn-analyzers-overview.md), che vengono sempre eseguiti in fase di compilazione se sono stati installati come NuGet pacchetto. Per informazioni sulla disabilitazione dell'analisi da questi analizzatori, vedere [Come disabilitare l'analisi del codice sorgente.](disable-code-analysis.md)
