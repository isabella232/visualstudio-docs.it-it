---
title: 'Procedura: Creare gestori eventi in Office progetti'
description: Informazioni sui diversi modi in cui è possibile creare gestori eventi predefiniti per i controlli in Visual Basic e C#.
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
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 6a3ef99f7032f3112ec65a110259a2ad7b3af6ba
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122122839"
---
# <a name="how-to-create-event-handlers-in-office-projects"></a>Procedura: Creare gestori eventi in Office progetti
  Esistono diversi modi per creare gestori eventi in Visual Basic e C#. Nella visualizzazione Progettazione è possibile creare i gestori eventi predefiniti per i controlli facendo  doppio clic sul controllo oppure usare il riquadro eventi della finestra Proprietà per creare gestori per qualsiasi evento nel controllo. Tuttavia, se si è nella visualizzazione Codice, potrebbe non essere necessario passare alla visualizzazione Progettazione per creare un gestore eventi.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

### <a name="to-create-an-event-handler-in-visual-basic"></a>Per creare un gestore eventi in Visual Basic

1. **Nell'elenco a** discesa Nome classe nella parte superiore dell'editor di codice selezionare l'oggetto per cui si vuole creare un gestore eventi.

    > [!NOTE]
    > Per creare gestori eventi per o , è necessario selezionare `ThisDocument` `ThisWorkbook` **(Eventi ThisDocument)** o  **(Eventi ThisWorkbook)** nell'elenco a discesa Nome classe

2. **Nell'elenco a discesa** Nome metodo nella parte superiore dell'editor di codice selezionare l'evento.

     Visual Studio crea il gestore eventi e sposta il punto di inserimento nel gestore eventi appena creato. Se il gestore eventi esiste già, il punto di inserimento viene spostato nel gestore eventi esistente.

### <a name="to-create-an-event-handler-in-c"></a>Per creare un gestore eventi in C\#

1. Creare il delegato dell'evento nell'evento **Startup** della classe digitando il nome completo dell'evento seguito da uno spazio e quindi digitando senza **+=** spazi in seguito. Esempio:

     `this.<object name>.<event name> +=`

2. Alla fine della riga di codice premere tab due volte.

     Visual Studio completa automaticamente la riga di codice, crea il gestore eventi e sposta il punto di inserimento nel gestore eventi appena creato.

## <a name="see-also"></a>Vedi anche
- [Scrivere codice in Office soluzioni](../vsto/writing-code-in-office-solutions.md)
- [Procedura dettagliata: Programmare in base agli eventi di un controllo NamedRange](../vsto/walkthrough-programming-against-events-of-a-namedrange-control.md)
- [Creare Office soluzioni](../vsto/building-office-solutions.md)
