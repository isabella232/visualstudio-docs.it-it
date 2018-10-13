---
title: 'Procedura: modificare un valore di registro | Microsoft Docs'
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
ms.openlocfilehash: c6846fc8ae093f3f63a0b9caceee7d0a0c23767f
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49196157"
---
# <a name="how-to-edit-a-register-value"></a>Procedura: modificare un valore di registro
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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





