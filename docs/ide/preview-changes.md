---
title: Visualizzare l'anteprima delle modifiche al codice
description: Informazioni su come usare la finestra Anteprima modifiche per esaminare le modifiche che verranno apportate al progetto prima di accettarle.
ms.custom: SEO-VS-2020
ms.date: 12/16/2016
ms.topic: conceptual
author: TerryGLee
ms.author: tglee
manager: jillfra
f1_keywords:
- vs.codefix.previewchanges
ms.workload:
- multiple
ms.openlocfilehash: f8eef438f1dd504120b62e2e0018935489d6c80a
ms.sourcegitcommit: 935e4d9a20928b733e573b6801a6eaff0d0b1b14
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/25/2020
ms.locfileid: "95871444"
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
