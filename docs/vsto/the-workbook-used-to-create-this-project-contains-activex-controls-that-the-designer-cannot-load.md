---
title: La cartella di lavoro contiene controlli ActiveX che non possono essere caricati
description: Informazioni su come è possibile risolvere l'errore che si verifica quando una cartella di lavoro contiene controlli ActiveX che non possono essere caricati.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: error-reference
f1_keywords:
- VST.SelectDocWizard.ContainsActiveXControls
dev_langs:
- VB
- CSharp
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 7257e3940af72f344906642adc51a1dd98cb3f25
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/15/2020
ms.locfileid: "97524176"
---
# <a name="the-workbook-contains-activex-controls-that-cannot-be-loaded"></a>La cartella di lavoro contiene controlli ActiveX che non possono essere caricati

  L'errore "la cartella di lavoro usata per creare il progetto contiene controlli ActiveX che la finestra di progettazione non è in grado di caricare" viene visualizzato quando si aggiunge un controllo a un documento di Word o a un foglio di lavoro di Excel a livello di codice, si salva il documento o la cartella di lavoro e quindi si crea una nuova soluzione a livello di documento basata sul documento

 Le informazioni relative alla descrizione del tipo gestito del controllo non vengono salvate insieme al documento o alla cartella di lavoro. Quando si crea una nuova soluzione basata su tale documento o cartella di lavoro, in Visual Studio non sono disponibili informazioni sufficienti per caricare il controllo nella finestra di progettazione dell'elemento host.

## <a name="to-correct-this-error"></a>Per correggere l'errore

1. Aprire il documento o la cartella di lavoro.

2. Rimuovere i controlli aggiunti in fase di esecuzione. A tale scopo, è possibile selezionarli nel documento o nella cartella di lavoro e premere il tasto **Canc** .

3. Creare una soluzione a livello di documento basata sul documento o sulla cartella di lavoro.

## <a name="see-also"></a>Vedere anche
- [Procedura: creare progetti di Office in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Aggiungere controlli ai documenti di Office in fase di esecuzione](../vsto/adding-controls-to-office-documents-at-run-time.md)
