---
title: Oggetto da un provider non supportato
description: È stato selezionato un oggetto di database da un provider di database non supportato. Visualizzare informazioni su questo Visual Studio (O/R Designer).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: error-reference
ms.assetid: c0f1298e-31aa-471e-ae19-1bafffd2ae40
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 33c69dca90a7fa662356ac648b6a53dfe893050a539dfdf9a4b612806022e0e2
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121346427"
---
# <a name="you-have-selected-a-database-object-from-an-unsupported-database-provider"></a>È stato selezionato un oggetto di database da un provider di database non supportato

**O/R Designer supporta** solo le .NET Framework provider di dati per SQL Server ( <xref:System.Data.SqlClient> ). Anche se è possibile fare clic su **OK** e continuare a usare gli oggetti di provider del database non supportati, potrebbe verificarsi un comportamento imprevisto in fase di esecuzione.

> [!NOTE]
> Sono supportate solo connessioni dati che usano il provider di dati .NET Framework per SQL Server.

## <a name="options"></a>Opzioni

- Fare clic su **OK** per continuare a progettare le classi di entità con mapping alla connessione che usa il provider del database non supportato. Quando si usano provider del database non supportati, potrebbe verificarsi un comportamento imprevisto.

- Fare **clic su** Annulla per arrestare l'azione. Creare o usare una connessione dati diversa che usa il provider .NET Framework per SQL Server.

## <a name="see-also"></a>Vedi anche

- [LINQ to SQL strumenti in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
