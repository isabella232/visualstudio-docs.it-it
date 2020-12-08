---
title: 'Procedura: creare gestori eventi nei progetti di Office'
description: Informazioni sui vari modi in cui è possibile creare gestori di eventi predefiniti per i controlli in Visual Basic e C#.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
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
ms.openlocfilehash: f87889c13021a7c0a43b58564210db34301abdf4
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/08/2020
ms.locfileid: "96846701"
---
# <a name="how-to-create-event-handlers-in-office-projects"></a>Procedura: creare gestori eventi nei progetti di Office
  Esistono diversi modi per creare i gestori eventi in Visual Basic e C#. Nella visualizzazione della struttura è possibile creare i gestori eventi predefiniti per i controlli facendo doppio clic sul controllo o utilizzando il riquadro eventi della finestra **Proprietà** per creare gestori per qualsiasi evento nel controllo. Tuttavia, se ci si trova nella visualizzazione codice, è possibile che non si desideri passare alla visualizzazione progettazione per creare un gestore eventi.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

### <a name="to-create-an-event-handler-in-visual-basic"></a>Per creare un gestore eventi in Visual Basic

1. Dall'elenco a discesa **nome classe** nella parte superiore dell'editor di codice, selezionare l'oggetto per il quale si vuole creare un gestore eventi.

    > [!NOTE]
    > Se si desidera creare gestori eventi per `ThisDocument` o `ThisWorkbook` , è necessario selezionare **(eventi ThisDocument)** o **(eventi ThisWorkbook)** nell'elenco a discesa **nome classe** .

2. Dall'elenco a discesa **nome metodo** nella parte superiore dell'editor di codice, selezionare l'evento.

     Visual Studio crea il gestore eventi e sposta il punto di inserimento nel gestore eventi appena creato. Se il gestore eventi esiste già, il punto di inserimento viene spostato nel gestore eventi esistente.

### <a name="to-create-an-event-handler-in-c"></a>Per creare un gestore eventi in C\#

1. Creare il delegato dell'evento nell'evento di **avvio** della classe digitando il nome completo dell'evento seguito da uno spazio, quindi digitando senza spazio in un secondo momento **+=** . Ad esempio:

     `this.<object name>.<event name> +=`

2. Alla fine della riga di codice, premere il tasto TAB due volte.

     Visual Studio completa automaticamente la riga di codice, crea il gestore eventi e sposta il punto di inserimento nel gestore eventi appena creato.

## <a name="see-also"></a>Vedi anche
- [Scrivere codice nelle soluzioni Office](../vsto/writing-code-in-office-solutions.md)
- [Procedura dettagliata: programma per eventi di un controllo NamedRange](../vsto/walkthrough-programming-against-events-of-a-namedrange-control.md)
- [Compilazione di soluzioni Office](../vsto/building-office-solutions.md)
