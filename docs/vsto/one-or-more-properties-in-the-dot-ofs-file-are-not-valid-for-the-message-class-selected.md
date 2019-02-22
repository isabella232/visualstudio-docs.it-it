---
title: Una o più proprietà del file con estensione ofs non sono valide per la classe messaggio selezionata
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VSTO.NewFormRegionWizard.OFSPropertyError
dev_langs:
- VB
- CSharp
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 6b13352ca54db84137e029aa126f1f174a1c80fe
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/21/2019
ms.locfileid: "56621474"
---
# <a name="one-or-more-properties-in-the-ofs-file-are-not-valid-for-the-message-class-selected"></a>Una o più proprietà del file con estensione ofs non sono valide per la classe messaggio selezionata
  Questo errore viene visualizzato quando si importa un'area del modulo progettata in Outlook, ma uno o più campi nell'area del modulo non sono compatibili con le classi messaggio selezionate nella pagina finale della **nuova area del modulo** procedura guidata.

Ad esempio, è possibile selezionare **Task (IPM.Task)** nella pagina finale della procedura guidata **Nuova area del modulo** . Se l'area del modulo contiene un **Business Address** campo, si riceverà questo errore perché un'attività non ha un indirizzo aziendale. Pertanto, il **Business Address** campo non è compatibile con il `IPM.Task` classe message.

 È possibile selezionare **Task (IPM. Attività)** nella pagina finale della **nuova area del modulo** procedura guidata. Se l'area del modulo contiene un **Business Address** campo, si riceverà questo errore perché un'attività non ha un indirizzo aziendale. Pertanto, il **Business Address** campo non è compatibile con il `IPM.Task` classe message.

## <a name="to-correct-this-error"></a>Per correggere l'errore

-   Nella pagina finale della procedura guidata **Nuova area del modulo** selezionare una classe messaggio compatibile con i campi dell'area del modulo.

-   Nella finestra di progettazione form in Outlook rimuovere i campi che non sono compatibili con le classi di messaggi. Rimuovere i campi che si intendono selezionare nella pagina finale della **nuova area del modulo** procedura guidata.

## <a name="see-also"></a>Vedere anche
- [Procedura dettagliata: Importare un'area del modulo progettata in Outlook](../vsto/walkthrough-importing-a-form-region-that-is-designed-in-outlook.md)
