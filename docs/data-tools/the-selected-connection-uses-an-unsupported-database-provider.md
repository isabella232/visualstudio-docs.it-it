---
title: Provider di database non supportato
description: La connessione selezionata utilizza un provider di database non supportato. Visualizzare informazioni su questo Visual Studio Object Relational Designer (O/R Designer).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: error-reference
ms.assetid: 4d25dfa1-8fa4-4529-9b90-973bc2ec2993
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: b4956314b994d66e972a9e65a30ee5eb8d8aac13
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126631127"
---
# <a name="the-selected-connection-uses-an-unsupported-database-provider"></a>La connessione selezionata utilizza un provider di database non supportato

Questo messaggio viene visualizzato quando si trascinano elementi che non usano il .NET Framework provider di dati per SQL Server da **Esplora server** o **Esplora database** agli strumenti LINQ to SQL [in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md).

**O/R Designer supporta** solo connessioni dati che usano il provider .NET Framework per SQL Server. Sono valide solo le connessioni a Microsoft SQL Server o a File di database Microsoft SQL Server.

Per correggere l'errore, aggiungere solo gli elementi delle connessioni dati che usano il .NET Framework provider di dati per SQL Server in **O/R Designer.**

## <a name="see-also"></a>Vedi anche

- <xref:System.Data.SqlClient>
- [LINQ to SQL strumenti in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
