---
title: È stato selezionato un oggetto di database da un provider di database non supportato
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: c0f1298e-31aa-471e-ae19-1bafffd2ae40
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: dae92f404bb9ecb23b77dbda33c329994b9ed15b
ms.sourcegitcommit: 50f0c3f2763a05de8482b3579026d9c76c0e226c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/09/2019
ms.locfileid: "65457871"
---
# <a name="you-have-selected-a-database-object-from-an-unsupported-database-provider"></a>È stato selezionato un oggetto di database da un provider di database non supportato

Il **O/R Designer** supporta solo il Provider di dati .NET Framework per SQL Server (<xref:System.Data.SqlClient>). Anche se è possibile fare clic su **OK** e continuare a usare gli oggetti di provider del database non supportati, potrebbe verificarsi un comportamento imprevisto in fase di esecuzione.

> [!NOTE]
> Sono supportate solo connessioni dati che usano il provider di dati .NET Framework per SQL Server.

## <a name="options"></a>Opzioni

- Fare clic su **OK** per continuare a progettare le classi di entità con mapping alla connessione che usa il provider del database non supportato. Quando si usano provider del database non supportati, potrebbe verificarsi un comportamento imprevisto.

- Fare clic su **annullare** per arrestare l'azione. Creare o usare una connessione dati diversa che usa il Provider .NET Framework per SQL Server.

## <a name="see-also"></a>Vedere anche

- [Strumenti LINQ to SQL in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)