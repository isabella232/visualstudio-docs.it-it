---
title: Disabilitare l'analisi del codice legacy
ms.date: 10/04/2019
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: c00a66a856dccb0ccb488937b935d9150ffc0266
ms.sourcegitcommit: 39a04f42d23597b70053686d7e927ba78f38a9a8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/05/2019
ms.locfileid: "71975091"
---
# <a name="how-to-enable-and-disable-binary-code-analysis-for-managed-code"></a>Procedura: Abilitare e disabilitare l'analisi del codice binario per il codice gestito

È possibile configurare l'analisi del codice legacy (analisi binaria) per l'esecuzione dopo ogni compilazione di un progetto di codice gestito. È anche possibile avere impostazioni diverse per ogni configurazione della build, ad esempio debug e release.

> [!NOTE]
> L'analisi legacy non è disponibile per i tipi di progetto più recenti, ad esempio .NET Core e app .NET Standard. Questi progetti utilizzano gli [analizzatori di codice basati su .NET Compiler Platform](roslyn-analyzers-overview.md) per analizzare il codice, sia in tempo reale che in fase di compilazione. Per informazioni sulla disabilitazione dell'analisi del codice sorgente in questi progetti, vedere [come disabilitare l'analisi del codice sorgente](disable-code-analysis.md).

Per abilitare o disabilitare l'analisi del codice legacy:

1. In **Esplora soluzioni**fare clic con il pulsante destro del mouse sul progetto, quindi scegliere **Proprietà**.

2. Nella finestra di dialogo Proprietà del progetto scegliere la scheda **analisi codice** .

3. Specificare il tipo di compilazione nella **configurazione** e nella piattaforma di **destinazione.** (Solo per i progetti Non-.NET Core/.NET standard).

::: moniker range="vs-2017"

4. Per abilitare o disabilitare l'analisi automatica del codice, selezionare o deselezionare la casella di controllo **Abilita analisi codice su compilazione** .

::: moniker-end

::: moniker range=">=vs-2019"

4. Per abilitare o disabilitare l'analisi automatica del codice, selezionare o deselezionare la casella di controllo **Esegui su compilazione** nella sezione **analizzatori binari** .

   ![Eseguire l'analisi del codice binario sull'opzione di compilazione in Visual Studio](media/run-on-build-binary-analyzers.png)

::: moniker-end

> [!NOTE]
> La disabilitazione dell'analisi del codice binario sulla compilazione non influisce sugli [analizzatori di codice basati su .NET Compiler Platform](roslyn-analyzers-overview.md), che vengono sempre eseguiti in fase di compilazione se sono stati installati come pacchetto NuGet. Per informazioni sulla disabilitazione dell'analisi da questi analizzatori, vedere [come disabilitare l'analisi del codice sorgente](disable-code-analysis.md).