---
title: È stato selezionato un oggetto di database da un provider di database non supportata | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c0f1298e-31aa-471e-ae19-1bafffd2ae40
caps.latest.revision: 8
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 2c225e00a6d303bff16e30fabd2f3e8e0e9d40ca
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47532028"
---
# <a name="you-have-selected-a-database-object-from-an-unsupported-database-provider"></a>È stato selezionato un oggetto di database da un provider di database non supportato
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [documentazione di Visual Studio 2017](https://docs.microsoft.com/en-us/visualstudio/).  
  
Il [!INCLUDE[vs_ordesigner_long](../includes/vs-ordesigner-long-md.md)] ([!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]) supporta solo il Provider di dati .NET Framework per SQL Server (<xref:System.Data.SqlClient>). Anche se è possibile fare clic su **OK** e continuare a lavorare con gli oggetti di provider di database non supportato, potrebbe verificarsi un comportamento imprevisto in fase di esecuzione.  
  
> [!NOTE]
>  Sono supportate solo connessioni dati che usano il provider di dati .NET Framework per SQL Server.  
  
### <a name="to-correct-this-error"></a>Per correggere l'errore  
  
-   Fare clic su **OK** per continuare a progettare le classi di entità che eseguono il mapping alla connessione che utilizza il provider di database non supportato. Quando si usano provider del database non supportati, potrebbe verificarsi un comportamento imprevisto.  
  
     oppure  
  
-   Fare clic su **annullare**.  
  
     L'azione viene interrotta. Creare o usare una connessione dati che si avvale del provider .NET Framework per SQL Server.  
  
## <a name="see-also"></a>Vedere anche  
 [Strumenti LINQ to SQL in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [LINQ to SQL](http://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655)   
 [Provider di dati .NET framework](http://msdn.microsoft.com/library/03a9fc62-2d24-491a-9fe6-d6bdb6dcb131)   
 [Connessione ai dati in Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)

