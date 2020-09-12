---
title: Tipo di dati non supportati
description: Uno o più elementi selezionati contengono un tipo di dati non supportato dalla finestra di progettazione
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: error-reference
ms.assetid: 71dcd4f9-2946-42c5-9ce4-99c819ea2785
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 167146b9a7938e5498e8db023602b2e13f74379c
ms.sourcegitcommit: 4ae5e9817ad13edd05425febb322b5be6d3c3425
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/11/2020
ms.locfileid: "90034078"
---
# <a name="one-or-more-selected-items-contain-a-data-type-that-is-not-supported-by-the-designer"></a>Uno o più elementi selezionati contengono un tipo di dati non supportato dalla finestra di progettazione

Uno o più elementi trascinati da **Esplora server** o **Esplora database** in **Progettazione relazionale** oggetti contiene un tipo di dati che non è supportato da **o/r designer**, ad esempio i [tipi CLR definiti dall'utente](/dotnet/framework/data/adonet/sql/clr-user-defined-types).

## <a name="to-correct-this-error"></a>Per correggere l'errore

1. Creare una visualizzazione basata sulla tabella desiderata e che non includa il tipo di dati non supportato.

2. Trascinare la vista da **Esplora server** o **Esplora database** nella finestra di progettazione.

## <a name="see-also"></a>Vedi anche

- [Strumenti di LINQ to SQL in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
