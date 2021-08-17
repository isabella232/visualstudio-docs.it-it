---
title: Il debug in modalità mista per i processi x64 è supportato solo quando si utilizza Microsoft .NET Framework 4 o versione successiva
description: Le versioni di .NET Framework precedenti alla 4 non forniscono alcun supporto per il debug in modalità mista di processi x64. Per le soluzioni alternative, vedere questo articolo.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 01299107e9260272044548323e84cab1f78e6867438293bde9e315458a2bd369
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121343689"
---
# <a name="mixed-mode-debugging-for-x64-processes-is-only-supported-when-using-microsoftnet-framework-4-or-greater"></a>Il debug in modalità mista per i processi x64 è supportato solo quando si utilizza Microsoft .NET Framework 4 o versione successiva
Le versioni di .NET Framework precedenti alla 4 non forniscono alcun supporto per il debug in modalità mista di processi x64. Ciò significa che non è possibile passare dal codice gestito al codice nativo, o viceversa, durante l'esecuzione del debug.

### <a name="workarounds"></a>Soluzioni alternative

- Aggiornare il progetto per l'utilizzo di Microsoft .NET Framework 4 o versione successiva.

     -oppure-

     Eseguire il debug del codice gestito e del codice nativo in sessioni di debug separate.

     -oppure-

     Eseguire il debug del codice misto come processo a 32 bit, come descritto nelle procedure che seguono.

### <a name="to-change-the-platform-to-32-bit-visual-basic-or-c"></a>Per impostare la piattaforma su 32 bit (Visual Basic o C#)

1. In **Esplora soluzioni** fare clic con il pulsante destro del mouse sul progetto e scegliere **Proprietà**.

2. Nella pagina delle proprietà fare clic sulla scheda **Compilazione** o **Debug**.

3. Fare clic su **Piattaforma** e selezionare x86 dall'elenco di piattaforme.

     Per impostazione predefinita, i compilatori Visual Basic e C# producono codice eseguibile in qualsiasi CPU. In un computer a 64 bit, questi binari sono eseguiti come processi a 64 bit. Per l'esecuzione in un processo a 32 bit, è necessario scegliere **Win32** anziché **AnyCPU**.

### <a name="to-change-the-platform-to-32-bit-cc"></a>Per impostare la piattaforma su 32 bit (C/C++)

1. In **Esplora soluzioni** fare clic con il pulsante destro del mouse sul progetto, quindi scegliere **Proprietà**.

2. Nelle pagine delle proprietà fare clic su **Piattaforma** e selezionare Win32 dall'elenco di piattaforme.

### <a name="to-correct-this-error"></a>Per correggere l'errore

- Vedere [Configurazione del SQL debug.](/previous-versions/visualstudio/visual-studio-2010/s4sszxst(v=vs.100))

## <a name="see-also"></a>Vedi anche
- [Eseguire il debug di applicazioni a 64 bit](../debugger/debug-64-bit-applications.md)