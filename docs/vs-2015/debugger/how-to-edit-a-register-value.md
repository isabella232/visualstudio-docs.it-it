---
title: 'Procedura: modificare un valore di registro | Microsoft Docs'
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
- vs.debug.register.edit
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
- Registers window, editing register values
- register values
ms.assetid: e27b6bd8-e6d4-4f1d-8a86-9f4047bb1167
caps.latest.revision: 29
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 465ecd4e8003b82a0a7dfbab33004ef2b80d7f32
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47528665"
---
# <a name="how-to-edit-a-register-value"></a>Procedura: modificare un valore di registro
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [procedura: modificare un valore di registro](https://docs.microsoft.com/visualstudio/debugger/how-to-edit-a-register-value).  
  
La finestra Registri è disponibile solo se è abilitato il debug a livello di indirizzo nel **le opzioni** della finestra di dialogo **debug** nodo.  
  
### <a name="to-change-the-value-of-a-register"></a>Per modificare il valore di un registro  
  
1.  Nel **registra** finestra, utilizzare il tasto TAB o il mouse per spostare l'inserimento punto sul valore che si desidera modificare. Prima di cominciare a digitare, assicurarsi che il cursore si trovi davanti al valore che si desidera sovrascrivere.  
  
2.  Digitare il nuovo valore.  
  
    > [!CAUTION]
    >  La modifica dei valori di registro, soprattutto per i registri EIP ed EBP, può avere effetto sull'esecuzione del programma.  
  
    > [!CAUTION]
    >  La modifica di valori a virgola mobile può causare lievi inesattezze dovute alla conversione dei componenti frazionari da decimali a binari. Anche una modifica apparentemente innocua può generare modifiche in alcuni dei bit meno significativi in un registro a virgola mobile.  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura: Usare la finestra Registri](../debugger/how-to-use-the-registers-window.md)





