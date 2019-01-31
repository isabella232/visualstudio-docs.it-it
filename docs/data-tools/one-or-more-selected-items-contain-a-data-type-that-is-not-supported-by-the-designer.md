---
title: Uno o più elementi selezionati contengono un tipo di dati non supportato dalla finestra di progettazione
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 71dcd4f9-2946-42c5-9ce4-99c819ea2785
author: gewarren
ms.author: gewarren
manager: jillfra
ms.prod: visual-studio-dev15
ms.workload:
- data-storage
ms.openlocfilehash: 294bc51345eb6a9e09f9892c3b9ec17f78c42451
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "54986124"
---
# <a name="one-or-more-selected-items-contain-a-data-type-that-is-not-supported-by-the-designer"></a>Uno o più elementi selezionati contengono un tipo di dati non supportato dalla finestra di progettazione

Uno o più elementi trascinati da **Esplora Server** oppure **Esplora Database** nel **O/R Designer** contiene un tipo di dati che non è supportato dal **O /R designer**, ad esempio [tipi CLR definiti dall'utente](/dotnet/framework/data/adonet/sql/clr-user-defined-types).

## <a name="to-correct-this-error"></a>Per correggere l'errore

1. Creare una visualizzazione basata sulla tabella desiderata e che non includa il tipo di dati non supportato.

2. Trascinare la visualizzazione dal **Esplora Server** oppure **Esplora Database** nella finestra di progettazione.

## <a name="see-also"></a>Vedere anche

- [Messaggi di Object Relational Designer](../data-tools/o-r-designer-messages.md)
- [Strumenti LINQ to SQL in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)