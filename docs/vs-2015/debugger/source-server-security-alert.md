---
title: Avviso di sicurezza del server di origine | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.sourceserver.enablewarning
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 8451c281-6914-469c-b80c-6271cc3f3d17
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 3f8b122deab5dbdc30b129bce221a804f8c53aa3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "65699316"
---
# <a name="source-server-security-alert"></a>Avviso di sicurezza del server di origine
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Quando viene utilizzato il server di origine, utilizzare unicamente file di simboli provenienti da un percorso conosciuto o attendibile.  
  
 Questo avviso viene visualizzato quando si attiva il supporto del server di origine. I comandi del server di origine sono incorporati nei file di simboli del debug (PDB). Assicurarsi di verificare l'origine dei file PDB.  
  
> [!IMPORTANT]
> Quando viene utilizzato il server di origine, è necessario considerare i potenziali pericoli per la sicurezza indicati di seguito. Nel file pdb dell'applicazione possono essere incorporati comandi arbitrari, pertanto assicurarsi di inserire solo i comandi da eseguire nel file srcsrv.ini. Eventuali tentativi di eseguire un comando non presente nel file srcsvr.ini causerà la visualizzazione di una finestra di dialogo di conferma. Per altre informazioni, vedere [avviso di sicurezza: il debugger deve eseguire un comando non attendibile](../debugger/security-warning-debugger-must-execute-untrusted-command.md). Non viene eseguita alcuna convalida sui parametri del comando, quindi prestare attenzione con i comandi attendibili. Se ad esempio si considera attendibile il file cmd.exe, un utente malintenzionato potrebbe specificare parametri in grado di rendere dannoso il comando.  
  
## <a name="see-also"></a>Vedere anche  
 [Specificare i file di simboli (con estensione pdb) e di origine](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)   
 [Sicurezza del debugger](../debugger/debugger-security.md)   
 [Server di origine](https://msdn.microsoft.com/library/windows/desktop/ms680641.aspx)
