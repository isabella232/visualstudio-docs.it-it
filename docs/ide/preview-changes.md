---
title: Visualizzare l'anteprima delle modifiche al codice
ms.date: 12/16/2016
ms.topic: conceptual
author: jillre
ms.author: jillfra
manager: jillfra
f1_keywords:
- vs.codefix.previewchanges
ms.workload:
- multiple
ms.openlocfilehash: 485a127faa8228ce5ef17a6208e9cc4e7e50e1b9
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72666791"
---
# <a name="preview-changes-window"></a>Finestra Anteprima modifiche

Quando si usano vari strumenti *Azioni rapide* o *Refactoring* in Visual Studio, spesso è possibile visualizzare in anteprima le modifiche che stanno per essere apportate al progetto prima di accettarle. Questa operazione viene eseguita nella finestra **Anteprima modifiche**.  Ecco ad esempio la finestra **Anteprima modifiche** con le modifiche apportate durante un refactoring di ridenominazione in un progetto C#:

![Anteprima modifiche](media/previewchanges.png)

Nella metà superiore della finestra vengono visualizzate le righe specifiche che verranno modificate, ognuna con una casella di controllo. È possibile selezionare o deselezionare ogni casella di controllo se si vuole applicare in modo selettivo il refactoring solo a righe specifiche.

Nella metà inferiore della finestra viene visualizzato il codice formattato dal progetto che verrà modificato, con le aree interessate evidenziate. Selezionare la riga specifica nella metà superiore della finestra per evidenziare la riga corrispondente nella metà inferiore. Questo consente di passare rapidamente alla riga appropriata e vedere il codice circostante.

Dopo aver verificato le modifiche, fare clic sul pulsante **Applica** per salvare le modifiche oppure fare clic sul pulsante **Annulla** per lasciare la situazione invariata.

## <a name="see-also"></a>Vedere anche

- [Effettuare il refactoring in Visual Studio](../ide/refactoring-in-visual-studio.md)
- [Azioni rapide](../ide/quick-actions.md)
