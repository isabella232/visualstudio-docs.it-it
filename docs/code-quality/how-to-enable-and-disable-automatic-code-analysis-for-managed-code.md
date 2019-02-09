---
title: Abilitare o disabilitare l'analisi codice
ms.date: 10/25/2018
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 4878c25021d87e91f6a575d11a876d7aac2455d5
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2019
ms.locfileid: "55918130"
---
# <a name="how-to-enable-and-disable-automatic-code-analysis-for-managed-code"></a>Procedura: Abilitare e disabilitare l'analisi automatica del codice per il codice gestito

È possibile configurare l'analisi del codice (statico) da eseguire dopo ogni compilazione di un progetto di codice gestito. È possibile impostare le proprietà di analisi per ogni configurazione di compilazione codice diverso, ad esempio, eseguire il debug e release.

Questo articolo riguarda analisi del codice solo come statico e l'analisi codice non in tempo reale usando [analizzatori di codice Roslyn](roslyn-analyzers-overview.md).

## <a name="to-enable-or-disable-automatic-code-analysis"></a>Per abilitare o disabilitare l'analisi del codice automatica

1. Nelle **Esplora soluzioni**, fare clic sul progetto e quindi scegliere **proprietà**.

1. Nella finestra di dialogo proprietà del progetto, scegliere il **analisi del codice** scheda.

   > [!TIP]
   > Tipi di progetto più recente, ad esempio le applicazioni .NET Core e .NET Standard non sono un **analisi del codice** scheda. Analisi statica del codice non sono disponibile per questi tipi di progetto, ma è comunque possibile ottenere usando analisi di codice in tempo reale [analizzatori di codice Roslyn](roslyn-analyzers-overview.md). Per eliminare gli avvisi generati dall'analisi del codice Roslyn, vedere la nota alla fine di questo articolo.

1. Specificare il tipo di compilazione nella **Configuration** e la piattaforma di destinazione **piattaforma**.

1. Per abilitare o disabilitare l'analisi automatica del codice, selezionare o deselezionare i **Abilita analisi codice su compilazione** casella di controllo.

> [!NOTE]
> Il **Abilita analisi codice su compilazione** casella di controllo influisce solo sulle analisi statica del codice. Non influisce sul [analizzatori del codice Roslyn](roslyn-analyzers-overview.md), che viene eseguito sempre in fase di compilazione se sono stati installati come pacchetto NuGet. Se si desidera cancellare gli errori dell'analizzatore dal **elenco errori**, è possibile eliminare tutte le violazioni correnti scegliendo **Analizza** > **Esegui analisi del codice e non visualizzare attivo Problemi** nella barra dei menu. Per altre informazioni, vedere [escludere le violazioni](use-roslyn-analyzers.md#suppress-violations).
