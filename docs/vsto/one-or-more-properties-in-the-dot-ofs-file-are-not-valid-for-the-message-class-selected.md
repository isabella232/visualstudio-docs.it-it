---
title: Proprietà non valide nel file OFS per la classe Message "
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
ms.openlocfilehash: 66e8ecacffb58e945a3f80d03f47edc1329668d1
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/30/2020
ms.locfileid: "91584659"
---
# <a name="invalid-properties-in-the-ofs-file-for-the-message-class"></a>Proprietà non valide nel file OFS per la classe Message

  L'errore "una o più proprietà nel file OFS non sono valide per la classe messaggio selezionata" viene visualizzato quando si importa un'area del modulo progettata in Outlook, ma uno o più campi nell'area del modulo non sono compatibili con le classi di messaggio selezionate nella pagina finale della procedura guidata **nuova area del modulo** .

Ad esempio, è possibile selezionare **Task (IPM.Task)** nella pagina finale della procedura guidata **Nuova area del modulo** . Se l'area del modulo contiene un campo dell' **indirizzo di business** , questo errore viene visualizzato perché un'attività non dispone di un indirizzo di business. Pertanto, il campo **indirizzo di business** non è compatibile con la `IPM.Task` classe Message.

 È possibile selezionare **Task (IPM). Attività)** nella pagina finale della procedura guidata **nuova area del modulo** . Se l'area del modulo contiene un campo dell' **indirizzo di business** , questo errore viene visualizzato perché un'attività non dispone di un indirizzo di business. Pertanto, il campo **indirizzo di business** non è compatibile con la `IPM.Task` classe Message.

## <a name="to-correct-this-error"></a>Per correggere l'errore

- Nella pagina finale della procedura guidata **Nuova area del modulo** selezionare una classe messaggio compatibile con i campi dell'area del modulo.

- In progettazione form in Outlook rimuovere i campi non compatibili con le classi messaggio. Rimuovere i campi che si intende selezionare nella pagina finale della procedura guidata **nuova area del modulo** .

## <a name="see-also"></a>Vedi anche
- [Procedura dettagliata: importare un'area del modulo progettata in Outlook](../vsto/walkthrough-importing-a-form-region-that-is-designed-in-outlook.md)
