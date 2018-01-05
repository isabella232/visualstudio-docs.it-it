---
title: 'Procedura: abilitare e disabilitare l''analisi della soluzione completa per il codice gestito | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: full solution analysis
ms.assetid: 04315147-5792-47f0-8b5f-9ac8413c6a57
caps.latest.revision: "12"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-ide-code-analysis
ms.workload: dotnet
ms.openlocfilehash: eb69b6c2e26aab36ec4dac0a664cb20b411a815a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-enable-and-disable-full-solution-analysis-for-managed-code"></a>Procedura: abilitare e disabilitare l'analisi della soluzione completa per il codice gestito
> [!NOTE]
>  Questo argomento si applica solo a Visual Studio 2015 Update 3 RC e versioni successive.  
  
 *Analisi della soluzione completa* è una funzionalità di Visual Studio che consente di scegliere se vengono visualizzati i problemi di analisi codice solo in Visual c# o Visual Basic file aperti nella soluzione o nel file Visual c# o Visual Basic sia aperti e chiusi nella soluzione.  
  
 Mentre la possibilità di visualizzare tutti i problemi in tutti i file è utile, può essere fonte di distrazione e rallentamento anche a Visual Studio se la soluzione è molto grande o dispone di molti file.  Per limitare il numero di problemi illustrato e migliorare le prestazioni di Visual Studio, è possibile disabilitare l'analisi della soluzione completa. Se si desidera, è possibile riabilitare facilmente questa funzionalità.  
  
#### <a name="to-toggle-full-solution-analysis"></a>Per attivare o disattivare analisi della soluzione completa  
  
1.  Nel menu principale in Visual Studio, scegliere **strumenti** &#124; **Opzioni** per visualizzare il **opzioni** la finestra di dialogo.  
  
2.  Nel **opzioni** finestra di dialogo scegliere **Editor di testo** &#124; **C#** o **base** &#124; **Advanced**.  
  
3.  Selezionare il **abilitare l'analisi della soluzione completa** casella di controllo per abilitare l'analisi della soluzione completa, o deselezionare la casella per disabilitarla. Scegliere il **OK** pulsante una volta terminato.  
  
     ![Abilitare la casella di controllo di analisi soluzione completa. ] (../code-quality/media/fsa_toolsoptions.png "FSA_ToolsOptions")  
  
## <a name="results-of-enabling-and-disabling-full-solution-analysis"></a>Risultati di abilitazione e disabilitazione di analisi della soluzione completa  
 Nella schermata seguente, è possibile visualizzare i risultati quando sono abilitata l'analisi della soluzione completa. Tutti gli errori e problemi di analisi del codice in *tutti* dei file nella soluzione vengono visualizzati, anche se i file sono aperti.  
  
 ![Analisi della soluzione completa abilitata. ] (../code-quality/media/fsa_enabled.png "FSA_Enabled")  
  
 Nella schermata seguente mostra i risultati dalla stessa soluzione dopo la disabilitazione di analisi della soluzione completa. Solo gli errori e problemi di analisi del codice in aprono Esplora file vengono visualizzati nell'elenco errori.  
  
 ![Analisi della soluzione completa disabilitato. ] (../code-quality/media/fsa_disabled.png "FSA_Disabled")  
  
## <a name="automatically-disabling-full-solution-analysis"></a>Disattiva automaticamente l'analisi della soluzione completa  
 Se Visual Studio rileva che 200MB o minore di memoria di sistema è disponibile, disabilita automaticamente analisi della soluzione completa (così come altre caratteristiche) se è abilitato. In questo caso, viene visualizzato un avviso che informa dell'oggetto. Un pulsante consente di abilitare nuovamente l'analisi della soluzione completa per eseguire questa operazione.  
  
 ![Avviso di analisi della soluzione completa di sospensione](../code-quality/media/fsa_alert.png "FSA_Alert")  
  
## <a name="additional-details"></a>Dettagli aggiuntivi  
 Per impostazione predefinita, l'analisi della soluzione completa sono abilitato per Visual Basic e disabilitato per Visual c#.  
  
 Visual Studio Update 3 RC include un motore di diagnostica v2 analyzer migliorata del codice che riduce l'utilizzo di memoria in modo significativo e riduce il tempo di CPU per inattività, anche se sono abilitata l'analisi della soluzione completa.