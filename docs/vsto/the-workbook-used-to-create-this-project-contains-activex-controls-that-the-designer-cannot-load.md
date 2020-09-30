---
title: La cartella di lavoro contiene controlli ActiveX che non possono essere caricati
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
ms.openlocfilehash: 09182fb354ad3ae8937b66952a0acd376d54fe0a
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/30/2020
ms.locfileid: "91584451"
---
# <a name="the-workbook-contains-activex-controls-that-cannot-be-loaded"></a>La cartella di lavoro contiene controlli ActiveX che non possono essere caricati

  L'errore "la cartella di lavoro usata per creare il progetto contiene controlli ActiveX che la finestra di progettazione non è in grado di caricare" viene visualizzato quando si aggiunge un controllo a un documento di Word o a un foglio di lavoro di Excel a livello di codice, si salva il documento o la cartella di lavoro e quindi si crea una nuova soluzione a livello di documento basata sul documento

 Le informazioni relative alla descrizione del tipo gestito del controllo non vengono salvate insieme al documento o alla cartella di lavoro. Quando si crea una nuova soluzione basata su tale documento o cartella di lavoro, in Visual Studio non sono disponibili informazioni sufficienti per caricare il controllo nella finestra di progettazione dell'elemento host.

## <a name="to-correct-this-error"></a>Per correggere l'errore

1. Aprire il documento o la cartella di lavoro.

2. Rimuovere i controlli aggiunti in fase di esecuzione. A tale scopo, è possibile selezionarli nel documento o nella cartella di lavoro e premere il tasto **Canc** .

3. Creare una soluzione a livello di documento basata sul documento o sulla cartella di lavoro.

## <a name="see-also"></a>Vedi anche
- [Procedura: creare progetti di Office in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Aggiungere controlli ai documenti di Office in fase di esecuzione](../vsto/adding-controls-to-office-documents-at-run-time.md)
