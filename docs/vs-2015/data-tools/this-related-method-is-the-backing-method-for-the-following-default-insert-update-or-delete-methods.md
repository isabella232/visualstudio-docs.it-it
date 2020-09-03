---
title: Questo metodo correlato è il metodo sottostante per i seguenti metodi predefiniti di inserimento, aggiornamento o eliminazione | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: 62afa6da-97cf-48b9-8de3-33e4d72a0377
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 84d27dc6f5081a36a237748c091429cfdabbe841
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "72667173"
---
# <a name="this-related-method-is-the-backing-method-for-the-following-default-insert-update-or-delete-methods"></a>Questo metodo correlato è il metodo sottostante per i seguenti metodi predefiniti di inserimento, aggiornamento o eliminazione
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Questo metodo correlato è il metodo sottostante per i seguenti metodi predefiniti di inserimento, aggiornamento o eliminazione. Se viene eliminato, verranno eliminati anche questi metodi. Continuare?

 Il metodo `DataContext` selezionato viene usato attualmente come uno dei metodi di inserimento, aggiornamento o eliminazione per una delle classi di entità in Progettazione relazionale oggetti. L'eliminazione del metodo selezionato determinerà, per la classe di entità che lo stava usando, il ripristino del comportamento in fase di esecuzione predefinito per l'esecuzione dei comandi di inserimento, aggiornamento o eliminazione durante un aggiornamento.

### <a name="to-delete-the-selected-method-causing-the-entity-class-to-use-runtime-updates"></a>Per eliminare il metodo selezionato e determinare l'uso degli aggiornamenti in fase di esecuzione da parte della classe di entità

- Fare clic su **Sì**.

     Il metodo selezionato viene eliminato e per tutte le classi che utilizzavano tale metodo per l'override del comportamento di aggiornamento viene ripristinato l'uso del comportamento in fase di esecuzione LINQ to SQL predefinito.

### <a name="to-close-the-message-box-leaving-the-selected-method-unchanged"></a>Per chiudere la finestra di messaggio e lasciare invariato il metodo selezionato

- Fare clic su **No**.

     La finestra di messaggio viene chiusa e non vengono apportate modifiche.

## <a name="see-also"></a>Vedere anche
 [Metodi DataContext (o/r designer)](../data-tools/datacontext-methods-o-r-designer.md) [procedura: assegnare stored procedure per eseguire aggiornamenti, inserimenti ed eliminazioni (o/r designer)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md) [LINQ to SQL Tools in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) [LINQ to SQL](https://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655)
