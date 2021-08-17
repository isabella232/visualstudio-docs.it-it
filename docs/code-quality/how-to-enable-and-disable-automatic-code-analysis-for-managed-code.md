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
ms.openlocfilehash: ff4ffe458a059cb202af61054459b349e470cbe267e95e1844ea7cdaabf22d82
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121455381"
---
# <a name="how-to-enable-and-disable-binary-code-analysis-for-managed-code"></a>Procedura: Abilitare e disabilitare l'analisi del codice binario per il codice gestito

È possibile configurare l'analisi del codice legacy (analisi binaria) da eseguire dopo ogni compilazione di un progetto di codice gestito. È anche possibile avere impostazioni diverse per ogni configurazione di compilazione, ad esempio debug e versione.

> [!NOTE]
> L'analisi legacy non è disponibile per i tipi di progetto più recenti, ad esempio .NET Core e .NET Standard app. Questi progetti usano [.NET Compiler Platform analizzatori](roslyn-analyzers-overview.md) di codice basati su per analizzare il codice, sia in tempo reale che in fase di compilazione. Per informazioni sulla disabilitazione dell'analisi del codice sorgente in questi progetti, vedere [Come disabilitare l'analisi del codice sorgente.](disable-code-analysis.md)

Per abilitare o disabilitare l'analisi del codice legacy:

1. In **Esplora soluzioni** selezionare e tenere premuto (o fare clic con il pulsante destro del mouse) sul progetto e quindi scegliere **Proprietà**.

2. Nella finestra di dialogo delle proprietà per il progetto passare alla **scheda** Code Analysis.

3. Specificare il tipo di compilazione in **Configurazione** e la piattaforma di destinazione in **Piattaforma**. (Non-.NET solo progetti Core/.NET Standard.

::: moniker range="vs-2017"

4. Per abilitare o disabilitare l'analisi automatica del codice, selezionare o deselezionare la casella **di controllo Abilita** Code Analysis durante la compilazione.

::: moniker-end

::: moniker range=">=vs-2019"

4. Per abilitare o disabilitare l'analisi del codice automatica, selezionare o deselezionare la casella di **controllo** Esegui in compilazione nella **sezione Analizzatori binari.**

   ![Eseguire l'analisi del codice binario nell'opzione di compilazione in Visual Studio](media/run-on-build-binary-analyzers.png)

::: moniker-end

> [!NOTE]
> La disabilitazione dell'analisi del codice binario nella compilazione non influisce sugli analizzatori di codice basati su .NET Compiler Platform [,](roslyn-analyzers-overview.md)che vengono sempre eseguiti in fase di compilazione se sono stati installati come NuGet pacchetto. Per informazioni sulla disabilitazione dell'analisi da questi analizzatori, vedere [Come disabilitare l'analisi del codice sorgente.](disable-code-analysis.md)
