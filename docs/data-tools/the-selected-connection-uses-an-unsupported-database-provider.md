---
title: La connessione selezionata utilizza un provider di database non supportato
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 4d25dfa1-8fa4-4529-9b90-973bc2ec2993
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 5fab6be50a9b4c273a7bb911d8afde5cf65d7676
ms.sourcegitcommit: 50f0c3f2763a05de8482b3579026d9c76c0e226c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/09/2019
ms.locfileid: "65460574"
---
# <a name="the-selected-connection-uses-an-unsupported-database-provider"></a>La connessione selezionata utilizza un provider di database non supportato

Questo messaggio viene visualizzato quando si trascinano gli elementi che non usano il Provider di dati .NET Framework per SQL Server da **Esplora Server** oppure **Esplora Database** nel [gli strumenti di LINQ to SQL in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md).

Il **O/R Designer** supporta solo le connessioni dati che utilizzano il Provider .NET Framework per SQL Server. Sono valide solo le connessioni a Microsoft SQL Server o a File di database Microsoft SQL Server.

Per correggere questo errore, aggiungere solo gli elementi delle connessioni dati che utilizzano il Provider di dati .NET Framework per SQL Server per il **O/R Designer**.

## <a name="see-also"></a>Vedere anche

- <xref:System.Data.SqlClient>
- [Strumenti LINQ to SQL in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
