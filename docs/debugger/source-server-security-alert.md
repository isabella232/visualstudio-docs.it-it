---
title: Avviso di sicurezza del server di origine | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug.sourceserver.enablewarning
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: 8451c281-6914-469c-b80c-6271cc3f3d17
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 69511c2f83570abf37ef4bea8b71c8f59431a128
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "72729565"
---
# <a name="source-server-security-alert"></a>Avviso di sicurezza del server di origine
Quando viene utilizzato il server di origine, utilizzare unicamente file di simboli provenienti da un percorso conosciuto o attendibile.

 Questo avviso viene visualizzato quando si attiva il supporto del server di origine. I comandi del server di origine sono incorporati nei file di simboli di debug (file con** \* estensione PDB** ). Assicurarsi di verificare l'origine dei file PDB.

> [!IMPORTANT]
> Quando viene utilizzato il server di origine, è necessario considerare i potenziali pericoli per la sicurezza indicati di seguito. Nel file pdb dell'applicazione possono essere incorporati comandi arbitrari, pertanto assicurarsi di inserire solo i comandi da eseguire nel file srcsrv.ini. Eventuali tentativi di eseguire un comando non presente nel file srcsvr.ini causerà la visualizzazione di una finestra di dialogo di conferma. Per altre informazioni, vedere [Security Warning: Debugger Must Execute Untrusted Command](../debugger/security-warning-debugger-must-execute-untrusted-command.md). Poiché non viene eseguita alcuna convalida sui parametri dei comandi, prestare attenzione nell'utilizzare i comandi attendibili. Se ad esempio si considera attendibile il file cmd.exe, un utente malintenzionato potrebbe specificare parametri in grado di rendere dannoso il comando.

## <a name="see-also"></a>Vedere anche
- [Specificare file di simboli (PDB) e di origine](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)
- [Sicurezza del debugger](../debugger/debugger-security.md)
- [Server di origine](/windows/desktop/Debug/source-server-and-source-indexing)
