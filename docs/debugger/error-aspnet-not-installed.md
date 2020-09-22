---
title: ASP.NET non è installato
ms.date: 11/04/2016
ms.topic: error-reference
f1_keywords:
- vs.debug.error.http_not_supported
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Web applications, errors
- debugger, Web application errors
- error messages, ASP.NET
- ASP.NET, installation error messages
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- aspnet
ms.openlocfilehash: 1c4138b1f3d102e235bb03ebcfd5a80808d8762c
ms.sourcegitcommit: 062615c058d2ff44751e8d0c704ccfa3c5543469
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/22/2020
ms.locfileid: "90852797"
---
# <a name="error-aspnet-not-installed"></a>Errore: ASP.NET non è installato
Questo errore si verifica quando [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] non è installato correttamente nel computer di cui si sta tentando di eseguire il debug. Questo errore potrebbe essere dovuto al fatto che [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] non è mai stato installato o che [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] è stato installato prima di IIS.

### <a name="to-reinstall-aspnet"></a>Per reinstallare ASP.NET

1. Da una finestra del prompt dei comandi eseguire il comando seguente:

   ```cmd
   \WINDOWS\Microsoft.NET\Framework\version\aspnet_regiis -i
   ```

    dove *Version* rappresenta il numero di versione del .NET Framework installato nel computer, ad esempio v 1.0.370. È possibile determinare la versione del Framework eseguendo una ricerca nella `\WINDOWS\Microsoft.NET\Framework` Directory.

   > [!NOTE]
   > Con Windows Server 2003 è possibile installare [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] dall'applicazione **Installazione applicazioni** del Pannello di controllo.

## <a name="see-also"></a>Vedere anche
- [Debug di applicazioni Web: errori e risoluzione dei problemi](../debugger/debugging-web-applications-errors-and-troubleshooting.md)
