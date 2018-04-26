---
title: La connessione selezionata utilizza un provider di database non supportato
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 4d25dfa1-8fa4-4529-9b90-973bc2ec2993
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 77519a5497c26553e2023862e46f3ba618e4f99f
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2018
---
# <a name="the-selected-connection-uses-an-unsupported-database-provider"></a>La connessione selezionata utilizza un provider di database non supportato

Questo messaggio viene visualizzato quando si trascinano gli elementi che non utilizzano il Provider di dati .NET Framework per SQL Server da **Esplora Server**/**Esplora Database** sul [LINQ to SQL Strumenti di Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md).

[!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] supporta solo connessioni dati che usano il provider di dati .NET Framework per SQL Server. Sono valide solo le connessioni a Microsoft SQL Server o a File di database Microsoft SQL Server.

Per correggere l'errore, aggiungere solo gli elementi delle connessioni dati che utilizzano il Provider di dati .NET Framework per SQL Server per il [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].

## <a name="see-also"></a>Vedere anche

- <xref:System.Data.SqlClient>
- [Messaggi di Object Relational Designer](../data-tools/o-r-designer-messages.md)
- [Gli strumenti di LINQ to SQL in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
