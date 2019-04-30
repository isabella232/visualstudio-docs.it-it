---
title: 'Procedura: Tornare alla funzione che ha chiamato MFC se interrotta | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.mfc
dev_langs:
- FSharp
- VB
- CSharp
- C++
- C++
helpviewer_keywords:
- functions [C++], debugging
- function calls, returning to calling function
- debugging [MFC], returning to calling function
- debugging [MFC], functions
- Break command
- programs, halting
- functions [debugger]
ms.assetid: d254a5a9-afbd-4923-9d7a-7422d824cabf
caps.latest.revision: 21
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 883fc1e4bd106ad067e3a9e412268860ed889e5c
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63438242"
---
# <a name="how-to-get-back-to-the-function-that-called-mfc-if-halted"></a>Procedura: Tornare alla funzione che ha chiamato MFC se interrotta
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

NOTA]
> Le finestre di dialogo e i comandi di menu visualizzati potrebbero essere diversi da quelli descritti nella Guida a seconda delle impostazioni attive o dell'edizione del programma. Per modificare le impostazioni, scegliere Importa/esporta impostazioni dal menu Strumenti. Per altre informazioni, vedere [Personalizzazione delle impostazioni di sviluppo in Visual Studio](http://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
 Se è stato usato il comando **Interrompi** del menu **Debug** per interrompere il programma ma la chiamata di MFC è stata comunque eseguita, è possibile usare la finestra Stack di chiamate per tornare alla funzione, dopo aver verificato che il problema dipende dal codice. Per altre informazioni, vedere [Procedura: Usare la finestra Stack di chiamate](../debugger/how-to-use-the-call-stack-window.md).  
  
 Talvolta è possibile che il codice si interrompa nel message pump. In questo caso, non è disponibile codice utente nello stack di chiamate. Per evitare questo problema, usare i punti di interruzione (se possibile con condizioni e conteggi dei passaggi) anziché il comando **Interrompi**. Per altre informazioni, vedere [Breakpoints and Tracepoints](http://msdn.microsoft.com/fe4eedc1-71aa-4928-962f-0912c334d583)).  
  
### <a name="to-navigate-to-the-function-from-which-mfc-was-called"></a>Per tornare alla funzione da cui è stata eseguita la chiamata di MFC  
  
- Usare la finestra **Stack di chiamate**.  
  
## <a name="see-also"></a>Vedere anche  
 [Domande frequenti sul debug del codice nativo](../debugger/debugging-native-code-faqs.md)   
 [Debug del codice nativo](../debugger/debugging-native-code.md)
