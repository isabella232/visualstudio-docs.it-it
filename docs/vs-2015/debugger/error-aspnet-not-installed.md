---
title: 'Errore: ASP.NET non è installato | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.error.http_not_supported
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- Web applications, errors
- debugger, Web application errors
- error messages, ASP.NET
- ASP.NET, installation error messages
ms.assetid: 6286dd3d-3e2b-4edd-959d-81e0ed45500b
caps.latest.revision: 17
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 31268b94ab632e598badcba3def387ef1fc2ba1d
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58954231"
---
# <a name="error-aspnet-not-installed"></a>Errore: ASP.NET non è installato
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Questo errore si verifica quando [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] non è installato correttamente nel computer di cui si sta tentando di eseguire il debug. Questo errore potrebbe essere dovuto al fatto che [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] non è mai stato installato o che [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] è stato installato prima di IIS.  
  
### <a name="to-reinstall-aspnet"></a>Per reinstallare ASP.NET  
  
1.  Da una finestra del prompt dei comandi eseguire il comando seguente:  
  
    ```  
    \WINDOWS\Microsoft.NET\Framework\version\aspnet_regiis -i  
    ```  
  
     in cui *versione* rappresenta il numero di versione di .NET Framework installata nel computer, ad esempio v1.0.370. È possibile determinare la versione del framework esaminando il `\WINDOWS\Microsoft.NET\Framework` directory.  
  
    > [!NOTE]
    >  Con Windows Server 2003 è possibile installare [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] dall'applicazione **Installazione applicazioni** del Pannello di controllo.  
  
## <a name="see-also"></a>Vedere anche  
 [Debug di applicazioni Web: Errori e risoluzione dei problemi](../debugger/debugging-web-applications-errors-and-troubleshooting.md)
