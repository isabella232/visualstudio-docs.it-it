---
title: 'Procedura: Creare i gestori eventi nei progetti di Office'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Visual Basic [Office development in Visual Studio], event handlers
- event handlers [Office development in Visual Studio]
- Visual C# [Office development in Visual Studio], event handlers
- events [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 537bae766b71744a61e5158b1a859cade4cdcda7
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63419647"
---
# <a name="how-to-create-event-handlers-in-office-projects"></a>Procedura: Creare i gestori eventi nei progetti di Office
  Esistono diversi modi per creare gestori eventi in Visual Basic e c#. Nella visualizzazione progettazione, è possibile creare il valore predefinito di gestori di eventi per i controlli facendo doppio clic sul controllo o utilizzare il riquadro eventi della **proprietà** finestra per creare gestori per qualsiasi evento del controllo. Se si è nella visualizzazione codice, tuttavia, non è necessario passare alla visualizzazione di progettazione per creare un gestore eventi.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

### <a name="to-create-an-event-handler-in-visual-basic"></a>Per creare un gestore eventi in Visual Basic

1. Dal **nome della classe** elenco a discesa nella parte superiore dell'Editor di codice, selezionare l'oggetto che si desidera creare un gestore eventi per.

    > [!NOTE]
    > Se si desidera creare gestori eventi per `ThisDocument` o `ThisWorkbook`, è necessario selezionare **(ThisDocument eventi)** oppure **(ThisWorkbook eventi)** nel **nome classe**elenco a discesa

2. Dal **nome del metodo** elenco a discesa nella parte superiore dell'Editor di codice, selezionare l'evento.

     Visual Studio crea il gestore dell'evento e sposta il punto di inserimento al gestore eventi appena creato. Se il gestore eventi esiste già, il punto di inserimento si sposta al gestore dell'evento esistente.

### <a name="to-create-an-event-handler-in-c"></a>Per creare un gestore eventi in C\#

1. Creare il delegato dell'evento nel **avvio** evento della classe digitando il nome completo dell'evento seguita da uno spazio e quindi digitando **+=** senza spazi finali. Ad esempio:

     `this.<object name>.<event name> +=`

2. Alla fine della riga di codice, premere il tasto TAB due volte.

     Visual Studio automaticamente viene completata la riga di codice, crea il gestore dell'evento e sposta il punto di inserimento al gestore eventi appena creato.

## <a name="see-also"></a>Vedere anche
- [Scrivere il codice nelle soluzioni Office](../vsto/writing-code-in-office-solutions.md)
- [Procedura dettagliata: Programmazione per eventi di un controllo NamedRange](../vsto/walkthrough-programming-against-events-of-a-namedrange-control.md)
- [Creazione di soluzioni Office](../vsto/building-office-solutions.md)
