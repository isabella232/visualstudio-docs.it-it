---
title: 'Avviso di sicurezza: Il Debugger deve eseguire un comando non attendibile | Microsoft Docs'
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
- vs.debug.sourceserver.securityalert
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: e5c004b3-b364-4098-ac98-770076ca9981
caps.latest.revision: 16
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b7582004372c5b3de7fdcc23398e4aacf128fcbb
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47517202"
---
# <a name="security-warning-debugger-must-execute-untrusted-command"></a>Avviso di sicurezza: il debugger deve eseguire un comando non attendibile
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [avviso di sicurezza: Debugger Must Execute Untrusted Command](https://docs.microsoft.com/visualstudio/debugger/security-warning-debugger-must-execute-untrusted-command).  
  
Questa finestra di dialogo di avviso viene visualizzata quando si usa il server di origine. Indica che il comando che deve essere eseguito dal debugger per ottenere il codice sorgente non è incluso nell'elenco dei comandi attendibili per il server di origine contenuto nel file srcsvr.ini. Se il comando è valido, è possibile aggiungerlo al file srcsvr.ini. In caso contrario, è opportuno non eseguirlo. Per altre informazioni, vedere [Specifica di file di simboli (con estensione pdb) e di origine](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).  
  
## <a name="message-text"></a>Testo del messaggio  
 **Il debugger deve eseguire questo comando non attendibile per ottenere il codice sorgente dal server di origine.**  
  
 **Se il debug dei file di simboli (\*con estensione pdb) è non da un'origine conosciuta e attendibile, questo comando potrebbe essere non valido o pericoloso da eseguire.**  
  
 **Si desidera eseguire questo comando?**  
  
## <a name="uielement-list"></a>Elenco UIElement  
 Casella di testo  
 Comando del file con estensione pdb da eseguire.  
  
 Run  
 Consente l'esecuzione del comando.  
  
 Non eseguire  
 Arresta l'esecuzione del comando e il download del file dal server di origine.  
  
## <a name="see-also"></a>Vedere anche  
 [Specifica simboli (PDB) e i file di origine](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)   
 [Sicurezza del debugger](../debugger/debugger-security.md)   
 [Server di origine](http://msdn.microsoft.com/library/windows/desktop/ms680641\(v=vs.85\).aspx)



