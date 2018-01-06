---
title: La cartella di lavoro utilizzato per creare il progetto contiene controlli ActiveX non caricabili nella finestra di progettazione | Documenti Microsoft
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VST.SelectDocWizard.ContainsActiveXControls
dev_langs:
- VB
- CSharp
ms.assetid: 91e9c6ee-7543-41e3-be0c-6c000cfd32d1
caps.latest.revision: "15"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 2227af08d42b6cf47f7db4ba68e568b9e315bae6
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="the-workbook-used-to-create-this-project-contains-activex-controls-that-the-designer-cannot-load"></a>La cartella di lavoro utilizzata per creare il progetto contiene controlli ActiveX non caricabili nella finestra di progettazione
  Questo errore viene visualizzato quando si aggiunge a livello di codice un controllo a un documento di Word o a un foglio di lavoro di Excel, si salva il documento o la cartella di lavoro e si crea quindi una nuova soluzione a livello di documento basata sul documento o sulla cartella di lavoro.  
  
 Le informazioni relative alla descrizione del tipo gestito del controllo non vengono salvate insieme al documento o alla cartella di lavoro. Quando si crea una nuova soluzione basata su tale documento o cartella di lavoro, in Visual Studio non sono disponibili informazioni sufficienti per caricare il controllo nella finestra di progettazione dell'elemento host.  
  
### <a name="to-correct-this-error"></a>Per correggere l'errore  
  
1.  Aprire il documento o la cartella di lavoro.  
  
2.  Rimuovere i controlli aggiunti in fase di esecuzione. A tal fine, selezionarli nel documento o nella cartella di lavoro e premere il tasto CANC.  
  
3.  Creare una soluzione a livello di documento basata sul documento o sulla cartella di lavoro.  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura: creare progetti di Office in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Adding Controls to Office Documents at Run Time](../vsto/adding-controls-to-office-documents-at-run-time.md)  
  
  