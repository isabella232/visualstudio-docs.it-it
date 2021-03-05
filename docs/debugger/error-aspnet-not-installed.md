---
description: Questo errore si verifica quando ASP.NET non è installato correttamente nel computer che si sta tentando di eseguire il debug.
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
manager: jmartens
ms.workload:
- aspnet
ms.openlocfilehash: 205f0fb3948414ec87b735af9b1b97917872a950
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2021
ms.locfileid: "102147055"
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

## <a name="see-also"></a>Vedi anche
- [Debug di applicazioni Web: errori e risoluzione dei problemi](../debugger/debugging-web-applications-errors-and-troubleshooting.md)
