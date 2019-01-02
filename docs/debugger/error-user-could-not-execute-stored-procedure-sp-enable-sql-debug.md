---
title: 'Errore: Utente non può eseguire Stored Procedure sp_enable_sql_debug | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: troubleshooting
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
ms.openlocfilehash: 7b121b863237a3b12b5131be348581ea3fd043d2
ms.sourcegitcommit: 75e02ed88a1ace6e8265fd4e3a82a1bc78f3adca
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 12/13/2018
ms.locfileid: "53348574"
---
# <a name="error-user-could-not-execute-stored-procedure-spenablesqldebug"></a>Errore: L'utente non è riuscito a eseguire la stored procedure sp_enable_sql_debug

Non è possibile eseguire la stored procedure sp_enable_sql_debug sul server. Questo errore può essere causato da:

- Un problema di connessione. È necessario disporre di una connessione stabile al server.

- Mancanza delle autorizzazioni necessarie sul server. Per eseguire il debug in SQL Server 2005, sia l'account con cui viene eseguito Visual Studio che quello utilizzato per la connessione a SQL Server devono essere membri del ruolo sysadmin. L'account utilizzato per la connessione a SQL Server può essere l'account utente di Windows, se si utilizza l'autenticazione di Windows, oppure un account con ID utente e password, se si utilizza l'autenticazione SQL.

Per altre informazioni, vedere [Procedura: Impostare autorizzazioni di SQL Server per il debug](https://msdn.microsoft.com/84e088d0-0409-41d4-841b-f5d4b0fda414).

## <a name="see-also"></a>Vedere anche

- [Procedura: Impostare autorizzazioni di SQL Server per il debug](https://msdn.microsoft.com/84e088d0-0409-41d4-841b-f5d4b0fda414)
- [Configurazione di debug SQL](/previous-versions/visualstudio/visual-studio-2010/s4sszxst\(v\=vs.100\))