---
title: Proprietà non valide nel file con estensione ofs per la classe messaggio"
description: Informazioni su come correggere un errore che si verifica quando una o più proprietà nel file ofs non sono valide per la classe di messaggio selezionata.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VSTO.NewFormRegionWizard.OFSPropertyError
dev_langs:
- VB
- CSharp
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 603a0a8aaa25ac8ec203780f9b509613c33f6c3e
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122147823"
---
# <a name="invalid-properties-in-the-ofs-file-for-the-message-class"></a>Proprietà non valide nel file con estensione ofs per la classe messaggio

  L'errore "Una o più proprietà nel file ofs non sono valide per la classe di messaggio selezionata" viene visualizzato quando si importa un'area del modulo progettata in Outlook, ma uno o più campi nell'area del modulo non sono compatibili con le classi di messaggio selezionate nella pagina finale della procedura guidata Nuova **area modulo.**

Ad esempio, è possibile selezionare **Task (IPM.Task)** nella pagina finale della procedura guidata **Nuova area del modulo** . Se l'area del modulo include un **campo Indirizzo** aziendale, si riceverà questo errore perché un'attività non ha un indirizzo aziendale. Pertanto, il **campo Indirizzo** aziendale non è compatibile con la classe `IPM.Task` di messaggio.

 È possibile selezionare **Attività (IPM). Attività)** nella pagina finale della procedura guidata **Nuova area del** modulo. Se l'area del modulo include un **campo Indirizzo** aziendale, si riceverà questo errore perché un'attività non ha un indirizzo aziendale. Pertanto, il **campo Indirizzo** aziendale non è compatibile con la classe `IPM.Task` di messaggio.

## <a name="to-correct-this-error"></a>Per correggere l'errore

- Nella pagina finale della procedura guidata **Nuova area del modulo** selezionare una classe messaggio compatibile con i campi dell'area del modulo.

- In Progettazione moduli in Outlook rimuovere i campi che non sono compatibili con le classi di messaggio. Rimuovere i campi che si prevede di selezionare nella pagina finale della **procedura guidata Nuova area del** modulo.

## <a name="see-also"></a>Vedi anche
- [Procedura dettagliata: Importare un'area del modulo progettata in Outlook](../vsto/walkthrough-importing-a-form-region-that-is-designed-in-outlook.md)
