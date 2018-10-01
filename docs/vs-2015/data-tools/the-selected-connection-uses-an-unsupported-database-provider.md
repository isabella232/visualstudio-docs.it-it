---
title: La connessione selezionata utilizza un provider di database non supportata | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4d25dfa1-8fa4-4529-9b90-973bc2ec2993
caps.latest.revision: 7
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 4e38bda495521bf81c6eb4b9a00a0f32620a71fb
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47518509"
---
# <a name="the-selected-connection-uses-an-unsupported-database-provider"></a>La connessione selezionata utilizza un provider di database non supportato
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [la connessione selezionata utilizza un provider di database non supportato](https://docs.microsoft.com/visualstudio/data-tools/the-selected-connection-uses-an-unsupported-database-provider).  
  
  
Questo messaggio viene visualizzato quando si trascinano gli elementi che non usano il Provider di dati .NET Framework per SQL Server da **Esplora Server**/**Database Explorer** nel [LINQ to SQL Strumenti di Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md).  
  
 [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] supporta solo connessioni dati che usano il provider di dati .NET Framework per SQL Server. Sono valide solo le connessioni a Microsoft SQL Server o a File di database Microsoft SQL Server.  
  
### <a name="to-correct-this-error"></a>Per correggere l'errore  
  
-   Aggiungere a [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] solo gli elementi delle connessioni dati che usano il provider di dati .NET Framework per SQL Server.  
  
## <a name="see-also"></a>Vedere anche  
 <xref:System.Data.SqlClient>   
 [Connessione ai dati in Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Provider di dati .NET framework](http://msdn.microsoft.com/library/03a9fc62-2d24-491a-9fe6-d6bdb6dcb131)   
 [Procedura dettagliata: Creazione di classi LINQ to SQL (O-R Designer)](http://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233)   
 [Creazione di applicazioni dati](../data-tools/creating-data-applications.md)

