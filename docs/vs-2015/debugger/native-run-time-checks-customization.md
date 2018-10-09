---
title: Personalizzazione dei controlli runtime nativi | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.crt
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- runtime_checks pragma
- debugger, native run-time checks
- /RTC compiler option [C++], native run-time checks
- customizing CRT error checking
- native run-time checks, customizing
ms.assetid: 76a365fe-6439-49db-8603-34058b78e5a8
caps.latest.revision: 23
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 65aaef84c96605eb0ac5a4836c637c2990a15477
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47532336"
---
# <a name="native-run-time-checks-customization"></a>Personalizzazione dei controlli runtime nativi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [personalizzazione dei controlli runtime nativi](https://docs.microsoft.com/visualstudio/debugger/native-run-time-checks-customization).  
  
Quando esegue la compilazione con **/RTC** (controlli di run-time) oppure usare il `runtime_checks` pragma, la libreria di runtime C fornisce controlli runtime nativi. In alcuni casi può essere necessario personalizzare il controllo runtime:  
  
-   Per indirizzare i messaggi del controllo runtime a un file o una destinazione diversa da quella predefinita.  
  
-   Per specificare una destinazione di output dei messaggi del controllo runtime in un debugger di altri produttori.  
  
-   Per segnalare i messaggi del controllo runtime provenienti da un programma compilato con una versione di rilascio della libreria di runtime del linguaggio C. Nelle versioni di rilascio della libreria per segnalare gli errori di runtime non viene utilizzato `_CrtDbgReportW` Viene invece visualizzata un' **Assert** finestra di dialogo per ogni errore di run-time.  
  
 Per personalizzare il controllo degli errori di runtime, è possibile utilizzare uno degli accorgimenti seguenti:  
  
-   Scrivere una funzione per la segnalazione degli errori di runtime. Per altre informazioni, vedere [procedura: scrivere una funzione di segnalazione errori di Run-Time](../debugger/how-to-write-a-run-time-error-reporting-function.md).  
  
-   Personalizzare la destinazione dei messaggi di errore.  
  
-   Eseguire una query per ottenere informazioni sugli errori rilevati dai controlli runtime.  
  
## <a name="customize-the-error-message-destination"></a>Personalizzare la destinazione dei messaggi di errore  
 Se si utilizza `_CrtDbgReportW` per la segnalazione degli errori, è possibile utilizzare `_CrtSetReportMode` per specificare la destinazione dei messaggi di errore.  
  
 Se si utilizza una funzione di segnalazione degli errori personalizzata, utilizzare `_RTC_SetErrorType` per associare un tipo di report a ciascun errore.  
  
## <a name="query-for-information-about-run-time-checks"></a>Eseguire una query per ottenere informazioni sui controlli runtime  
 `_RTC_NumErrors` restituisce il numero di tipi di errore rilevati dai controlli degli errori di runtime. Per ottenere una breve descrizione di ciascun errore, è possibile creare un ciclo da 0 al valore restituito da `_RTC_NumErrors` passando il valore di iterazione a `_RTC_GetErrDesc` in ciascun ciclo. Per altre informazioni, vedere [RTC_NumErrors](http://msdn.microsoft.com/library/7e82adae-38e2-4f8b-bc0b-37bda8109fd1) e [RTC_GetErrDesc](http://msdn.microsoft.com/library/7994ec2b-5488-4fd4-806d-a166c9a9f927).  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura: usare controlli runtime nativi](../debugger/how-to-use-native-run-time-checks.md)   
 [runtime_checks](http://msdn.microsoft.com/library/ae50b43f-f88d-47ad-a2db-3389e9e7df5b)   
 [_CrtDbgReport, _CrtDbgReportW](http://msdn.microsoft.com/library/6e581fb6-f7fb-4716-9432-f0145d639ecc)




