---
title: Tipo di dati non supportati
description: Uno o più elementi selezionati contengono un tipo di dati non supportato dalla finestra di progettazione. Visualizzare informazioni su questo Visual Studio O/R Designer.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: error-reference
ms.assetid: 71dcd4f9-2946-42c5-9ce4-99c819ea2785
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 55402288d52f6f4b5eeac41efbb15d9f164ff5cd
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122075151"
---
# <a name="one-or-more-selected-items-contain-a-data-type-that-is-not-supported-by-the-designer"></a>Uno o più elementi selezionati contengono un tipo di dati non supportato dalla finestra di progettazione

Uno o più elementi trascinati da **Esplora server** o **Esplora database in** **O/R Designer** contengono un tipo di dati non supportato da Progettazione **O/R,** ad esempio i tipi [CLR](/dotnet/framework/data/adonet/sql/clr-user-defined-types)definiti dall'utente.

## <a name="to-correct-this-error"></a>Per correggere l'errore

1. Creare una visualizzazione basata sulla tabella desiderata e che non includa il tipo di dati non supportato.

2. Trascinare la visualizzazione **Esplora server** o **Esplora database** nella finestra di progettazione.

## <a name="see-also"></a>Vedi anche

- [LINQ to SQL strumenti in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
