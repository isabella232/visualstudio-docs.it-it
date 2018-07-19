---
title: Questo metodo correlato è il metodo sottostante per i seguenti metodi predefiniti di inserimento, aggiornamento o eliminazione
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 62afa6da-97cf-48b9-8de3-33e4d72a0377
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 30e08cb10b6e1912fe5962620faf34a1c6250cf3
ms.sourcegitcommit: f37affbc1b885dfe246d4b2c295a6538b383a0ca
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37174166"
---
# <a name="this-related-method-is-the-backing-method-for-the-following-default-insert-update-or-delete-methods"></a>Questo metodo correlato è il metodo sottostante per i seguenti metodi predefiniti di inserimento, aggiornamento o eliminazione

Questo metodo correlato è il metodo sottostante per l'impostazione predefinita seguente `Insert`, `Update`, o `Delete` metodi. Se viene eliminato, verranno eliminati anche questi metodi. Continuare?

Selezionato `DataContext` metodo viene usato attualmente come uno dei `Insert`, `Update`, o `Delete` metodi per una delle classi di entità nel **O/R Designer**. Il metodo selezionato provoca l'eliminazione della classe di entità che lo stava usando questo metodo per ripristinare il comportamento in fase di esecuzione predefinito per l'esecuzione di inserimento, aggiornare o eliminare durante un aggiornamento.

## <a name="to-delete-the-selected-method-causing-the-entity-class-to-use-runtime-updates"></a>Per eliminare il metodo selezionato e determinare l'uso degli aggiornamenti in fase di esecuzione da parte della classe di entità

- Scegliere **Sì**.

    Il metodo selezionato viene eliminato e per tutte le classi che utilizzavano tale metodo per l'override del comportamento di aggiornamento viene ripristinato l'uso del comportamento in fase di esecuzione LINQ to SQL predefinito.

## <a name="to-close-the-message-box-leaving-the-selected-method-unchanged"></a>Per chiudere la finestra di messaggio e lasciare invariato il metodo selezionato

- Fare clic su **No**.

    La finestra di messaggio viene chiusa e non vengono apportate modifiche.

## <a name="see-also"></a>Vedere anche

- [Messaggi di Object Relational Designer](../data-tools/o-r-designer-messages.md)
- [Strumenti LINQ to SQL in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)