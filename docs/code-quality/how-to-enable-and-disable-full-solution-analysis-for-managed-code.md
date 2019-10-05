---
title: Abilitare & disabilitare l'analisi completa della soluzione per il codice gestito
ms.date: 03/23/2018
ms.topic: conceptual
helpviewer_keywords:
- full solution analysis
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 0b192b29190d530d22943e8ba2a396ae1fe9ad87
ms.sourcegitcommit: 39a04f42d23597b70053686d7e927ba78f38a9a8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/05/2019
ms.locfileid: "71975119"
---
# <a name="how-to-enable-and-disable-full-solution-analysis-for-managed-code"></a>Procedura: Abilitare e disabilitare l'analisi completa della soluzione per il codice gestito

L' *analisi completa della soluzione* indica che l'analisi del codice C# esamina tutti i file di o Visual Basic nella soluzione, indipendentemente dal fatto che siano aperti o meno nell'editor. Per impostazione predefinita, l'analisi della soluzione completa è *abilitata* per C#Visual Basic e *disabilitata* per.

Può essere utile per visualizzare tutti i problemi in tutti i file, ma può anche essere distrazione. Se la soluzione è molto grande o contiene molti file, rallenta Visual Studio. Per limitare il numero di problemi visualizzati e migliorare le prestazioni di Visual Studio, è possibile disabilitare l'analisi completa della soluzione. Se necessario, è possibile riabilitare la funzionalità in modo semplice.

Nell'immagine seguente è abilitata l'analisi della soluzione completa. I problemi di analisi del codice e del compilatore in tutti i file della soluzione vengono visualizzati, anche se non sono aperti.

![Analisi completa della soluzione abilitata.](../code-quality/media/fsa_enabled.png)

La figura seguente mostra i risultati della stessa soluzione dopo aver disabilitato l'analisi completa della soluzione. Nel Elenco errori vengono visualizzati solo gli errori del compilatore e i problemi di analisi del codice nei file di soluzione aperti.

![Analisi completa della soluzione disabilitata.](../code-quality/media/fsa_disabled.png)

## <a name="toggle-full-solution-analysis"></a>Consente di abilitare o disabilitare l'analisi completa della soluzione

1. Per aprire la finestra di dialogo **Opzioni** , sulla barra dei menu in Visual Studio scegliere **strumenti** > **Opzioni**.

1. Nella finestra di dialogo **Opzioni** scegliere **Editor di testo** > **C#** o **Basic** > **Advanced**.

1. Selezionare la casella di controllo **Abilita analisi della soluzione completa** per abilitare l'analisi completa della soluzione oppure deselezionare la casella per disabilitarla. Al termine, scegliere **OK** .

   ![Casella di controllo Abilita analisi della soluzione completa.](../code-quality/media/options-enable-full-solution-analysis.png)

## <a name="automatically-disable-full-solution-analysis"></a>Disabilita automaticamente l'analisi completa della soluzione

Se Visual Studio rileva che sono disponibili 200 MB o meno di memoria di sistema, Disabilita automaticamente l'analisi completa della soluzione (e alcune altre funzionalità) se è abilitata. In tal caso, viene visualizzato un avviso che informa che Visual Studio ha disabilitato alcune funzionalità. Un pulsante consente di riabilitare l'analisi completa della soluzione, se necessario.

![Testo dell'avviso la sospensione di analisi della soluzione completa](../code-quality/media/fsa_alert.png)