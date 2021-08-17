---
description: Questo errore si verifica quando si tenta di eseguire il debug di una routine Transact-SQL o SQLCLR e il debugger non riceve messaggi di debug dal SQL Server.
title: Esecuzione transact-SQL terminata senza eseguire il debug | Microsoft Docs
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
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: f769f7af0412b19be1addd0b556a647c5d8041bd9b3c3f48e0022315d3519bc9
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121419923"
---
# <a name="error-transact-sql-execution-ended-without-debugging"></a>Errore: esecuzione Transact-SQL terminata senza debug

Questo errore si verifica quando si tenta di eseguire il debug di una routine Transact-SQL o SQLCLR e il debugger non riceve messaggi di debug dal SQL Server.

Questo problema può essere dovuto a problemi di rete o a problemi nel SQL Server, ma la causa più probabile è un problema di autorizzazioni.

Questo problema riguarda due account:

- L'account dell'applicazione è l'account utente utilizzato per l'esecuzione di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].

- L'account di connessione è l'identità utilizzata per effettuare la connessione a SQL Server. Questo account non corrisponde necessariamente all'identità che Visual Studio viene eseguita come se la connessione usa l'SQL autenticazione.

  SQL il debug richiede che l'account dell'applicazione corrisponda all'account di connessione o che sia un amministratore di sistema.

  Se si usa un nome di account SQL come sa, l'account dell'applicazione deve essere configurato nel SQL Server come amministratore di sistema. Per impostazione predefinita, gli amministratori nel computer SQL server in cui è in esecuzione SQL Server sysadmins.

  Per correggere questo errore, è possibile:

  - Verificare le impostazioni delle autorizzazioni. Per altre informazioni, vedere [Procedura: Impostare le autorizzazioni SQL Server per il debug.](/previous-versions/w1bhybwz(v=vs.100))

  - Assicurarsi che il debug SQL sia configurato correttamente.

  - Consultare l'amministratore della rete o del database.

## <a name="see-also"></a>Vedi anche

- [Configurazione del SQL debug](/previous-versions/visualstudio/visual-studio-2010/s4sszxst(v=vs.100))
- [Procedura: impostare le autorizzazioni SQL Server per il debug](/previous-versions/w1bhybwz(v=vs.100))
- [Attività Impostazioni e preparazione del debugger](../debugger/debugger-settings-and-preparation.md)
- [Debug remoto](../debugger/remote-debugging.md)
