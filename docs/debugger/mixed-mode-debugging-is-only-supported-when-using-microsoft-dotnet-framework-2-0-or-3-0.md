---
title: Debug in modalità mista è supportato solo quando si usa Microsoft .NET Framework 2.0 o 3.0 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.error.interop_unsupported_to_old
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: f607af6f-57fe-472a-a32e-b6202067aa96
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 9d51a0ca72840b20e23eaaa9db3a82382a3fa012
ms.sourcegitcommit: 1ab675a872848c81a44d6b4bd3a49958fe673c56
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/10/2018
ms.locfileid: "44284068"
---
# <a name="mixed-mode-debugging-is-only-supported-when-using-microsoft-net-framework-20-or-30"></a>Supporto del debug in modalità mista solo quando si utilizza Microsoft .NET Framework 2.0 o 3.0
Le versioni di Microsoft .NET Framework precedenti alla 2.0 non forniscono alcun supporto per il debug in modalità mista di processi a 64 bit. Ciò significa che non è possibile passare dal codice gestito al codice nativo o viceversa durante l'esecuzione del debug.  
  
 Per aggirare il problema è possibile:  
  
-   Aggiornare il progetto per utilizzare Microsoft .NET Framework 2.0 o 3.0.  
  
-   Eseguire il debug del codice gestito e del codice nativo in sessioni di debug separate.  
  
-   Eseguire il debug del codice misto come processo a 32 bit, come descritto nelle procedure che seguono.  
  
### <a name="to-change-the-operating-system-to-32-bit-visual-basic-or-c"></a>Per modificare il sistema operativo a 32 bit (Visual Basic o C#)  
  
1.  Nelle **Esplora soluzioni**mouse sul progetto e quindi fare clic su **proprietà** nel menu di scelta rapida.  
  
2.  Nelle pagine delle proprietà, fare clic sul **Compile** oppure **Debug** scheda.  
  
3.  Fare clic su **piattaforma**, quindi selezionare **x86** dall'elenco di piattaforme.  
  
     Per impostazione predefinita, i compilatori di Visual Basic e C# producono codice eseguibile in qualsiasi CPU. In un computer a 64 bit, questi binari sono eseguiti come processi a 64 bit. Per eseguire in un processo a 32 bit, è necessario scegliere **Win32**, non **AnyCPU**.  
  
### <a name="to-change-the-operating-system-to-32-bit-cc"></a>Per modificare il sistema operativo a 32 bit (C/C++)  
  
1.  Nelle **Esplora soluzioni**mouse sul progetto e quindi fare clic su **proprietà** nel menu di scelta rapida.  
  
     Nelle pagine delle proprietà, fare clic su **piattaforma**, quindi selezionare **Win32** dall'elenco di piattaforme.  
  
### <a name="to-correct-this-error"></a>Per correggere l'errore  
  
-   Visualizzare [impostazione del debug SQL](/previous-versions/visualstudio/visual-studio-2010/s4sszxst(v=vs.100)).  
  
## <a name="see-also"></a>Vedere anche  
 [Eseguire il debug di applicazioni a 64 Bit](../debugger/debug-64-bit-applications.md)