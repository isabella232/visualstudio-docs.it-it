---
title: 'Procedura: Aggiungere controlli XMLNodes ai documenti di Word'
description: Si apprenderà che quando si esegue il mapping di un elemento xml schema ripetuto Microsoft Office documento di Word, Visual Studio aggiunge automaticamente un controllo XMLNodes al documento.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- XMLNodes control, adding to documents
- controls [Office development in Visual Studio], adding to documents
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 69320f9734951bae3af6a4bf5447302435db1541
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122122852"
---
# <a name="how-to-add-xmlnodes-controls-to-word-documents"></a>Procedura: Aggiungere controlli XMLNodes ai documenti di Word
  **Importante** Le informazioni contenute in questo argomento relative a Microsoft Word vengono presentate esclusivamente a vantaggio e all'uso di utenti e organizzazioni che si trovano al di fuori del Stati Uniti e dei relativi territori o che usano o sviluppano programmi in esecuzione su prodotti Microsoft Word concessi in licenza da Microsoft prima di gennaio 2010, quando Microsoft ha rimosso un'implementazione di funzionalità specifiche correlate al codice XML personalizzato da Microsoft Word. Queste informazioni relative Microsoft Word non possono essere lette o usate da singoli utenti o organizzazioni nel Stati Uniti o nei relativi territori che usano o sviluppano programmi in esecuzione su prodotti Microsoft Word concessi in licenza da Microsoft dopo il 10 gennaio 2010; tali prodotti non si comporteranno come i prodotti concessi in licenza prima di tale data o acquistati e concessi in licenza per l'uso al di fuori del Stati Uniti.

 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]

 Quando si esegue il mapping di un elemento dello schema XML ripetuto a un documento Microsoft Office Word, Visual Studio aggiunge automaticamente <xref:Microsoft.Office.Tools.Word.XMLNodes> un controllo al documento.

 Per informazioni sul mapping di elementi xml schema non ripetuti, vedere [Procedura: Aggiungere controlli XMLNode ai documenti di Word.](../vsto/how-to-add-xmlnode-controls-to-word-documents.md)

> [!NOTE]
> Il <xref:Microsoft.Office.Tools.Word.XMLNodes> controllo non è  disponibile dalla casella degli strumenti o dalla **finestra Origini** dati, né può essere creato a livello di codice.

 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

### <a name="to-add-an-xmlnodes-control-to-a-document"></a>Per aggiungere un controllo XMLNodes a un documento

1. Nella finestra di progettazione Visual Studio documento fare clic sulla scheda Sviluppo **sulla barra multifunzione.**

    > [!NOTE]
    > Se la scheda **Sviluppatore** non viene mostrata, è necessario abilitarne la visualizzazione. Per altre informazioni, vedere [Procedura: Visualizzare la scheda Sviluppatore sulla barra multifunzione.](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md)

2. Nel gruppo **XML** fare clic su **Schema**.

     Verrà **visualizzata la finestra di** dialogo Modelli e componenti aggiuntivi.

3. Fare clic **sulla scheda XML Schema.**

4. Fare clic **su Aggiungi schema**.

     Verrà **visualizzata la finestra** di dialogo Aggiungi schema .

5. Selezionare uno schema XML contenente elementi dello schema ripetuti e fare clic su **Apri**.

     Verrà **visualizzata la Impostazioni** schema .

6. Assegnare un alias o fare clic **su OK** per aggiungere lo schema senza un alias.

     Lo schema viene aggiunto alla **finestra di dialogo Aggiungi** schema .

7. Nella finestra **di dialogo Aggiungi** schema fare clic su **OK**.

     Verrà visualizzato il riquadro attività Struttura **XML.**

8. Fare clic sull'elemento dello schema ripetuto nel riquadro attività **Struttura XML** per aggiungerlo al documento.

     Un <xref:Microsoft.Office.Tools.Word.XMLNodes> controllo viene creato e aggiunto al progetto.

## <a name="see-also"></a>Vedi anche
- [Controllo XMLNodes](../vsto/xmlnodes-control.md)
- [Automatizzare Word usando oggetti estesi](../vsto/automating-word-by-using-extended-objects.md)
- [Panoramica degli elementi host e dei controlli host](../vsto/host-items-and-host-controls-overview.md)
- [Limitazioni a livello di codice di elementi host e controlli host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
