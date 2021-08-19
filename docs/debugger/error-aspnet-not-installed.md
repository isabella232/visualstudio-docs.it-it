---
description: Questo errore si verifica quando ASP.NET non è installato correttamente nel computer di cui si sta tentando di eseguire il debug.
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
ms.technology: vs-ide-debug
ms.workload:
- aspnet
ms.openlocfilehash: f368d08ec7af90cf51a68fbf8244f82fa178451c
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122121190"
---
# <a name="error-aspnet-not-installed"></a>Errore: ASP.NET non è installato
Questo errore si verifica quando [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] non è installato correttamente nel computer di cui si sta tentando di eseguire il debug. Questo errore potrebbe essere dovuto al fatto che [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] non è mai stato installato o che [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] è stato installato prima di IIS.

### <a name="to-reinstall-aspnet"></a>Per reinstallare ASP.NET

1. Da una finestra del prompt dei comandi eseguire il comando seguente:

   ```cmd
   \WINDOWS\Microsoft.NET\Framework\version\aspnet_regiis -i
   ```

    dove *version* rappresenta il numero di versione del .NET Framework installato nel computer, ad esempio v1.0.370. È possibile determinare la versione del framework cercando nella `\WINDOWS\Microsoft.NET\Framework` directory .

   > [!NOTE]
   > Con Windows Server 2003 è possibile installare [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] dall'applicazione **Installazione applicazioni** del Pannello di controllo.

## <a name="see-also"></a>Vedi anche
- [Debug di applicazioni Web: errori e risoluzione dei problemi](../debugger/debugging-web-applications-errors-and-troubleshooting.md)
