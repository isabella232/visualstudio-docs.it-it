---
title: Non è possibile eliminare il metodo di backup
description: Questo metodo correlato è il metodo sottostante per i seguenti metodi predefiniti di inserimento, aggiornamento o eliminazione
ms.date: 11/04/2016
ms.topic: error-reference
ms.assetid: 62afa6da-97cf-48b9-8de3-33e4d72a0377
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: ad7c66c6d110d09940a93e694a897a7dafd92e17
ms.sourcegitcommit: 2a201c93ed526b0f7e5848657500f1111b08ac2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/10/2020
ms.locfileid: "89743084"
---
# <a name="this-related-method-is-the-backing-method-for-the-following-default-insert-update-or-delete-methods"></a>Questo metodo correlato è il metodo sottostante per i seguenti metodi predefiniti di inserimento, aggiornamento o eliminazione

Questo metodo correlato è il metodo sottostante per i seguenti `Insert` metodi predefiniti, `Update` o `Delete` . Se viene eliminato, verranno eliminati anche questi metodi. Continuare?

Il `DataContext` metodo selezionato è attualmente usato come uno dei `Insert` metodi, `Update` o `Delete` per una delle classi di entità in **Progettazione relazionale di o/R**. Se si elimina il metodo selezionato, la classe di entità che utilizza questo metodo ripristina il comportamento predefinito della fase di esecuzione per l'esecuzione dell'istruzione INSERT, Update o DELETE durante un aggiornamento.

## <a name="selected-method-options"></a>Opzioni metodo selezionate

- Per eliminare il metodo selezionato, facendo in modo che la classe di entità usi gli aggiornamenti del runtime, fare clic su **Sì**.

   Il metodo selezionato viene eliminato e tutte le classi che utilizzano questo metodo per eseguire l'override del comportamento di aggiornamento vengono ripristinate in base al comportamento predefinito della fase di esecuzione LINQ to SQL.

- Per chiudere la finestra di messaggio lasciando invariato il metodo selezionato, fare clic su **No**.

   La finestra di messaggio viene chiusa e non vengono apportate modifiche.

## <a name="see-also"></a>Vedere anche

- [Strumenti di LINQ to SQL in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)