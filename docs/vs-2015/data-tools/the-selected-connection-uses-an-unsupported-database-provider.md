---
title: La connessione selezionata utilizza un provider di database non supportata | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: 4d25dfa1-8fa4-4529-9b90-973bc2ec2993
caps.latest.revision: 7
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 3db964387209b833437e1ffc4dbc3a26689729ed
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60061413"
---
# <a name="the-selected-connection-uses-an-unsupported-database-provider"></a>La connessione selezionata utilizza un provider di database non supportato
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Questo messaggio viene visualizzato quando si trascinano gli elementi che non usano il Provider di dati .NET Framework per SQL Server da **Esplora Server**/**Database Explorer** nel [LINQ to SQL Strumenti di Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md).  
  
 [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] supporta solo connessioni dati che usano il provider di dati .NET Framework per SQL Server. Sono valide solo le connessioni a Microsoft SQL Server o a File di database Microsoft SQL Server.  
  
### <a name="to-correct-this-error"></a>Per correggere l'errore  
  
- Aggiungere a [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] solo gli elementi delle connessioni dati che usano il provider di dati .NET Framework per SQL Server.  
  
## <a name="see-also"></a>Vedere anche  
 <xref:System.Data.SqlClient>   
 [Provider di dati .NET framework](http://msdn.microsoft.com/library/03a9fc62-2d24-491a-9fe6-d6bdb6dcb131)   
 [Procedura dettagliata: Creazione di classi LINQ to SQL (O-R Designer)](http://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233)