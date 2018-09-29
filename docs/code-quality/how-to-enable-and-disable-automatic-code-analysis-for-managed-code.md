---
title: "Procedura: abilitare e disabilitare l'analisi automatica del codice gestito"
ms.date: 09/28/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 3113143b07ccb6f765cd0cf1735b34be6e952c72
ms.sourcegitcommit: 6672a1e9d135d7e5cca3cceea07c6fe5a0871475
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/28/2018
ms.locfileid: "47443545"
---
# <a name="how-to-enable-and-disable-automatic-code-analysis-for-managed-code"></a>Procedura: abilitare e disabilitare l'analisi automatica del codice per il codice gestito

È possibile configurare l'analisi del codice da eseguire dopo ogni compilazione di un progetto di codice gestito. È possibile impostare le proprietà di analisi per ogni configurazione di compilazione codice diverso, ad esempio, eseguire il debug e release.

## <a name="to-enable-or-disable-automatic-code-analysis"></a>Per abilitare o disabilitare l'analisi del codice automatica

1. Nelle **Esplora soluzioni**, fare clic sul progetto e quindi scegliere **proprietà**.

1. Nella finestra di dialogo proprietà del progetto, scegliere il **analisi del codice** scheda.

1. Specificare il tipo di compilazione nella **Configuration** e la piattaforma di destinazione **piattaforma**.

1. Per abilitare o disabilitare l'analisi automatica del codice, selezionare o deselezionare i **Abilita analisi codice su compilazione** casella di controllo.

> [!NOTE]
> Il **Abilita analisi codice su compilazione** casella di controllo influisce solo sulle analisi statica del codice. Non influisce sul [analizzatori del codice Roslyn](roslyn-analyzers-overview.md), che viene eseguito sempre in fase di compilazione se sono stati installati come pacchetto NuGet. Se si desidera cancellare gli errori dell'analizzatore dal **elenco errori**, è possibile eliminare tutte le violazioni correnti scegliendo **Analizza** > **Esegui analisi del codice e non visualizzare attivo Problemi** nella barra dei menu. Per altre informazioni, vedere [escludere le violazioni](use-roslyn-analyzers.md#suppress-violations).
