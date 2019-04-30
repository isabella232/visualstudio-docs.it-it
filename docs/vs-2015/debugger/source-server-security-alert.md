---
title: Avviso di sicurezza di Server di origine | Microsoft Docs
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
ms.openlocfilehash: cc7c68fe767d2add0842e30f66c51a3dcc84905f
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63447283"
---
# <a name="source-server-security-alert"></a>Avviso di sicurezza del server di origine
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Quando viene utilizzato il server di origine, utilizzare unicamente file di simboli provenienti da un percorso conosciuto o attendibile.  
  
 Questo avviso viene visualizzato quando si attiva il supporto del server di origine. I comandi del server di origine sono incorporati nei file di simboli del debug (PDB). Assicurarsi di verificare l'origine dei file PDB.  
  
> [!IMPORTANT]
> I seguenti potenziali minacce alla sicurezza devono essere presi in considerazione quando si usa il Server di origine: I comandi arbitrari possono essere incorporati nel file PDB dell'applicazione, assicurarsi pertanto di che inserire solo quelli da eseguire nel file srcsrv. Eventuali tentativi di eseguire un comando non presente nel file srcsvr.ini causerà la visualizzazione di una finestra di dialogo di conferma. Per altre informazioni, vedere [avviso di sicurezza: Il debugger deve eseguire un comando non attendibile](../debugger/security-warning-debugger-must-execute-untrusted-command.md). Viene eseguita alcuna convalida i parametri dei comandi, prestare attenzione quando si utilizzano comandi attendibili. Se ad esempio si considera attendibile il file cmd.exe, un utente malintenzionato potrebbe specificare parametri in grado di rendere dannoso il comando.  
  
## <a name="see-also"></a>Vedere anche  
 [Specificare file di simboli (PDB) e di origine](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)   
 [Sicurezza del debugger](../debugger/debugger-security.md)   
 [Server di origine](http://msdn.microsoft.com/library/windows/desktop/ms680641.aspx)
