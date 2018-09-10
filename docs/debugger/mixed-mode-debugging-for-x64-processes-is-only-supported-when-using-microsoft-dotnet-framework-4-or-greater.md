---
title: Modalità mista debug per i processi x64 è solo supportato quando si usa Microsoft.NET Framework 4 o versioni successive | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a6d58713da9a4c809d5f9c3db6f7157a699a467f
ms.sourcegitcommit: 1ab675a872848c81a44d6b4bd3a49958fe673c56
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/10/2018
ms.locfileid: "44284094"
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
  
1.  Nelle **Esplora soluzioni**mouse sul progetto e quindi fare clic su **proprietà**.  
  
2.  Nelle pagine delle proprietà, fare clic sui **Compile** o il **Debug** scheda.  
  
3.  Fare clic su **piattaforma** e selezionare x86 dall'elenco di piattaforme.  
  
     Per impostazione predefinita, i compilatori Visual Basic e C# producono codice eseguibile in qualsiasi CPU. In un computer a 64 bit, questi binari sono eseguiti come processi a 64 bit. Per eseguire in un processo a 32 bit, è necessario scegliere **Win32**, non **AnyCPU**.  
  
### <a name="to-change-the-platform-to-32-bit-cc"></a>Per impostare la piattaforma su 32 bit (C/C++)  
  
1.  Nelle **Esplora soluzioni**, fare clic sul progetto, quindi fare clic su **proprietà**.  
  
2.  Nelle pagine delle proprietà, fare clic su **piattaforma** e selezionare Win32 dall'elenco di piattaforme.  
  
### <a name="to-correct-this-error"></a>Per correggere l'errore  
  
-   Visualizzare [impostazione del debug SQL](/previous-versions/visualstudio/visual-studio-2010/s4sszxst(v=vs.100)).  
  
## <a name="see-also"></a>Vedere anche  
 [Eseguire il debug di applicazioni a 64 Bit](../debugger/debug-64-bit-applications.md)