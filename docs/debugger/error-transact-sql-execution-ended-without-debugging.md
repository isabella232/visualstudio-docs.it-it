---
title: Errore-esecuzione Transact-SQL terminata senza debug | Microsoft Docs
ms.date: 11/08/2018
ms.topic: error-reference
f1_keywords:
- vs.debug.error.sqlde_sql_executed_but_not_debugged
dev_langs:
- CSharp
- VB
- FSharp
- C++
- SQL
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e141fac7fba1939811c722d8e08f49531111ff7e
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/27/2020
ms.locfileid: "85460247"
---
# <a name="error-transact-sql-execution-ended-without-debugging"></a>Errore: esecuzione Transact-SQL terminata senza debug

Questo errore si verifica quando si tenta di eseguire il debug di una procedura Transact-SQL o SQLCLR e il debugger non riceve messaggi di debug dal SQL Server.

Questo problema può essere causato da problemi di rete o da problemi di SQL Server, ma la causa più probabile è un problema relativo alle autorizzazioni.

Questo problema riguarda due account:

- L'account dell'applicazione è l'account utente utilizzato per l'esecuzione di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].

- L'account di connessione è l'identità utilizzata per effettuare la connessione a SQL Server. Questo account non è necessariamente uguale all'identità che viene eseguita da Visual Studio come se la connessione utilizza l'autenticazione SQL.

  Per il debug SQL è necessario che l'account dell'applicazione corrisponda all'account di connessione oppure che sia un sysadmin.

  Se si usa un nome di account SQL come sa, l'account dell'applicazione deve essere configurato nel SQL Server come amministratore di sistema. Per impostazione predefinita, gli amministratori del computer in cui è in esecuzione SQL Server sono SQL Server sysadmin.

  Per correggere questo errore, è possibile:

  - Verificare le impostazioni delle autorizzazioni. Per altre informazioni, vedere [How to: Set SQL Server Permissions for debugging](https://msdn.microsoft.com/84e088d0-0409-41d4-841b-f5d4b0fda414).

  - Assicurarsi che il debug SQL sia configurato correttamente.

  - Consultare l'amministratore della rete o del database.

## <a name="see-also"></a>Vedi anche

- [Impostazione del debug SQL](/previous-versions/visualstudio/visual-studio-2010/s4sszxst(v=vs.100))
- [Procedura: impostare le autorizzazioni SQL Server per il debug](https://msdn.microsoft.com/84e088d0-0409-41d4-841b-f5d4b0fda414)
- [Impostazioni di debug e preparazione](../debugger/debugger-settings-and-preparation.md)
- [Debug remoto](../debugger/remote-debugging.md)