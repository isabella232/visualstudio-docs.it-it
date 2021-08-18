---
description: Non è possibile eseguire la stored procedure sp_enable_sql_debug sul server.
title: L'utente non è stato in grado di eseguire la stored procedure sp_enable_sql_debug | Microsoft Docs
ms.date: 11/04/2016
ms.topic: error-reference
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: df25fb20fcf824c09b46a13eb704015d196a2930
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122097168"
---
# <a name="error-user-could-not-execute-stored-procedure-sp_enable_sql_debug"></a>Errore: l'utente non può eseguire la stored procedure sp_enable_sql_debug

Non è possibile eseguire la stored procedure sp_enable_sql_debug sul server. Questo errore può essere causato da:

- Un problema di connessione. È necessario disporre di una connessione stabile al server.

- Mancanza delle autorizzazioni necessarie sul server. Per eseguire il debug in SQL Server 2005, sia l'account con cui viene eseguito Visual Studio che quello utilizzato per la connessione a SQL Server devono essere membri del ruolo sysadmin. L'account utilizzato per la connessione a SQL Server può essere l'account utente di Windows, se si utilizza l'autenticazione di Windows, oppure un account con ID utente e password, se si utilizza l'autenticazione SQL.

Per altre informazioni, vedere [Procedura: Impostare le autorizzazioni SQL Server per il debug](/previous-versions/w1bhybwz(v=vs.100)).

## <a name="see-also"></a>Vedi anche

- [Procedura: impostare le autorizzazioni SQL Server per il debug](/previous-versions/w1bhybwz(v=vs.100))
- [Configurazione del SQL debug](/previous-versions/visualstudio/visual-studio-2010/s4sszxst\(v\=vs.100\))
