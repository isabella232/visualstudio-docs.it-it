---
title: Oggetto da provider non supportato
description: È stato selezionato un oggetto di database da un provider di database non supportato
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: error-reference
ms.assetid: c0f1298e-31aa-471e-ae19-1bafffd2ae40
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 84841c5e0759618430f9c2e4f0146cbc2d21fae9
ms.sourcegitcommit: 4ae5e9817ad13edd05425febb322b5be6d3c3425
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/11/2020
ms.locfileid: "90036717"
---
# <a name="you-have-selected-a-database-object-from-an-unsupported-database-provider"></a>È stato selezionato un oggetto di database da un provider di database non supportato

La **finestra di progettazione O/R** supporta solo i provider di dati .NET Framework per SQL Server ( <xref:System.Data.SqlClient> ). Anche se è possibile fare clic su **OK** e continuare a usare gli oggetti di provider del database non supportati, potrebbe verificarsi un comportamento imprevisto in fase di esecuzione.

> [!NOTE]
> Sono supportate solo connessioni dati che usano il provider di dati .NET Framework per SQL Server.

## <a name="options"></a>Opzioni

- Fare clic su **OK** per continuare a progettare le classi di entità con mapping alla connessione che usa il provider del database non supportato. Quando si usano provider del database non supportati, potrebbe verificarsi un comportamento imprevisto.

- Fare clic su **Annulla** per arrestare l'azione. Creare o usare una connessione dati diversa che usi il provider di .NET Framework per SQL Server.

## <a name="see-also"></a>Vedi anche

- [Strumenti di LINQ to SQL in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
