---
title: 'Errore: Utente non può eseguire Stored Procedure sp_enable_sql_debug | Microsoft Docs'
ms.date: 11/04/2016
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
ms.openlocfilehash: 9c80a4055b899f155b4be8e7832df9f3aa22db20
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53903578"
---
# <a name="error-user-could-not-execute-stored-procedure-spenablesqldebug"></a>Errore: L'utente non è riuscito a eseguire la stored procedure sp_enable_sql_debug

Non è possibile eseguire la stored procedure sp_enable_sql_debug sul server. Questo errore può essere causato da:

- Un problema di connessione. È necessario disporre di una connessione stabile al server.

- Mancanza delle autorizzazioni necessarie sul server. Per eseguire il debug in SQL Server 2005, sia l'account con cui viene eseguito Visual Studio che quello utilizzato per la connessione a SQL Server devono essere membri del ruolo sysadmin. L'account utilizzato per la connessione a SQL Server può essere l'account utente di Windows, se si utilizza l'autenticazione di Windows, oppure un account con ID utente e password, se si utilizza l'autenticazione SQL.

Per altre informazioni, vedere [Procedura: Impostare autorizzazioni di SQL Server per il debug](https://msdn.microsoft.com/84e088d0-0409-41d4-841b-f5d4b0fda414).

## <a name="see-also"></a>Vedere anche

- [Procedura: Impostare autorizzazioni di SQL Server per il debug](https://msdn.microsoft.com/84e088d0-0409-41d4-841b-f5d4b0fda414)
- [Configurazione di debug SQL](/previous-versions/visualstudio/visual-studio-2010/s4sszxst\(v\=vs.100\))