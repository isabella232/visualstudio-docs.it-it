---
title: 'Errore: ASP.NET non è installato | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: troubleshooting
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
ms.openlocfilehash: 98db3475c7d83427eb516f696731a738e34bd7a1
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63399300"
---
# <a name="error-aspnet-not-installed"></a>Errore: ASP.NET non è installato
Questo errore si verifica quando [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] non è installato correttamente nel computer di cui si sta tentando di eseguire il debug. Questo errore potrebbe essere dovuto al fatto che [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] non è mai stato installato o che [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] è stato installato prima di IIS.

### <a name="to-reinstall-aspnet"></a>Per reinstallare ASP.NET

1. Da una finestra del prompt dei comandi eseguire il comando seguente:

   ```cmd
   \WINDOWS\Microsoft.NET\Framework\version\aspnet_regiis -i
   ```

    in cui *versione* rappresenta il numero di versione di .NET Framework installata nel computer, ad esempio v1.0.370. È possibile determinare la versione del framework esaminando il `\WINDOWS\Microsoft.NET\Framework` directory.

   > [!NOTE]
   > Con Windows Server 2003 è possibile installare [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] dall'applicazione **Installazione applicazioni** del Pannello di controllo.

## <a name="see-also"></a>Vedere anche
- [Debug di applicazioni Web: Errori e risoluzione dei problemi](../debugger/debugging-web-applications-errors-and-troubleshooting.md)
