---
title: La cartella di lavoro ActiveX controlli che non possono essere caricati
description: Informazioni su come risolvere l'errore che si verifica quando una cartella di lavoro contiene ActiveX controlli che non possono essere caricati.
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
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: e89484f9da4868ff04cbaeaa72247e39be147185
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122147726"
---
# <a name="the-workbook-contains-activex-controls-that-cannot-be-loaded"></a>La cartella di lavoro ActiveX controlli che non possono essere caricati

  L'errore "La cartella di lavoro usata per creare questo progetto contiene controlli ActiveX che la finestra di progettazione non può caricare" viene visualizzato quando si aggiunge un controllo a un documento di Word o a un foglio di lavoro Excel a livello di codice, si salva il documento o la cartella di lavoro e quindi si crea una nuova soluzione a livello di documento basata sul documento o sulla cartella di lavoro.

 Le informazioni relative alla descrizione del tipo gestito del controllo non vengono salvate insieme al documento o alla cartella di lavoro. Quando si crea una nuova soluzione basata su tale documento o cartella di lavoro, in Visual Studio non sono disponibili informazioni sufficienti per caricare il controllo nella finestra di progettazione dell'elemento host.

## <a name="to-correct-this-error"></a>Per correggere l'errore

1. Aprire il documento o la cartella di lavoro.

2. Rimuovere i controlli aggiunti in fase di esecuzione. A tale scopo, selezionarli nel documento o nella cartella di lavoro e premere **CANC.**

3. Creare una soluzione a livello di documento basata sul documento o sulla cartella di lavoro.

## <a name="see-also"></a>Vedi anche
- [Procedura: Creare Office progetti in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Aggiungere controlli per Office documenti in fase di esecuzione](../vsto/adding-controls-to-office-documents-at-run-time.md)
