---
title: 'Errore: Modalità mista di debug per i processi x64 è supportato solo quando si usa Microsoft .NET Framework 4 o versione successiva | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.error.interop_unsupported_x64
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: e4b0216c-7006-4832-883f-08e982ba8d3f
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 6d338ee3660c4459510de7b01b42cb3670328e4c
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58964339"
---
# <a name="error-mixed-mode-debugging-for-x64-processes-is-supported-only-when-using-microsoft-net-framework-4-or-greater"></a>Errore: Il debug in modalità mista per i processi x64 è supportato solo quando si esegue una versione di Microsoft .NET Framework precedente alla 4
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Per eseguire il debug di codice nativo e gestito misto in un processo a 64 bit, è necessario disporre di [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] versione 4. Il debug in modalità mista dei processi a 64 bit con versioni di [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] precedenti alla 4 non è supportato.  
  
### <a name="to-correct-this-error"></a>Per correggere l'errore  
  
-   Effettuare uno dei passaggi indicati di seguito.  
  
    -   Aggiornare [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] alla versione 4.  
  
    -   Compilare una versione a 32 bit dell'applicazione per il debug.  
  
## <a name="see-also"></a>Vedere anche  
 [Impostare Remote Tools sul dispositivo](http://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c)
