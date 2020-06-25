---
title: Questo metodo correlato è il metodo sottostante per i seguenti metodi predefiniti di inserimento, aggiornamento o eliminazione
ms.date: 11/04/2016
ms.topic: error-reference
ms.assetid: 62afa6da-97cf-48b9-8de3-33e4d72a0377
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 60634bb2cdc0cf85bfaee441a3fb3d3eb55b3159
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/23/2020
ms.locfileid: "85281279"
---
# <a name="this-related-method-is-the-backing-method-for-the-following-default-insert-update-or-delete-methods"></a>Questo metodo correlato è il metodo sottostante per i seguenti metodi predefiniti di inserimento, aggiornamento o eliminazione

Questo metodo correlato è il metodo sottostante per i seguenti `Insert` metodi predefiniti, `Update` o `Delete` . Se viene eliminato, verranno eliminati anche questi metodi. Continuare?

Il `DataContext` metodo selezionato è attualmente usato come uno dei `Insert` metodi, `Update` o `Delete` per una delle classi di entità in **Progettazione relazionale di o/R**. Se si elimina il metodo selezionato, la classe di entità che utilizza questo metodo ripristina il comportamento predefinito della fase di esecuzione per l'esecuzione dell'istruzione INSERT, Update o DELETE durante un aggiornamento.

## <a name="selected-method-options"></a>Opzioni metodo selezionate

- Per eliminare il metodo selezionato, facendo in modo che la classe di entità usi gli aggiornamenti del runtime, fare clic su **Sì**.

   Il metodo selezionato viene eliminato e tutte le classi che utilizzano questo metodo per eseguire l'override del comportamento di aggiornamento vengono ripristinate in base al comportamento predefinito della fase di esecuzione LINQ to SQL.

- Per chiudere la finestra di messaggio lasciando invariato il metodo selezionato, fare clic su **No**.

   La finestra di messaggio viene chiusa e non vengono apportate modifiche.

## <a name="see-also"></a>Vedi anche

- [Strumenti LINQ to SQL in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)