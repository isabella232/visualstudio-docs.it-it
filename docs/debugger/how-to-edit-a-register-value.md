---
title: 'Procedura: modificare un valore di registro | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug.register.edit
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- Registers window, editing register values
- register values
ms.assetid: e27b6bd8-e6d4-4f1d-8a86-9f4047bb1167
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b3ccaa124b64ad462f633e760695f931afaae531
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2019
ms.locfileid: "72733410"
---
# <a name="how-to-edit-a-register-value-c-c-visual-basic-f"></a>Procedura: modificare un valore di registro (C#, C++, Visual Basic, F#)

La finestra Registri è disponibile solo se il debug a livello di indirizzo è stato attivato nella finestra di dialogo **Opzioni**, nodo **Debug**.

### <a name="to-change-the-value-of-a-register"></a>Per modificare il valore di un registro

1. Nella finestra **Registri** premere TAB o utilizzare il mouse per spostare il punto di inserimento sul valore che si desidera modificare. Prima di cominciare a digitare, assicurarsi che il cursore si trovi davanti al valore che si desidera sovrascrivere.

2. Digitare il nuovo valore.

    > [!CAUTION]
    > La modifica dei valori di registro, soprattutto per i registri EIP ed EBP, può avere effetto sull'esecuzione del programma.

    > [!CAUTION]
    > La modifica di valori a virgola mobile può causare lievi inesattezze dovute alla conversione dei componenti frazionari da decimali a binari. Anche una modifica apparentemente innocua può generare modifiche in alcuni dei bit meno significativi in un registro a virgola mobile.

## <a name="see-also"></a>Vedere anche
- [Procedura: Usare la finestra Registri](../debugger/how-to-use-the-registers-window.md)