---
title: Una o più proprietà del file con estensione ofs non sono valide per la classe messaggio selezionata
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VSTO.NewFormRegionWizard.OFSPropertyError
dev_langs:
- VB
- CSharp
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: cfae8533337bbe18c89dbb670fb58a0c89c6c54c
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/01/2018
ms.locfileid: "34692499"
---
# <a name="one-or-more-properties-in-the-ofs-file-are-not-valid-for-the-message-class-selected"></a>Una o più proprietà del file con estensione ofs non sono valide per la classe messaggio selezionata
  Questo errore viene visualizzato quando si importa un'area del modulo progettata in Outlook, ma uno o più campi nell'area del modulo non sono compatibili con le classi messaggio selezionate nella pagina finale della **nuova area del modulo** procedura guidata.  

Ad esempio, è possibile selezionare **Task (IPM.Task)** nella pagina finale della procedura guidata **Nuova area del modulo** . Se l'area del modulo ha un **indirizzo aziendale** campo, verrà visualizzato questo errore perché un'attività non ha un indirizzo della società. Pertanto, il **Business Address** campo non è compatibile con la `IPM.Task` classe message.  
  
 È possibile selezionare **Task (IPM. Attività)** nella pagina finale del **nuova area del modulo** procedura guidata. Se l'area del modulo ha un **indirizzo aziendale** campo, verrà visualizzato questo errore perché un'attività non ha un indirizzo della società. Pertanto, il **Business Address** campo non è compatibile con la `IPM.Task` classe message.  
  
## <a name="to-correct-this-error"></a>Per correggere l'errore  
  
-   Nella pagina finale della procedura guidata **Nuova area del modulo** selezionare una classe messaggio compatibile con i campi dell'area del modulo.  
  
-   Nella finestra di progettazione di form in Outlook, rimuovere i campi che non sono compatibili con le classi di messaggi. Rimuovere i campi che si intendono selezionare nella pagina finale della **nuova area del modulo** procedura guidata.  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura dettagliata: Importare un'area del modulo progettata in Outlook](../vsto/walkthrough-importing-a-form-region-that-is-designed-in-outlook.md)  
  
  