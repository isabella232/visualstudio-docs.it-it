---
title: Come è possibile individuare chi passa un valore di parametro errato? | Microsoft Docs
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
- vs.debug.parameters
dev_langs:
- FSharp
- VB
- CSharp
- C++
- C++
helpviewer_keywords:
- debugging [C++], parameters
- parameters [debugger]
- passing parameters, troubleshooting wrong values
- functions [debugger], detecting wrong parameter values
- parameter values, troubleshooting
ms.assetid: 1f1ae455-0e25-4e9d-b33f-53908f5bd6ce
caps.latest.revision: 22
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b1d7ae67e7ba09a25277afc55ef92da47a8e770d
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47520018"
---
# <a name="how-can-i-find-out-who-is-passing-a-wrong-parameter-value"></a>Come è possibile individuare chi passa un valore di parametro errato?
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [come è possibile è possibile individuare chi passa un valore di parametro errato?](https://docs.microsoft.com/visualstudio/debugger/how-can-i-find-out-who-is-passing-a-wrong-parameter-value-q).  
  
Descrizione del problema  
 Il valore di parametro errato è stato passato a una delle funzioni utilizzate. Questa funzione viene chiamata da numerosissime posizioni. Come è possibile capire quale elemento passa il valore errato?  
  
## <a name="solution"></a>Soluzione  
  
#### <a name="to-resolve-this-problem"></a>Per risolvere questo problema  
  
1.  Impostare un punto di interruzione del percorso all'inizio della funzione.  
  
2.  Il punto di interruzione e scegliere **condizione**.  
  
3.  Nel **condizione punto di interruzione** finestra di dialogo, fare clic sui **condizione** casella di controllo. Visualizzare [punti di interruzione avanzati](../debugger/using-breakpoints.md#BKMK_Specify_a_breakpoint_condition_using_a_code_expression).  
  
4.  Nella casella di testo immettere un'espressione, ad esempio `Var==3`, in cui `Var` è il nome del parametro che contiene il valore errato e `3` il valore errato passato.  
  
5.  Selezionare il **è impostata su True** pulsante di opzione e fare clic sui **OK** pulsante.  
  
6.  Eseguire nuovamente il programma. Il punto di interruzione causa l'arresto del programma all'inizio della funzione, quando il parametro `Var` ha valore `3`.  
  
7.  Utilizzare la finestra Stack di chiamate per individuare la funzione chiamante e passare al relativo codice sorgente. Per altre informazioni, vedere [procedura: usare la finestra Stack di chiamate](../debugger/how-to-use-the-call-stack-window.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Domande frequenti sul codice nativo debug](../debugger/debugging-native-code-faqs.md)   
 [Punti di interruzione](http://msdn.microsoft.com/en-us/fe4eedc1-71aa-4928-962f-0912c334d583)   
 [Debug del codice nativo](../debugger/debugging-native-code.md)



