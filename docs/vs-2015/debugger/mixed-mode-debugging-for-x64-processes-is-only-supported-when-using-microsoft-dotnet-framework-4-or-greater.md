---
title: Modalità mista debug per i processi x64 è solo supportato quando si usa Microsoft.NET Framework 4 o versioni successive | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.error.interop_unsupported_x64
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: b7495655-54c0-4315-8422-43bf63b8c22e
caps.latest.revision: 8
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 80a0c6d24bb1954a9d405c2f318dbb44642d1996
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58954595"
---
# <a name="mixed-mode-debugging-for-x64-processes-is-only-supported-when-using-microsoftnet-framework-4-or-greater"></a>Il debug in modalità mista per i processi x64 è supportato solo quando si utilizza Microsoft .NET Framework 4 o versione successiva
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

NET Framework versioni precedenti a 4 non forniscono supporto per il debug in modalità mista di x64 processi. Ciò significa che non è possibile passare dal codice gestito al codice nativo, o viceversa, durante l'esecuzione del debug.  
  
### <a name="workarounds"></a>Soluzioni  
  
-   Aggiornare il progetto per l'utilizzo di Microsoft .NET Framework 4 o versione successiva.  
  
     - oppure -  
  
     Eseguire il debug del codice gestito e del codice nativo in sessioni di debug separate.  
  
     - oppure -  
  
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
  
-   Visualizzare [impostazione del debug SQL](http://msdn.microsoft.com/3db09e68-edcc-42de-9c22-4e97cfd55ab3).  
  
## <a name="see-also"></a>Vedere anche  
 [Eseguire il debug di applicazioni a 64 Bit](../debugger/debug-64-bit-applications.md)
