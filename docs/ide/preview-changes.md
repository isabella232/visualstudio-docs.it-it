---
title: Visualizzare l'anteprima delle modifiche al codice
ms.date: 12/16/2016
ms.prod: visual-studio-dev15
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: jillfra
f1_keywords:
- vs.codefix.previewchanges
ms.workload:
- multiple
ms.openlocfilehash: af5cc054411d5297e919f549c7cb518b48ac441b
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "54928815"
---
# <a name="preview-changes-window"></a>Finestra Anteprima modifiche

Quando si usano vari strumenti *Azioni rapide* o *Refactoring* in Visual Studio, spesso è possibile visualizzare in anteprima le modifiche che stanno per essere apportate al progetto prima di accettarle. Questa operazione viene eseguita nella finestra **Anteprima modifiche**.  Ecco ad esempio la finestra **Anteprima modifiche** con le modifiche apportate durante un refactoring di ridenominazione in un progetto C#:

![Anteprima modifiche](media/previewchanges.png)

Nella metà superiore della finestra vengono visualizzate le righe specifiche che verranno modificate, ognuna con una casella di controllo. È possibile selezionare o deselezionare ogni casella di controllo se si vuole applicare in modo selettivo il refactoring solo a righe specifiche.

Nella metà inferiore della finestra viene visualizzato il codice formattato dal progetto che verrà modificato, con le aree interessate evidenziate. Selezionare la riga specifica nella metà superiore della finestra per evidenziare la riga corrispondente nella metà inferiore. Questo consente di passare rapidamente alla riga appropriata e vedere il codice circostante.

Dopo aver verificato le modifiche, fare clic sul pulsante **Applica** per salvare le modifiche oppure fare clic sul pulsante **Annulla** per lasciare la situazione invariata.

## <a name="see-also"></a>Vedere anche

- [Refactoring in Visual Studio](../ide/refactoring-in-visual-studio.md) (Effettuare il refactoring in Visual Studio)
- [Azioni rapide](../ide/quick-actions.md)
