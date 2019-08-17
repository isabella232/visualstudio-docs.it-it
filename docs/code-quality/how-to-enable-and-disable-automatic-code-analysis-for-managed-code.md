---
title: Abilitare o disabilitare l'analisi del codice
ms.date: 10/25/2018
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: ec0a8a3f04830115d343fcef611cfbd338163395
ms.sourcegitcommit: 209ed0fcbb8daa1685e8d6b9a97f3857a4ce1152
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/16/2019
ms.locfileid: "69551043"
---
# <a name="how-to-enable-and-disable-automatic-code-analysis-for-managed-code"></a>Procedura: Abilitare e disabilitare l'analisi automatica del codice gestito

È possibile configurare l'analisi del codice (statica) per l'esecuzione dopo ogni compilazione di un progetto di codice gestito. È possibile impostare diverse proprietà di analisi del codice per ogni configurazione della build, ad esempio debug e release.

Questo articolo è valido solo per l'analisi legacy e non per l'analisi del codice in tempo reale usando gli analizzatori di [codice](roslyn-analyzers-overview.md).

## <a name="to-enable-or-disable-automatic-code-analysis"></a>Per abilitare o disabilitare l'analisi automatica del codice

1. In **Esplora soluzioni**fare clic con il pulsante destro del mouse sul progetto, quindi scegliere **Proprietà**.

1. Nella finestra di dialogo Proprietà del progetto scegliere la scheda **analisi codice** .

   > [!TIP]
   > I nuovi tipi di progetto, ad esempio le applicazioni .NET Core e .NET Standard, non dispongono di una scheda **analisi codice** . L'analisi legacy non è disponibile per questi tipi di progetto, ma è possibile ottenere l'analisi del codice in tempo reale usando [analizzatori di codice basati su .NET Compiler Platform](roslyn-analyzers-overview.md). Per escludere gli avvisi dagli analizzatori del codice, vedere la nota alla fine di questo articolo.

1. Specificare il tipo di compilazione nella **configurazione** e nella piattaforma didestinazione.

1. Per abilitare o disabilitare l'analisi automatica del codice, selezionare o deselezionare la casella di controllo **Abilita analisi codice su compilazione** .

> [!NOTE]
> La casella **di controllo Abilita analisi codice su compilazione** ha effetto solo sull'analisi legacy. Non influisce sull'analizzatore di [codice basato su .NET Compiler Platform](roslyn-analyzers-overview.md), che viene sempre eseguito in fase di compilazione se è stato installato come pacchetto NuGet. Se si desidera cancellare gli errori dell'analizzatore dalla **Elenco errori**, è possibile eliminare tutte le violazioni correnti scegliendo **analizza** > **Esegui analisi codice ed elimina problemi attivi** sulla barra dei menu. Per ulteriori informazioni, vedere la pagina relativa all' [eliminazione delle violazioni](use-roslyn-analyzers.md#suppress-violations).
