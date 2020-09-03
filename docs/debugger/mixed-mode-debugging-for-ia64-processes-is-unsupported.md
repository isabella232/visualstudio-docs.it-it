---
title: Il debug in modalità mista per i processi IA64 non è supportato. | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug.error.interop_unsupported_ia64
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: 20bc1e38-049b-4388-87c4-936815d85b46
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c85c31cff5920ba3dc4b9356a1865d0db2323b2d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "72731096"
---
# <a name="mixed-mode-debugging-for-ia64-processes-is-unsupported"></a>Il debug in modalità mista per i processi IA64 non è supportato.
Visual Studio non supporta debug in modalità mista di codice gestito e nativo nei processi IA64. Questo significa che non è possibile passare dal codice gestito al codice nativo, o viceversa, durante l'esecuzione del debug.

### <a name="workarounds"></a>Soluzioni alternative

- Eseguire il debug del codice gestito e del codice nativo in sessioni di debug separate.

     -oppure-

     Eseguire il debug del codice misto come processo a 32 bit, come descritto nelle procedure che seguono.

### <a name="to-change-the-platform-to-32-bit-visual-basic-or-c"></a>Per impostare la piattaforma su 32 bit (Visual Basic o C#)

1. In **Esplora soluzioni** fare clic con il pulsante destro del mouse sul progetto, quindi fare clic su **Proprietà** nel menu di scelta rapida.

2. Nella pagina delle proprietà fare clic sulla scheda **Compilazione** o **Debug**.

3. Fare clic su **Piattaforma** e selezionare x86 dall'elenco di piattaforme.

     Per impostazione predefinita, i compilatori Visual Basic e C# producono codice eseguibile in qualsiasi CPU. In un computer a 64 bit, questi binari sono eseguiti come processi a 64 bit. Per l'esecuzione in un processo a 32 bit, è necessario scegliere **Win32** anziché **AnyCPU**.

### <a name="to-change-the-platform-to-32-bit-cc"></a>Per impostare la piattaforma su 32 bit (C/C++)

1. In **Esplora soluzioni** fare clic con il pulsante destro del mouse sul progetto, quindi fare clic su **Proprietà** nel menu di scelta rapida.

2. Nelle pagine delle proprietà fare clic su **piattaforma** e selezionare Win32 dall'elenco di piattaforme.

## <a name="see-also"></a>Vedere anche
- [Eseguire il debug di applicazioni a 64 bit](../debugger/debug-64-bit-applications.md)