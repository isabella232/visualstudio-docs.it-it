---
title: "Procedura: abilitare e disabilitare l'analisi completa della soluzione per il codice gestito | Microsoft Docs"
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- full solution analysis
ms.assetid: 04315147-5792-47f0-8b5f-9ac8413c6a57
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 72b27bf9dcc1f0ee8a222ac701f2ffae4fc68614
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72646286"
---
# <a name="how-to-enable-and-disable-full-solution-analysis-for-managed-code"></a>Procedura: abilitare e disabilitare l'analisi completa della soluzione per il codice gestito
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

NOTA]
> Questo argomento si applica solo a Visual Studio 2015 Update 3 RC e versioni successive.

 L' *analisi completa della soluzione* è una funzionalità di Visual Studio che consente di scegliere se visualizzare i problemi di analisi del codice C# solo nei file Visual o Visual Basic aperti della soluzione oppure nei file visivi C# aperti e chiusi o Visual Basic nel soluzione.

 Anche se la possibilità di visualizzare tutti i problemi in tutti i file è utile, è possibile che si tratti di distrazione e persino rallentare Visual Studio se la soluzione è molto grande o contiene molti file.  Per limitare il numero di problemi visualizzati e migliorare le prestazioni di Visual Studio, è possibile disabilitare l'analisi completa della soluzione. Se lo si desidera, è possibile riabilitare la funzionalità in modo semplice.

#### <a name="to-toggle-full-solution-analysis"></a>Per abilitare o disabilitare l'analisi completa della soluzione

1. Nel menu principale di Visual Studio scegliere **strumenti** &#124; **Opzioni** per visualizzare la finestra di dialogo **Opzioni** .

2. Nella finestra di dialogo **Opzioni** scegliere **Editor** &#124; **C#** di testo o &#124; **Avanzate**di base.

3. Selezionare la casella di controllo **Abilita analisi della soluzione completa** per abilitare l'analisi completa della soluzione oppure deselezionare la casella per disabilitarla. Al termine, scegliere il pulsante **OK** .

     ![Casella di controllo Abilita analisi della soluzione completa.](../code-quality/media/fsa-toolsoptions.png "FSA_ToolsOptions")

## <a name="results-of-enabling-and-disabling-full-solution-analysis"></a>Risultati dell'abilitazione e disabilitazione dell'analisi completa della soluzione
 Nello screenshot seguente è possibile visualizzare i risultati quando è abilitata l'analisi completa della soluzione. Vengono visualizzati tutti gli errori e i problemi di analisi del codice in *tutti* i file della soluzione, indipendentemente dal fatto che i file siano aperti o meno.

 ![Analisi completa della soluzione abilitata.](../code-quality/media/fsa-enabled.png "FSA_Enabled")

 La schermata seguente mostra i risultati della stessa soluzione dopo la disabilitazione dell'analisi completa della soluzione. Nel Elenco errori vengono visualizzati solo gli errori e i problemi di analisi del codice nei file di soluzione aperti.

 ![Analisi completa della soluzione disabilitata.](../code-quality/media/fsa-disabled.png "FSA_Disabled")

## <a name="automatically-disabling-full-solution-analysis"></a>Disabilitazione automatica dell'analisi completa della soluzione
 Se Visual Studio rileva che è disponibile 200 MB o meno di memoria di sistema, Disabilita automaticamente l'analisi completa della soluzione (oltre ad altre funzionalità) se è abilitata. In tal caso, viene visualizzato un avviso che informa l'utente. Un pulsante consente di riabilitare l'analisi completa della soluzione, se si desidera eseguire questa operazione.

 ![Testo dell'avviso sospensione dell'analisi completa della soluzione](../code-quality/media/fsa-alert.png "FSA_Alert")

## <a name="additional-details"></a>Dettagli aggiuntivi
 Per impostazione predefinita, l'analisi della soluzione completa è abilitata per Visual Basic C#e disabilitata per Visual.

 Visual Studio Update 3 RC include un motore di diagnostica ottimizzato del codice V2 che riduce significativamente l'utilizzo della memoria e riduce il tempo di inattività della CPU, anche se è abilitata l'analisi completa della soluzione.
