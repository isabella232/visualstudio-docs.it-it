---
title: Errore-l'utente non è riuscito a eseguire la stored procedure sp_enable_sql_debug | Microsoft Docs
ms.date: 11/04/2016
ms.topic: error-reference
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
ms.openlocfilehash: 84326c5c1beb91269a5f097c8c5d7cb8782a7a56
ms.sourcegitcommit: ed4372bb6f4ae64f1fd712b2b253bf91d9ff96bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/09/2020
ms.locfileid: "89600143"
---
# <a name="error-user-could-not-execute-stored-procedure-sp_enable_sql_debug"></a>Errore: l'utente non può eseguire la stored procedure sp_enable_sql_debug

Non è possibile eseguire la stored procedure sp_enable_sql_debug sul server. Questo errore può essere causato da:

- Un problema di connessione. È necessario disporre di una connessione stabile al server.

- Mancanza delle autorizzazioni necessarie sul server. Per eseguire il debug in SQL Server 2005, sia l'account con cui viene eseguito Visual Studio che quello utilizzato per la connessione a SQL Server devono essere membri del ruolo sysadmin. L'account utilizzato per la connessione a SQL Server può essere l'account utente di Windows, se si utilizza l'autenticazione di Windows, oppure un account con ID utente e password, se si utilizza l'autenticazione SQL.

Per altre informazioni, vedere [How to: Set SQL Server Permissions for debugging](/previous-versions/w1bhybwz(v=vs.100)).

## <a name="see-also"></a>Vedi anche

- [Procedura: impostare le autorizzazioni SQL Server per il debug](/previous-versions/w1bhybwz(v=vs.100))
- [Impostazione del debug SQL](/previous-versions/visualstudio/visual-studio-2010/s4sszxst\(v\=vs.100\))