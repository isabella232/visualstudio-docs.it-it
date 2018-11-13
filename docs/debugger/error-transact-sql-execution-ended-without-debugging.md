---
title: 'Errore: Esecuzione Transact-SQL terminata senza debug | Microsoft Docs'
ms.custom: ''
ms.date: 11/08/2018
ms.technology: vs-ide-debug
ms.topic: troubleshooting
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0efb83f6b6cbebc255f6f47c30e3934d74de7870
ms.sourcegitcommit: bc43970c000f07c9cc2051f1264a9742943a9755
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/09/2018
ms.locfileid: "51349007"
---
# <a name="error-transact-sql-execution-ended-without-debugging"></a>Errore: esecuzione Transact-SQL terminata senza debug

Questo errore si verifica quando si sta tentando di eseguire il debug di una Transact-SQL o una routine SQLCLR e il debugger non riceve i messaggi di debug da SQL Server.  
  
Questo problema potrebbe essere a causa di problemi di rete o a problemi su SQL Server, ma la causa più probabile è un problema di autorizzazioni.  
  
Questo problema riguarda due account:  
  
- L'account dell'applicazione è l'account utente utilizzato per l'esecuzione di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
- L'account di connessione è l'identità utilizzata per effettuare la connessione a SQL Server. Questo account non è necessariamente lo stesso come l'identità che esegue Visual Studio come se la connessione con autenticazione SQL.  
  
  Debug SQL è necessario che l'account dell'applicazione deve corrispondere all'account di connessione oppure essere un amministratore di sistema.  
  
  Se si usa un nome dell'account SQL quale sa, l'applicazione account deve essere configurato in SQL Server come membri del ruolo sysadmin. Per impostazione predefinita, gli amministratori nel computer che esegue SQL server su sono gli amministratori di sistema di SQL Server.  
  
  Per correggere questo errore, è possibile:  
  
  - Verificare le impostazioni delle autorizzazioni. Per altre informazioni, vedere [procedura: impostare delle autorizzazioni di SQL Server per il debug](https://msdn.microsoft.com/84e088d0-0409-41d4-841b-f5d4b0fda414).  
  
  - Assicurarsi che il debug SQL sia configurato correttamente.  
  
  - Consultare l'amministratore della rete o del database.  
  
## <a name="see-also"></a>Vedere anche

- [Configurazione di debug SQL](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/s4sszxst(v=vs.100))
- [Procedura: impostare le autorizzazioni di SQL Server per il debug](https://msdn.microsoft.com/84e088d0-0409-41d4-841b-f5d4b0fda414)
- [Impostazioni di debug e preparazione](../debugger/debugger-settings-and-preparation.md)
- [Remote Debugging](../debugger/remote-debugging.md)