---
title: Utilizzo in fase di esecuzione dei controlli senza la libreria Run-Time di C | Microsoft Docs
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
- vs.debug.runtime
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
- run-time errors, error checks
- CRT, run-time checks
- debugger, native run-time checks
- run-time errors, run-time checks
- run-time checks, /RTC option
- debugging [Visual Studio], run-time routines
ms.assetid: 30ed90f3-9323-4784-80a4-937449eb54f6
caps.latest.revision: 20
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 864e21d2c2ec2a9922d70e6b69192d9268556737
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47532021"
---
# <a name="using-run-time-checks-without-the-c-run-time-library"></a>Utilizzo dei controlli runtime senza la libreria di runtime del linguaggio C
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [utilizzo libreria Run-Time controlla senza the C Run-Time](https://docs.microsoft.com/visualstudio/debugger/using-run-time-checks-without-the-c-run-time-library).  
  
Se si collega il programma senza la libreria di runtime C, Usa **/NODEFAULTLIB**e si desidera usare i controlli in fase di esecuzione, è necessario collegarlo con RunTmChk.  
  
 `_RTC_Initialize` consente di inizializzare il programma per i controlli runtime. Se non si stabilisce il collegamento con la libreria di runtime del linguaggio C, è necessario verificare che il programma sia compilato con i controlli degli errori di runtime prima di chiamare `_RTC_Initialize`, come illustrato di seguito:  
  
```  
#ifdef __MSVC_RUNTIME_CHECKS  
    _RTC_Initialize();  
#endif  
```  
  
 Se non si stabilisce il collegamento con la libreria di runtime del linguaggio C, è necessario definire anche una funzione chiamata `_CRT_RTC_INITW`. `_CRT_RTC_INITW` consente di installare la funzione definita dall'utente come funzione di segnalazione degli errori predefinita, come illustrato di seguito:  
  
```  
// C version:  
_RTC_error_fnW __cdecl _CRT_RTC_INITW(  
        void *res0, void **res1, int res2, int res3, int res4)  
{  
    // set the error handler.  
    return &MyErrorFunc;   
}  
  
// C++ version:  
extern "C" _RTC_error_fnW __cdecl _CRT_RTC_INITW(  
       void *res0, void **res1, int res2, int res3, int res4)  
{  
    // set the error handler:  
    return &MyErrorFunc;  
}  
```  
  
 Dopo aver installato la funzione di segnalazione degli errori predefinita, sarà possibile installare altre funzioni di segnalazione degli errori con `_RTC_SetErrorFuncW`. Per altre informazioni, vedere [RTC_SetErrorFuncW](http://msdn.microsoft.com/library/b3e0d71f-1bd3-4c37-9ede-2f638eb3c81a).  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura: Usare controlli runtime nativi](../debugger/how-to-use-native-run-time-checks.md)




