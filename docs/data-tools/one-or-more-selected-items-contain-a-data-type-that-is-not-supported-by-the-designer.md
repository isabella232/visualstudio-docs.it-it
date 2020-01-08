---
title: Uno o più elementi selezionati contengono un tipo di dati non supportato dalla finestra di progettazione
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 71dcd4f9-2946-42c5-9ce4-99c819ea2785
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: e2f4911c79ac6d44d2553f3db15c5649dd7160f9
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/01/2020
ms.locfileid: "75586354"
---
# <a name="one-or-more-selected-items-contain-a-data-type-that-is-not-supported-by-the-designer"></a>Uno o più elementi selezionati contengono un tipo di dati non supportato dalla finestra di progettazione

Uno o più elementi trascinati da **Esplora server** o **Esplora database** in **Progettazione relazionale** oggetti contiene un tipo di dati che non è supportato da **o/r designer**, ad esempio i [tipi CLR definiti dall'utente](/dotnet/framework/data/adonet/sql/clr-user-defined-types).

## <a name="to-correct-this-error"></a>Per correggere l'errore

1. Creare una visualizzazione basata sulla tabella desiderata e che non includa il tipo di dati non supportato.

2. Trascinare la vista da **Esplora server** o **Esplora database** nella finestra di progettazione.

## <a name="see-also"></a>Vedere anche

- [Strumenti LINQ to SQL in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
