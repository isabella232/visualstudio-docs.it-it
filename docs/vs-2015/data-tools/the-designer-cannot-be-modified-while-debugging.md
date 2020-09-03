---
title: Impossibile modificare la finestra di progettazione durante il debug | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: 487dafe4-d57c-4be1-9e3a-bb0a8699b2fa
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a8e393ad46b6d37bd74806a0a4b84825bd059457
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "72672266"
---
# <a name="the-designer-cannot-be-modified-while-debugging"></a>Impossibile modificare la finestra di progettazione durante il debug
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Questo messaggio viene visualizzato quando si tenta di modificare elementi in Progettazione relazionale oggetti durante l'esecuzione dell'applicazione in modalità di debug. Quando l'applicazione è in esecuzione in tale modalità, Progettazione relazionale oggetti è di sola lettura.

### <a name="to-correct-this-error"></a>Per correggere l'errore

- Scegliere **Interrompi debug** dal menu **debug** .

     Il debug viene interrotto e sarà quindi possibile modificare gli elementi in Progettazione relazionale oggetti.

## <a name="see-also"></a>Vedere anche
 [Strumenti di LINQ to SQL in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) [procedura dettagliata: creazione di classi LINQ to SQL (O-R Designer)](https://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233) [LINQ to SQL](https://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655)
