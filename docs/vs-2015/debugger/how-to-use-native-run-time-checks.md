---
title: 'Procedura: utilizzare i controlli runtime nativi | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- c.runtime.errorchecks
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
- /RTC compiler option [C++], /O compiler option
- run-time checks, native
- stack, pointer corruption
- stack pointers, corruption
- /O compiler option, /RTC option
- run-time errors, error checks
- O compiler option, /RTC option
- debugger, runtime errors
- variables [debugger], loss of data
- runtime_checks pragma
- variables [debugger], catching dependencies on uninitialized local variables
- run-time errors, debugging
- debugger, native run-time checks
- optimized build option
- RTC compiler option, /O compiler option
- native run-time checks
- run-time checks
- debugging arrays
- stack pointers
- arrays [Visual Studio], debugging
ms.assetid: dc7b2f1e-5ff6-42e0-89b3-dc9dead83ee1
caps.latest.revision: 24
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: b50dda3e31e27fa5d177c3b0ba2790babd2a660f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "65685863"
---
# <a name="how-to-use-native-run-time-checks"></a>Procedura: utilizzare controlli runtime nativi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In Visual C++ è possibile usare [runtime_checks](https://msdn.microsoft.com/library/ae50b43f-f88d-47ad-a2db-3389e9e7df5b) nativi per rilevare errori di runtime comuni, ad esempio:  
  
- Errori del puntatore dello stack.  
  
- Sovraccarichi di matrici locali.  
  
- Errori dello stack.  
  
- Dipendenze da variabili locali non inizializzate.  
  
- Perdita di dati a causa dell'assegnazione a una variabile di lunghezza inferiore.  
  
  Se si usa l'opzione **/RTC** con una build ottimizzata (**/O**), verrà restituito un errore del compilatore. Se si usa un pragma `runtime_checks` in una build ottimizzata, il pragma non avrà effetto.  
  
  Durante il debug di un programma in cui sono attivi i controlli runtime, l'azione predefinita quando si verifica un errore di runtime è l'arresto del programma e il passaggio al debugger. Tale comportamento predefinito può essere modificato per qualsiasi controllo runtime. Per ulteriori informazioni, vedere [gestione delle eccezioni con il debugger](../debugger/managing-exceptions-with-the-debugger.md).  
  
  Nelle procedure riportate di seguito viene descritto come attivare i controlli runtime nativi in una build di debug e come modificare il comportamento di tali controlli.  
  
  Negli altri argomenti di questa sezione vengono fornite informazioni relative a:  
  
- [Personalizzazione dei controlli runtime nativi](../debugger/native-run-time-checks-customization.md)  
  
- [Utilizzo dei controlli runtime senza la libreria di runtime del linguaggio C](../debugger/using-run-time-checks-without-the-c-run-time-library.md)  
  
### <a name="to-enable-native-run-time-checks-in-a-debug-build"></a>Per attivare i controlli runtime nativi in una build di debug  
  
- Usare l'opzione **/RTC** e collegarsi alla versione di debug di una libreria di runtime del linguaggio C, ad esempio /MDd.  
  
### <a name="to-modify-native-run-time-check-behavior"></a>Per modificare il comportamento dei controlli runtime nativi  
  
- Usare il pragma `runtime_checks` .  
  
## <a name="see-also"></a>Vedere anche  
 [Debug in Visual Studio](../debugger/debugging-in-visual-studio.md)   
 [runtime_checks](https://msdn.microsoft.com/library/ae50b43f-f88d-47ad-a2db-3389e9e7df5b)   
 [Controllo degli errori di run-time](https://msdn.microsoft.com/library/c965dd01-57ad-4a3c-b1d6-5aa04f920501)
