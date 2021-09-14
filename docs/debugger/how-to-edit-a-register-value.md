---
title: Modificare un valore di registro | Microsoft Docs
description: Informazioni su come modificare il contenuto di un registro modificandone il valore nella finestra Registri (disponibile solo se è abilitato il debug a livello di indirizzo).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.debug.register.edit
dev_langs:
- C++
helpviewer_keywords:
- Registers window, editing register values
- register values
ms.assetid: e27b6bd8-e6d4-4f1d-8a86-9f4047bb1167
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 71532f7b1c1aad8959ce3a10e7b955d55c3e51d9
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126636684"
---
# <a name="how-to-edit-a-register-value-c"></a>Procedura: Modificare un valore di registro (C++)

La finestra Registri è disponibile solo se il debug a livello di indirizzo è stato attivato nella finestra di dialogo **Opzioni**, nodo **Debug**.

### <a name="to-change-the-value-of-a-register"></a>Per modificare il valore di un registro

1. Nella finestra **Registri** premere TAB o utilizzare il mouse per spostare il punto di inserimento sul valore che si desidera modificare. Prima di cominciare a digitare, assicurarsi che il cursore si trovi davanti al valore che si desidera sovrascrivere.

2. Digitare il nuovo valore.

    > [!CAUTION]
    > La modifica dei valori di registro, soprattutto per i registri EIP ed EBP, può avere effetto sull'esecuzione del programma.

    > [!CAUTION]
    > La modifica di valori a virgola mobile può causare lievi inesattezze dovute alla conversione dei componenti frazionari da decimali a binari. Anche una modifica apparentemente innocua può generare modifiche in alcuni dei bit meno significativi in un registro a virgola mobile.

## <a name="see-also"></a>Vedi anche
- [Procedura: utilizzare la finestra Registri](../debugger/how-to-use-the-registers-window.md)
