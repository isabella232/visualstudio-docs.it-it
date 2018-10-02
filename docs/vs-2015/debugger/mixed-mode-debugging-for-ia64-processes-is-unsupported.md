---
title: Il debug in modalità mista per i processi IA64 non è supportato. | Microsoft Docs
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
- vs.debug.error.interop_unsupported_ia64
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 20bc1e38-049b-4388-87c4-936815d85b46
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3777ce079aea853400896408542380c5e2d16ef5
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47526012"
---
# <a name="mixed-mode-debugging-for-ia64-processes-is-unsupported"></a>Il debug in modalità mista per i processi IA64 non è supportato.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [debug in modalità mista per i processi IA64 non è supportato.](https://docs.microsoft.com/visualstudio/debugger/mixed-mode-debugging-for-ia64-processes-is-unsupported).  
  
Visual Studio non supporta debug in modalità mista di codice gestito e nativo nei processi IA64. Questo significa che non è possibile passare dal codice gestito al codice nativo, o viceversa, durante l'esecuzione del debug.  
  
### <a name="workarounds"></a>Soluzioni  
  
-   Eseguire il debug del codice gestito e del codice nativo in sessioni di debug separate.  
  
     - oppure -  
  
     Eseguire il debug del codice misto come processo a 32 bit, come descritto nelle procedure che seguono.  
  
### <a name="to-change-the-platform-to-32-bit-visual-basic-or-c"></a>Per impostare la piattaforma su 32 bit (Visual Basic o C#)  
  
1.  Nelle **Esplora soluzioni**, fare doppio clic sul progetto, quindi fare clic su **proprietà** nel menu di scelta rapida.  
  
2.  Nelle pagine delle proprietà, fare clic sul **Compile** oppure **Debug** scheda.  
  
3.  Fare clic su **piattaforma** e selezionare x86 dall'elenco di piattaforme.  
  
     Per impostazione predefinita, i compilatori Visual Basic e C# producono codice eseguibile in qualsiasi CPU. In un computer a 64 bit, questi binari sono eseguiti come processi a 64 bit. Per eseguire in un processo a 32 bit, è necessario scegliere **Win32**, non **AnyCPU**.  
  
### <a name="to-change-the-platform-to-32-bit-cc"></a>Per impostare la piattaforma su 32 bit (C/C++)  
  
1.  Nelle **Esplora soluzioni**, fare doppio clic sul progetto, quindi fare clic su **proprietà** nel menu di scelta rapida.  
  
2.  Nelle pagine delle proprietà, fare clic su **piattaforma** e selezionare Win32 dall'elenco di piattaforme,  
  
## <a name="see-also"></a>Vedere anche  
 [Eseguire il debug di applicazioni a 64 Bit](../debugger/debug-64-bit-applications.md)



