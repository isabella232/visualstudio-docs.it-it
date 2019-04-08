---
title: "Procedura: Abilitare e disabilitare l'analisi della soluzione completa per il codice gestito | Microsoft Docs"
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- full solution analysis
ms.assetid: 04315147-5792-47f0-8b5f-9ac8413c6a57
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 6b9efdb5ea3e7ccbee9aefb724e847db6a37c2a0
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58954843"
---
# <a name="how-to-enable-and-disable-full-solution-analysis-for-managed-code"></a>Procedura: Abilitare e disabilitare l'analisi della soluzione completa per il codice gestito
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

NOTA]
>  Questo argomento si applica solo a Visual Studio 2015 Update 3 RC e versioni successive.  
  
 *Analisi della soluzione completa* è una funzionalità di Visual Studio che consente di scegliere se vengono visualizzati i problemi di analisi codice solo in Visual C# o Visual Basic file aperti nella soluzione o nel file Visual C# o Visual Basic sia aperti e chiusi nella soluzione.  
  
 Benché sia utile la possibilità di vedere tutti i problemi in tutti i file, può essere fonte di distrazione e rallentano anche a Visual Studio se la soluzione è molto grande o contiene una grande quantità di file.  Per limitare il numero di problemi visualizzati e migliorare le prestazioni di Visual Studio, è possibile disabilitare l'analisi della soluzione completa. Se si desidera, è possibile riabilitare facilmente questa funzionalità.  
  
#### <a name="to-toggle-full-solution-analysis"></a>Per attivare o disattivare analisi della soluzione completa  
  
1.  Nel menu principale in Visual Studio, scegliere **degli strumenti** &#124; **opzioni** per visualizzare il **opzioni** nella finestra di dialogo.  
  
2.  Nel **le opzioni** finestra di dialogo, scegliere **Editor di testo** &#124; **C#** o **Basic** &#124; **avanzate**.  
  
3.  Selezionare il **Abilita analisi della soluzione completa** casella di controllo per abilitare l'analisi della soluzione completa o deselezionare la casella per disabilitarla. Scegliere il **OK** pulsante al termine.  
  
     ![Abilitare la casella di controllo analysis soluzione completa. ](../code-quality/media/fsa-toolsoptions.png "FSA_ToolsOptions")  
  
## <a name="results-of-enabling-and-disabling-full-solution-analysis"></a>Risultati di abilitazione e disabilitazione di analisi della soluzione completa  
 Nello screenshot seguente, è possibile visualizzare i risultati quando sono abilitata l'analisi della soluzione completa. Tutti gli errori e problemi di analisi del codice nel *tutti* dei file nella soluzione viene visualizzata, indipendentemente dal fatto che i file sono aperti.  
  
 ![Analisi della soluzione completa abilitata. ](../code-quality/media/fsa-enabled.png "FSA_Enabled")  
  
 Lo screenshot seguente mostra i risultati dalla stessa soluzione dopo la disabilitazione di analisi della soluzione completa. Solo gli errori e problemi di analisi del codice in aprono Esplora file vengono visualizzati nell'elenco errori.  
  
 ![Analisi della soluzione completa disabilitato. ](../code-quality/media/fsa-disabled.png "FSA_Disabled")  
  
## <a name="automatically-disabling-full-solution-analysis"></a>Automaticamente la disabilitazione di analisi della soluzione completa  
 Se Visual Studio rileva che 200MB o inferiore di memoria di sistema è disponibile a esso, viene disabilitata automaticamente analisi della soluzione completa (nonché alcune altre funzionalità) se è abilitato. In questo caso, viene visualizzato un avviso per informare l'utente di questo oggetto. Un pulsante consente di abilitare nuovamente l'analisi della soluzione completa se si desidera eseguire questa operazione.  
  
 ![Testo dell'avviso la sospensione di analisi della soluzione completa](../code-quality/media/fsa-alert.png "FSA_Alert")  
  
## <a name="additional-details"></a>Dettagli aggiuntivi  
 Per impostazione predefinita, analisi della soluzione completa sono abilitato per Visual Basic e disabilitato per Visual C#.  
  
 Visual Studio Update 3 RC include un motore di diagnostica v2 analizzatore ottimizzato del codice che riduce l'utilizzo di memoria in modo significativo e riduce il tempo di CPU per inattività, anche se sono abilitata l'analisi della soluzione completa.
