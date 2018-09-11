---
title: 'Errore: Esecuzione Transact-SQL terminata senza debug | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
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
ms.openlocfilehash: 5e6ae81608ee476e3748fde6830dfaa11c119f7a
ms.sourcegitcommit: 1ab675a872848c81a44d6b4bd3a49958fe673c56
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/10/2018
ms.locfileid: "44283132"
---
# <a name="error-transact-sql-execution-ended-without-debugging"></a>Errore: esecuzione Transact-SQL terminata senza debug
Questo errore si verifica quando si tenta di eseguire il debug di una routine Transact-SQL o SQLCLR e il debugger non riceve messaggi di debug da SQL Server.  
  
 L'errore può essere dovuto a problemi di rete o a problemi su SQL Server, ma con maggiore probabilità è dovuto a un problema di autorizzazioni.  
  
 Questo problema riguarda due account:  
  
-   L'account dell'applicazione è l'account utente utilizzato per l'esecuzione di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
-   L'account di connessione è l'identità utilizzata per effettuare la connessione a SQL Server. Nel caso di una connessione con autenticazione SQL, questo account non corrisponde necessariamente all'identità utilizzata per l'esecuzione di Visual Studio.  
  
 Per il debug SQL è necessario che l'account dell'applicazione corrisponda a quello di connessione oppure che sia sysadmin.  
  
 Se si utilizza un account di accesso SQL quale sa, l'account dell'applicazione deve essere configurato su SQL Server come sysadmin. Per impostazione predefinita, gli amministratori del computer sul quale è in esecuzione SQL Server sono configurati come account sysadmin.  
  
 Per correggere questo errore, è possibile:  
  
-   Verificare le impostazioni delle autorizzazioni. Per altre informazioni, vedere [procedura: impostare delle autorizzazioni di SQL Server per il debug](http://msdn.microsoft.com/en-us/84e088d0-0409-41d4-841b-f5d4b0fda414).  
  
-   Assicurarsi che il debug SQL sia configurato correttamente.  
  
-   Consultare l'amministratore della rete o del database.  
  
## <a name="see-also"></a>Vedere anche  
 [Configurazione di debug SQL](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/s4sszxst(v=vs.100))   
 [Procedura: impostare le autorizzazioni di SQL Server per il debug](http://msdn.microsoft.com/en-us/84e088d0-0409-41d4-841b-f5d4b0fda414)   
 [Debugger Settings and Preparation](../debugger/debugger-settings-and-preparation.md)  (Impostazioni di debug e preparazione)  
 [Debug remoto](../debugger/remote-debugging.md)