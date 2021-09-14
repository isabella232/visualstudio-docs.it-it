---
title: Impossibile eliminare il metodo di backup
description: Questo metodo correlato è il metodo sottostante per i seguenti metodi predefiniti di inserimento, aggiornamento o eliminazione
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: error-reference
ms.assetid: 62afa6da-97cf-48b9-8de3-33e4d72a0377
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 8dcf07340584a3103a854dae3ffa7787cabee448
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126631134"
---
# <a name="this-related-method-is-the-backing-method-for-the-following-default-insert-update-or-delete-methods"></a>Questo metodo correlato è il metodo sottostante per i seguenti metodi predefiniti di inserimento, aggiornamento o eliminazione

Questo metodo correlato è il metodo di supporto per i seguenti metodi `Insert` `Update` predefiniti , o `Delete` . Se viene eliminato, verranno eliminati anche questi metodi. Continuare?

Il metodo selezionato è attualmente utilizzato come uno dei metodi , o per una delle classi di `DataContext` `Insert` entità in `Update` `Delete` **O/R Designer.** Se si elimina il metodo selezionato, la classe di entità che usa questo metodo ripristina il comportamento di run-time predefinito per l'esecuzione dell'inserimento, dell'aggiornamento o dell'eliminazione durante un aggiornamento.

## <a name="selected-method-options"></a>Opzioni del metodo selezionate

- Per eliminare il metodo selezionato, facendo in modo che la classe di entità usi gli aggiornamenti di runtime, fare clic **su Sì.**

   Il metodo selezionato viene eliminato e tutte le classi che hanno usato questo metodo per eseguire l'override del comportamento di aggiornamento vengono ripristinate all'uso del comportamento LINQ to SQL in fase di esecuzione.

- Per chiudere la finestra di messaggio, lasciando invariato il metodo selezionato, fare clic su **No.**

   La finestra di messaggio viene chiusa e non vengono apportate modifiche.

## <a name="see-also"></a>Vedi anche

- [LINQ to SQL strumenti in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)