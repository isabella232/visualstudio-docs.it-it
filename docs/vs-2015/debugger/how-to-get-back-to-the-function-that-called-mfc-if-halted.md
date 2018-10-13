---
title: 'Procedura: tornare alla funzione che ha chiamato MFC se interrotta | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
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
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9cf717fec6324d26d2f483bd0f38c3a0731f0d67
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49172926"
---
# <a name="how-to-get-back-to-the-function-that-called-mfc-if-halted"></a>Procedura: tornare alla funzione che ha chiamato MFC se interrotta
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

NOTA]
>  Le finestre di dialogo e i comandi di menu visualizzati potrebbero essere diversi da quelli descritti nella Guida a seconda delle impostazioni attive o dell'edizione del programma. Per modificare le impostazioni, scegliere Importa/esporta impostazioni dal menu Strumenti. Per altre informazioni, vedere [Personalizzazione delle impostazioni di sviluppo in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
 Se è stato usato il **interrompere** comando il **Debug** menu per interrompere il programma e finisce nel MFC e si è certi che il problema è nel codice, è possibile utilizzare la finestra Stack di chiamate per tornare alla funzione. Per altre informazioni, vedere [procedura: usare la finestra Stack di chiamate](../debugger/how-to-use-the-call-stack-window.md).  
  
 Talvolta è possibile che il codice si interrompa nel message pump. In questo caso, non è disponibile codice utente nello stack di chiamate. Per evitare questo problema, è possibile usare i punti di interruzione (possibilmente con condizioni e conteggi dei passaggi) anziché il **Interrompi** comando. Per altre informazioni, vedere [Breakpoints and Tracepoints](http://msdn.microsoft.com/en-us/fe4eedc1-71aa-4928-962f-0912c334d583)).  
  
### <a name="to-navigate-to-the-function-from-which-mfc-was-called"></a>Per tornare alla funzione da cui è stata eseguita la chiamata di MFC  
  
-   Usare la **Stack di chiamate** finestra.  
  
## <a name="see-also"></a>Vedere anche  
 [Domande frequenti sul codice nativo debug](../debugger/debugging-native-code-faqs.md)   
 [Debug del codice nativo](../debugger/debugging-native-code.md)



