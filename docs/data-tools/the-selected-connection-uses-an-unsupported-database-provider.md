---
title: La connessione selezionata utilizza un provider di database non supportato
ms.date: 11/04/2016
ms.topic: error-reference
ms.assetid: 4d25dfa1-8fa4-4529-9b90-973bc2ec2993
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 52b88e1de91c2b2da629b6b9034ac552b8d88d5d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "85281318"
---
# <a name="the-selected-connection-uses-an-unsupported-database-provider"></a>La connessione selezionata utilizza un provider di database non supportato

Questo messaggio viene visualizzato quando si trascinano elementi che non utilizzano l'provider di dati .NET Framework per SQL Server da **Esplora server** o **Esplora database** [negli strumenti di LINQ to SQL in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md).

La **finestra di progettazione di O/R** supporta solo connessioni dati che usano il Provider di .NET Framework per SQL Server. Sono valide solo le connessioni a Microsoft SQL Server o a File di database Microsoft SQL Server.

Per correggere l'errore, aggiungere solo gli elementi delle connessioni dati che usano la .NET Framework provider di dati per SQL Server a **Progettazione relazionale**oggetti.

## <a name="see-also"></a>Vedere anche

- <xref:System.Data.SqlClient>
- [Strumenti LINQ to SQL in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
