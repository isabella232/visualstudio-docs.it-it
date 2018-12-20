---
title: Visualizzare l'anteprima delle modifiche al codice
ms.date: 12/16/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
f1_keywords:
- vs.codefix.previewchanges
ms.workload:
- multiple
ms.openlocfilehash: 16f681d8498242eb8ddc9c1a81fe8d17186f2fff
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/07/2018
ms.locfileid: "53067356"
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
