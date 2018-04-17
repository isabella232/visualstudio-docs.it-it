---
title: È stato selezionato un oggetto database da un provider di database non supportato | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: c0f1298e-31aa-471e-ae19-1bafffd2ae40
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 5dfb475cdb1b63e4dfcaaebcda4b5d2dc3a7f070
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="you-have-selected-a-database-object-from-an-unsupported-database-provider"></a>È stato selezionato un oggetto di database da un provider di database non supportato
O/R Designer supporta solo il Provider di dati .NET Framework per SQL Server (<xref:System.Data.SqlClient>). Anche se è possibile fare clic su **OK** e continuare a lavorare con gli oggetti di provider del database non supportato, potrebbe verificarsi un comportamento imprevisto in fase di esecuzione.  
  
> [!NOTE]
>  Sono supportate solo connessioni dati che usano il provider di dati .NET Framework per SQL Server.  
  
### <a name="to-correct-this-error"></a>Per correggere l'errore  
  
- Fare clic su **OK**.

   È possibile continuare a progettare le classi di entità con mapping alla connessione che utilizza il provider di database non supportato. Quando si usano provider del database non supportati, potrebbe verificarsi un comportamento imprevisto.  
  
     oppure  
  
- Fare clic su **Annulla**.

   L'azione viene interrotta. Creare o usare una connessione dati che si avvale del provider .NET Framework per SQL Server.  
  
## <a name="see-also"></a>Vedere anche
[Messaggi di Object Relational Designer](../data-tools/o-r-designer-messages.md)  
[Gli strumenti di LINQ to SQL in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)