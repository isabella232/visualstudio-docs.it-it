---
title: 'Errore: Esecuzione di Transact-SQL terminata senza debug | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.error.sqlde_sql_executed_but_not_debugged
dev_langs:
- FSharp
- VB
- CSharp
- C++
- SQL
ms.assetid: 7a4d4999-3973-4339-ba6a-f0d19bcb1d4a
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 910b84e7a024547208ea2e7ae1d6a6897cf60893
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62431888"
---
# <a name="error-transact-sql-execution-ended-without-debugging"></a>Errore: Esecuzione di Transact-SQL terminata senza debug
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Questo errore si verifica quando si tenta di eseguire il debug di una routine Transact-SQL o SQLCLR e il debugger non riceve messaggi di debug da SQL Server.  
  
 L'errore può essere dovuto a problemi di rete o a problemi su SQL Server, ma con maggiore probabilità è dovuto a un problema di autorizzazioni.  
  
 Questo problema riguarda due account:  
  
- L'account dell'applicazione è l'account utente utilizzato per l'esecuzione di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
- L'account di connessione è l'identità utilizzata per effettuare la connessione a SQL Server. Nel caso di una connessione con autenticazione SQL, questo account non corrisponde necessariamente all'identità utilizzata per l'esecuzione di Visual Studio.  
  
  Per il debug SQL è necessario che l'account dell'applicazione corrisponda a quello di connessione oppure che sia sysadmin.  
  
  Se si utilizza un account di accesso SQL quale sa, l'account dell'applicazione deve essere configurato su SQL Server come sysadmin. Per impostazione predefinita, gli amministratori del computer sul quale è in esecuzione SQL Server sono configurati come account sysadmin.  
  
  Per correggere questo errore, è possibile:  
  
- Verificare le impostazioni delle autorizzazioni. Per altre informazioni, vedere [Procedura: Impostare autorizzazioni di SQL Server per il debug](http://msdn.microsoft.com/84e088d0-0409-41d4-841b-f5d4b0fda414).  
  
- Assicurarsi che il debug SQL sia configurato correttamente.  
  
- Consultare l'amministratore della rete o del database.  
  
## <a name="see-also"></a>Vedere anche  
 [Configurazione di debug SQL](http://msdn.microsoft.com/3db09e68-edcc-42de-9c22-4e97cfd55ab3)   
 [Procedura: Impostare autorizzazioni di SQL Server per il debug](http://msdn.microsoft.com/84e088d0-0409-41d4-841b-f5d4b0fda414)   
 [Debugger Settings and Preparation](../debugger/debugger-settings-and-preparation.md)  (Impostazioni di debug e preparazione)  
 [Remote Debugging](../debugger/remote-debugging.md)
