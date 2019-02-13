---
title: Questo metodo correlato è il metodo sottostante per i seguenti metodi predefiniti di inserimento, aggiornamento o eliminazione
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 62afa6da-97cf-48b9-8de3-33e4d72a0377
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: cc83bc78aace73cedf186b5ec925dce0a509b91d
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2019
ms.locfileid: "55945651"
---
# <a name="this-related-method-is-the-backing-method-for-the-following-default-insert-update-or-delete-methods"></a>Questo metodo correlato è il metodo sottostante per i seguenti metodi predefiniti di inserimento, aggiornamento o eliminazione

Questo metodo correlato è il metodo sottostante per l'impostazione predefinita seguente `Insert`, `Update`, o `Delete` metodi. Se viene eliminato, verranno eliminati anche questi metodi. Continuare?

Selezionato `DataContext` metodo viene usato attualmente come uno dei `Insert`, `Update`, o `Delete` metodi per una delle classi di entità nel **O/R Designer**. Il metodo selezionato provoca l'eliminazione della classe di entità che lo stava usando questo metodo per ripristinare il comportamento in fase di esecuzione predefinito per l'esecuzione di inserimento, aggiornare o eliminare durante un aggiornamento.

## <a name="selected-method-options"></a>Opzioni per il metodo selezionato

- Per eliminare il metodo selezionato, causando la classe di entità da utilizzare aggiornamenti al runtime, fare clic su **Sì**.

   Il metodo selezionato viene eliminato e per tutte le classi che utilizzavano tale metodo per l'override del comportamento di aggiornamento viene ripristinato l'uso del comportamento in fase di esecuzione LINQ to SQL predefinito.

- Per chiudere la finestra di messaggio, lasciando il metodo selezionato non modificato, fare clic su **No**.

   La finestra di messaggio viene chiusa e non vengono apportate modifiche.

## <a name="see-also"></a>Vedere anche

- [Messaggi di Object Relational Designer](../data-tools/o-r-designer-messages.md)
- [Strumenti LINQ to SQL in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)