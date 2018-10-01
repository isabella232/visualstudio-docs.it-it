---
title: 'Errore: ASP.NET non è installato | Microsoft Docs'
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
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0617f5200a69809afc86fe9405dc3ea9bd8fcda0
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47528898"
---
# <a name="error-aspnet-not-installed"></a>Errore: ASP.NET non è installato
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [errore: ASP.NET non installato](https://docs.microsoft.com/visualstudio/debugger/error-aspnet-not-installed).  
  
Questo errore si verifica quando [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] non è installato correttamente nel computer di cui si sta tentando di eseguire il debug. Questo errore potrebbe essere dovuto al fatto che [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] non è mai stato installato o che [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] è stato installato prima di IIS.  
  
### <a name="to-reinstall-aspnet"></a>Per reinstallare ASP.NET  
  
1.  Da una finestra del prompt dei comandi eseguire il comando seguente:  
  
    ```  
    \WINDOWS\Microsoft.NET\Framework\version\aspnet_regiis -i  
    ```  
  
     in cui *versione* rappresenta il numero di versione di .NET Framework installata nel computer, ad esempio v1.0.370. È possibile determinare la versione del framework esaminando il `\WINDOWS\Microsoft.NET\Framework` directory.  
  
    > [!NOTE]
    >  Con Windows Server 2003, è possibile installare [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] usando **Aggiungi / Rimuovi programmi** nel Pannello di controllo.  
  
## <a name="see-also"></a>Vedere anche  
 [Debug di applicazioni Web: errori e risoluzione dei problemi](../debugger/debugging-web-applications-errors-and-troubleshooting.md)



