---
title: "Errore: L'utente non può eseguire Stored Procedure sp_enable_sql_debug | Microsoft Docs"
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.sqlde_accessdenied
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 795dcb07459318326085d5e1fe99554d9c8d1311
ms.sourcegitcommit: bc43970c000f07c9cc2051f1264a9742943a9755
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/09/2018
ms.locfileid: "51349504"
---
# <a name="error-user-could-not-execute-stored-procedure-spenablesqldebug"></a>Errore: l'utente non può eseguire la stored procedure sp_enable_sql_debug
Non è possibile eseguire la stored procedure sp_enable_sql_debug sul server. Questo errore può essere causato da:  
  
- Un problema di connessione. È necessario disporre di una connessione stabile al server.  
  
- Mancanza delle autorizzazioni necessarie sul server. Per eseguire il debug in SQL Server 2005, sia l'account con cui viene eseguito Visual Studio che quello utilizzato per la connessione a SQL Server devono essere membri del ruolo sysadmin. L'account utilizzato per la connessione a SQL Server può essere l'account utente di Windows, se si utilizza l'autenticazione di Windows, oppure un account con ID utente e password, se si utilizza l'autenticazione SQL.  
  
  Per altre informazioni, vedere [procedura: impostare delle autorizzazioni di SQL Server per il debug](https://msdn.microsoft.com/84e088d0-0409-41d4-841b-f5d4b0fda414).  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura: impostare le autorizzazioni di SQL Server per il debug](https://msdn.microsoft.com/84e088d0-0409-41d4-841b-f5d4b0fda414)   
 [Configurazione di debug SQL](/previous-versions/visualstudio/visual-studio-2010/s4sszxst\(v\=vs.100\))