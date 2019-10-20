---
title: La connessione selezionata utilizza un provider di database non supportato | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: 4d25dfa1-8fa4-4529-9b90-973bc2ec2993
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 4e79d8408fba54cf192d51f9d2ead8c0ffafe1f0
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72667187"
---
# <a name="the-selected-connection-uses-an-unsupported-database-provider"></a>La connessione selezionata utilizza un provider di database non supportato
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Questo messaggio viene visualizzato quando si trascinano elementi che non utilizzano l'provider di dati .NET Framework per SQL Server da **Esplora server** **/ Esplora database** [negli strumenti di LINQ to SQL in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md).

 [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] supporta solo connessioni dati che usano il provider di dati .NET Framework per SQL Server. Sono valide solo le connessioni a Microsoft SQL Server o a File di database Microsoft SQL Server.

### <a name="to-correct-this-error"></a>Per correggere l'errore

- Aggiungere a [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] solo gli elementi delle connessioni dati che usano il provider di dati .NET Framework per SQL Server.

## <a name="see-also"></a>Vedere anche
 <xref:System.Data.SqlClient> [.NET Framework i provider di dati](https://msdn.microsoft.com/library/03a9fc62-2d24-491a-9fe6-d6bdb6dcb131) [procedura dettagliata: creazione di classi di LINQ to SQL (O-R Designer)](https://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233)