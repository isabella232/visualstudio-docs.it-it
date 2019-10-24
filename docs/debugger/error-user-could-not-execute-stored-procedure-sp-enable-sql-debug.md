---
title: "Errore: l'utente non è riuscito a eseguire la stored procedure sp_enable_sql_debug | Microsoft Docs"
ms.date: 11/04/2016
ms.topic: troubleshooting
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3bdc6ecb03572d824f6e3b887090d67be416cdef
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2019
ms.locfileid: "72736544"
---
# <a name="error-user-could-not-execute-stored-procedure-sp_enable_sql_debug"></a>Errore: l'utente non può eseguire la stored procedure sp_enable_sql_debug

Non è possibile eseguire la stored procedure sp_enable_sql_debug sul server. Questo errore può essere causato da:

- Un problema di connessione. È necessario disporre di una connessione stabile al server.

- Mancanza delle autorizzazioni necessarie sul server. Per eseguire il debug in SQL Server 2005, sia l'account con cui viene eseguito Visual Studio che quello utilizzato per la connessione a SQL Server devono essere membri del ruolo sysadmin. L'account utilizzato per la connessione a SQL Server può essere l'account utente di Windows, se si utilizza l'autenticazione di Windows, oppure un account con ID utente e password, se si utilizza l'autenticazione SQL.

Per altre informazioni, vedere [How to: Set SQL Server Permissions for debugging](https://msdn.microsoft.com/84e088d0-0409-41d4-841b-f5d4b0fda414).

## <a name="see-also"></a>Vedere anche

- [Procedura: impostare autorizzazioni di SQL Server per il debug](https://msdn.microsoft.com/84e088d0-0409-41d4-841b-f5d4b0fda414)
- [Impostazione del debug SQL](/previous-versions/visualstudio/visual-studio-2010/s4sszxst\(v\=vs.100\))