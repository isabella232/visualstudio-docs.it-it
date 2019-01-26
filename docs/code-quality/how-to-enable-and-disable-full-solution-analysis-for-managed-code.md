---
title: "Procedura: Abilitare e disabilitare l'analisi della soluzione completa per il codice gestito"
ms.date: 03/23/2018
ms.topic: conceptual
helpviewer_keywords:
- full solution analysis
author: gewarren
ms.author: gewarren
manager: jillfra
ms.prod: visual-studio-dev15
ms.workload:
- dotnet
ms.openlocfilehash: ffda04828789a591c0e6dca35ef391fe6b8556d7
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "55035472"
---
# <a name="how-to-enable-and-disable-full-solution-analysis-for-managed-code"></a>Procedura: Abilitare e disabilitare l'analisi della soluzione completa per il codice gestito

*Analisi della soluzione completa* è una funzionalità di Visual Studio che consente di vedere i problemi di analisi del codice solo in Visual aprire C# o file di Visual Basic nella soluzione, o anche nei file di codice che sono chiusi. Per impostazione predefinita, sono l'analisi della soluzione completa *abilitate* per Visual Basic, e *disabilitato* per oggetto visivo C#.

Può essere utile visualizzare tutti i problemi in tutti i file, ma può anche essere fonte di distrazione. Rallenta Visual Studio se la soluzione è molto grande o contiene molti file. Per limitare il numero di problemi visualizzati e migliorare le prestazioni di Visual Studio, è possibile disabilitare l'analisi della soluzione completa. Se necessario, è possibile riabilitare facilmente questa funzionalità.

## <a name="to-toggle-full-solution-analysis"></a>Per attivare o disattivare analisi della soluzione completa

1. Per aprire la **le opzioni** finestra di dialogo, nella barra dei menu in Visual Studio scegliere **Tools** > **opzioni**.

1. Nel **opzioni** finestra di dialogo, scegliere **Editor di testo**  >  **C#** oppure **base**  >  **Advanced**.

1. Selezionare il **Abilita analisi della soluzione completa** casella di controllo per abilitare l'analisi della soluzione completa o deselezionare la casella per disabilitarla. Scegli **OK** dopo aver completato.

    ![Abilitare la casella di controllo analysis soluzione completa.](../code-quality/media/options-enable-full-solution-analysis.png)

## <a name="results-of-enabling-and-disabling-full-solution-analysis"></a>Risultati di abilitazione e disabilitazione di analisi della soluzione completa

Nello screenshot seguente, è possibile visualizzare i risultati quando sono abilitata l'analisi della soluzione completa. Tutti gli errori e problemi di analisi del codice nel *tutti* dei file nella soluzione viene visualizzata, indipendentemente dal fatto che i file sono aperti.

![Analisi della soluzione completa abilitata.](../code-quality/media/fsa_enabled.png)

Lo screenshot seguente mostra i risultati dalla stessa soluzione dopo la disabilitazione di analisi della soluzione completa. Vengono visualizzati solo gli errori e problemi di analisi del codice nei file di soluzione aperta nel **elenco errori**.

![Analisi della soluzione completa disabilitato.](../code-quality/media/fsa_disabled.png)

## <a name="automatically-disable-full-solution-analysis"></a>Disabilitare automaticamente l'analisi della soluzione completa

Se Visual Studio rileva che 200 MB o inferiore di memoria di sistema è disponibile a esso, viene disabilitata automaticamente analisi della soluzione completa (e alcune altre funzionalità) se è abilitato. In questo caso, viene visualizzato un avviso che informa che alcune funzionalità è disattivata da Visual Studio. Un pulsante consente di riattivare l'analisi della soluzione completa se si desidera.

![Testo dell'avviso la sospensione di analisi della soluzione completa](../code-quality/media/fsa_alert.png)