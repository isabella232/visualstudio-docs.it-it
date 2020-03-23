---
title: Abilitare & disabilitare l'analisi completa della soluzione per il codice gestitoEnable to disable full solution analysis for managed code
ms.date: 03/23/2018
ms.topic: conceptual
helpviewer_keywords:
- full solution analysis
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: d699dd74315cfc36820c1cdb4120543e0290b1a1
ms.sourcegitcommit: b32fbbcbc43910b0ed7ce79aa9a22f2ed36ab57e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/16/2020
ms.locfileid: "79428271"
---
# <a name="how-to-enable-and-disable-full-solution-analysis-for-managed-code"></a>Procedura: abilitare e disabilitare l'analisi completa della soluzione per il codice gestitoHow to: Enable and disable full solution analysis for managed code

*L'analisi completa* della soluzione significa che l'analisi del codice esamina tutti i file di C o Visual Basic nella soluzione, indipendentemente dal fatto che siano aperti o meno nell'editor. Per impostazione predefinita, l'analisi completa della soluzione è *abilitata* per Visual Basic e *disabilitata* per C .

Può essere utile vedere tutti i problemi in tutti i file, ma può anche essere fonte di distrazione. Rallenta Visual Studio se la soluzione è molto grande o ha molti file. Per limitare il numero di problemi visualizzati e migliorare le prestazioni di Visual Studio, è possibile disabilitare l'analisi completa della soluzione. Se necessario, è possibile riattivare facilmente questa funzione.

Nell'immagine seguente è abilitata l'analisi completa della soluzione. Il compilatore e i problemi di analisi del codice in tutti i file nella soluzione vengono visualizzati, anche se non sono aperti.

![Analisi completa della soluzione abilitata.](../code-quality/media/fsa_enabled.png)

L'immagine seguente mostra i risultati della stessa soluzione dopo la disabilitazione dell'analisi completa della soluzione. Solo gli errori del compilatore e i problemi di analisi del codice nei file di soluzione aperti vengono visualizzati nell'Elenco errori.

![Analisi completa della soluzione disabilitata.](../code-quality/media/fsa_disabled.png)

## <a name="toggle-full-solution-analysis"></a>Attiva/disattiva l'analisi completa della soluzione

1. Per aprire la finestra di dialogo **Opzioni,** sulla barra dei menu di Visual Studio scegliere**Opzioni** **strumenti** > .

1. Nella finestra di dialogo **Opzioni,** scegliere **Editor di** > testo**in C,** o**Avanzate**di **base** > .

1. Selezionare la casella di controllo **Abilita analisi soluzione completa** per abilitare l'analisi completa della soluzione oppure deselezionare la casella per disabilitarla. Al termine, scegliere **OK.**

   ![Casella di controllo Abilita analisi soluzione completa.](../code-quality/media/options-enable-full-solution-analysis.png)

## <a name="automatically-disable-full-solution-analysis"></a>Disabilita automaticamente l'analisi completa della soluzione

Se Visual Studio rileva che 200 MB o meno di memoria di sistema è disponibile, disabilita automaticamente l'analisi completa della soluzione (e alcune altre funzionalità) se è abilitata. In questo caso, viene visualizzato un avviso che informa che Visual Studio ha disabilitato alcune funzionalità. Un pulsante consente di riattivare l'analisi completa della soluzione, se lo si desidera.

![Testo di avviso che sospende l'analisi completa della soluzione](../code-quality/media/fsa_alert.png)
