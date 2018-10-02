---
title: 'Errore: In modalità mista debug per i processi x64 è supportato solo quando si usa Microsoft .NET Framework 4 o versioni successive | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.error.interop_unsupported_x64
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: e4b0216c-7006-4832-883f-08e982ba8d3f
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 479a771300e37e09412accb16771d31454469f95
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47525405"
---
# <a name="error-mixed-mode-debugging-for-x64-processes-is-supported-only-when-using-microsoft-net-framework-4-or-greater"></a>Errore: il debug in modalità mista per i processi x64 è supportato solo quando si utilizza Microsoft .NET Framework 4 o versione successiva
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [errori: modalità mista di debug per i processi x64 è supportato solo quando si usa Microsoft .NET Framework 4 o versione successiva](https://docs.microsoft.com/visualstudio/debugger/error-mixed-mode-debugging-for-x64-processes-is-supported-only-when-using-microsoft-dotnet-framework-4-or-greater).  
  
Per eseguire il debug di codice nativo e gestito misto in un processo a 64 bit, è necessario disporre di [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] versione 4. Il debug in modalità mista dei processi a 64 bit con versioni di [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] precedenti alla 4 non è supportato.  
  
### <a name="to-correct-this-error"></a>Per correggere l'errore  
  
-   Effettuare uno dei passaggi indicati di seguito.  
  
    -   Aggiornare [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] alla versione 4.  
  
    -   Compilare una versione a 32 bit dell'applicazione per il debug.  
  
## <a name="see-also"></a>Vedere anche  
 [Impostare Remote Tools sul dispositivo](http://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c)



