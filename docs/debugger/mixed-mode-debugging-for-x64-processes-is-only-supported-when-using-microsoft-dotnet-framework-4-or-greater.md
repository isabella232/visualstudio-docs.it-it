---
title: Modalità mista debug per i processi x64 è solo supportato quando si usa Microsoft.NET Framework 4 o versioni successive | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug.error.interop_unsupported_x64
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: b7495655-54c0-4315-8422-43bf63b8c22e
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6ba8186114fd976ec7e4704d97acb91ee0c97824
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 02/22/2019
ms.locfileid: "56719535"
---
# <a name="mixed-mode-debugging-for-x64-processes-is-only-supported-when-using-microsoftnet-framework-4-or-greater"></a>Il debug in modalità mista per i processi x64 è supportato solo quando si utilizza Microsoft .NET Framework 4 o versione successiva
Le versioni di .NET Framework precedenti alla 4 non forniscono alcun supporto per il debug in modalità mista di processi x64. Ciò significa che non è possibile passare dal codice gestito al codice nativo, o viceversa, durante l'esecuzione del debug.

### <a name="workarounds"></a>Soluzioni

-   Aggiornare il progetto per l'utilizzo di Microsoft .NET Framework 4 o versione successiva.

     oppure

     Eseguire il debug del codice gestito e del codice nativo in sessioni di debug separate.

     oppure

     Eseguire il debug del codice misto come processo a 32 bit, come descritto nelle procedure che seguono.

### <a name="to-change-the-platform-to-32-bit-visual-basic-or-c"></a>Per impostare la piattaforma su 32 bit (Visual Basic o C#)

1.  In **Esplora soluzioni** fare clic con il pulsante destro del mouse sul progetto e scegliere **Proprietà**.

2.  Nella pagina delle proprietà fare clic sulla scheda **Compilazione** o **Debug**.

3.  Fare clic su **Piattaforma** e selezionare x86 dall'elenco di piattaforme.

     Per impostazione predefinita, i compilatori Visual Basic e C# producono codice eseguibile in qualsiasi CPU. In un computer a 64 bit, questi binari sono eseguiti come processi a 64 bit. Per l'esecuzione in un processo a 32 bit, è necessario scegliere **Win32** anziché **AnyCPU**.

### <a name="to-change-the-platform-to-32-bit-cc"></a>Per impostare la piattaforma su 32 bit (C/C++)

1.  In **Esplora soluzioni** fare clic con il pulsante destro del mouse sul progetto, quindi scegliere **Proprietà**.

2.  Nelle pagine delle proprietà fare clic su **Piattaforma** e selezionare Win32 dall'elenco di piattaforme.

### <a name="to-correct-this-error"></a>Per correggere l'errore

-   Visualizzare [impostazione del debug SQL](/previous-versions/visualstudio/visual-studio-2010/s4sszxst(v=vs.100)).

## <a name="see-also"></a>Vedere anche
- [Eseguire il debug di applicazioni a 64 Bit](../debugger/debug-64-bit-applications.md)