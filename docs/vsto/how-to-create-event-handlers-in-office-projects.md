---
title: 'Procedura: creare gestori eventi nei progetti di Office | Documenti Microsoft'
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Visual Basic [Office development in Visual Studio], event handlers
- event handlers [Office development in Visual Studio]
- Visual C# [Office development in Visual Studio], event handlers
- events [Office development in Visual Studio]
ms.assetid: 2cfd6a45-4c25-4431-b4fc-e0f2c0a72e54
caps.latest.revision: "31"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 151648a6c12e2c28d912be3b75c51b438ae5ee13
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-event-handlers-in-office-projects"></a>Procedura: creare gestori eventi in progetti di Office
  Esistono diversi modi per creare gestori eventi in Visual Basic e c#. Nella visualizzazione progettazione, è possibile creare l'impostazione predefinita, i gestori di eventi per i controlli facendo doppio clic sul controllo o utilizzare il riquadro eventi del **proprietà** finestra consente di creare gestori per qualsiasi evento del controllo. Se si è nella visualizzazione codice, tuttavia, non è desidera passare alla visualizzazione progettazione per creare un gestore eventi.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
### <a name="to-create-an-event-handler-in-visual-basic"></a>Per creare un gestore eventi in Visual Basic  
  
1.  Dal **nome classe** elenco a discesa nella parte superiore dell'Editor di codice, selezionare l'oggetto che si desidera creare un gestore eventi per.  
  
    > [!NOTE]  
    >  Se si desidera creare gestori eventi per `ThisDocument` o `ThisWorkbook`, è necessario selezionare **(ThisDocument Events)** o **(ThisWorkbook Events)** nel **nome classe**elenco a discesa  
  
2.  Dal **nome del metodo** elenco a discesa nella parte superiore dell'Editor di codice, selezionare l'evento.  
  
     Visual Studio crea il gestore dell'evento e sposta il punto di inserimento al gestore eventi appena creato. Se esiste già il gestore dell'evento, il gestore dell'evento esistente si sposta il punto di inserimento.  
  
### <a name="to-create-an-event-handler-in-c"></a>Per creare un gestore eventi in c#  
  
1.  Creare il delegato dell'evento nel **avvio** evento della classe digitando il nome completo dell'evento seguito da uno spazio e quindi digitando  **+=**  senza spazi finali. Ad esempio:  
  
     `this.<object name>.<event name> +=`  
  
2.  Alla fine della riga di codice, premere il tasto TAB due volte.  
  
     Visual Studio automaticamente completa la riga di codice, crea il gestore dell'evento e si sposta il punto di inserimento al gestore eventi appena creato.  
  
## <a name="see-also"></a>Vedere anche  
 [Scrittura di codice nelle soluzioni Office](../vsto/writing-code-in-office-solutions.md)   
 [Procedura dettagliata: Programmazione per eventi di un controllo NamedRange](../vsto/walkthrough-programming-against-events-of-a-namedrange-control.md)   
 [Compilazione di soluzioni Office](../vsto/building-office-solutions.md)  
  
  