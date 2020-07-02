---
title: La cartella di lavoro utilizzata per creare il progetto contiene controlli ActiveX non caricabili nella finestra di progettazione
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
ms.openlocfilehash: 4485489b48c4d1b03b608c6072cfc859e8bc8f59
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/30/2020
ms.locfileid: "85537345"
---
# <a name="the-workbook-used-to-create-this-project-contains-activex-controls-that-the-designer-cannot-load"></a>La cartella di lavoro utilizzata per creare il progetto contiene controlli ActiveX non caricabili nella finestra di progettazione
  Questo errore viene visualizzato quando si aggiunge a livello di codice un controllo a un documento di Word o a un foglio di lavoro di Excel, si salva il documento o la cartella di lavoro e si crea quindi una nuova soluzione a livello di documento basata sul documento o sulla cartella di lavoro.

 Le informazioni relative alla descrizione del tipo gestito del controllo non vengono salvate insieme al documento o alla cartella di lavoro. Quando si crea una nuova soluzione basata su tale documento o cartella di lavoro, in Visual Studio non sono disponibili informazioni sufficienti per caricare il controllo nella finestra di progettazione dell'elemento host.

## <a name="to-correct-this-error"></a>Per correggere l'errore

1. Aprire il documento o la cartella di lavoro.

2. Rimuovere i controlli aggiunti in fase di esecuzione. A tale scopo, è possibile selezionarli nel documento o nella cartella di lavoro e premere il tasto **Canc** .

3. Creare una soluzione a livello di documento basata sul documento o sulla cartella di lavoro.

## <a name="see-also"></a>Vedere anche
- [Procedura: creare progetti di Office in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Aggiungere controlli ai documenti di Office in fase di esecuzione](../vsto/adding-controls-to-office-documents-at-run-time.md)
