---
title: Avviso di sicurezza di Server di origine | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.sourceserver.enablewarning
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 8451c281-6914-469c-b80c-6271cc3f3d17
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8f75ae71cb03e4811e5fa0599bd1ee51371c7891
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49230100"
---
# <a name="source-server-security-alert"></a>Avviso di sicurezza del server di origine
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Quando viene utilizzato il server di origine, utilizzare unicamente file di simboli provenienti da un percorso conosciuto o attendibile.  
  
 Questo avviso viene visualizzato quando si attiva il supporto del server di origine. I comandi del server di origine sono incorporati nei file di simboli del debug (PDB). Assicurarsi di verificare l'origine dei file PDB.  
  
> [!IMPORTANT]
>  Quando viene utilizzato il server di origine, è necessario considerare i potenziali pericoli per la sicurezza indicati di seguito. Nel file pdb dell'applicazione possono essere incorporati comandi arbitrari, pertanto assicurarsi di inserire solo i comandi da eseguire nel file srcsrv.ini. Eventuali tentativi di eseguire un comando non presente nel file srcsvr.ini causerà la visualizzazione di una finestra di dialogo di conferma. Per altre informazioni, vedere [avviso di sicurezza: Debugger Must Execute Untrusted Command](../debugger/security-warning-debugger-must-execute-untrusted-command.md). Viene eseguita alcuna convalida i parametri dei comandi, prestare attenzione quando si utilizzano comandi attendibili. Se ad esempio si considera attendibile il file cmd.exe, un utente malintenzionato potrebbe specificare parametri in grado di rendere dannoso il comando.  
  
## <a name="see-also"></a>Vedere anche  
 [Specifica simboli (PDB) e i file di origine](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)   
 [Sicurezza del debugger](../debugger/debugger-security.md)   
 [Server di origine](http://msdn.microsoft.com/library/windows/desktop/ms680641.aspx)



