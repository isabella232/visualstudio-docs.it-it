---
title: 'Procedura: aggiungere controlli XMLNodes ai documenti di Word'
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 95fc165c1a3123d68529f6ccaea99fea963c2a67
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "85543494"
---
# <a name="how-to-add-xmlnodes-controls-to-word-documents"></a>Procedura: aggiungere controlli XMLNodes ai documenti di Word
  **Importante** Le informazioni contenute in questo argomento riguardanti Microsoft Word sono presentate esclusivamente per il vantaggio e l'utilizzo di singoli utenti e organizzazioni che si trovano al di fuori del Stati Uniti e dei suoi territori o che utilizzano o sviluppano programmi eseguiti in Microsoft Word, che sono stati concessi in licenza da Microsoft prima del gennaio 2010, quando Microsoft ha rimosso un'implementazione di particolari funzionalità correlate a XML personalizzato da Microsoft Word. Queste informazioni relative a Microsoft Word non possono essere lette o usate da singoli utenti o organizzazioni nel Stati Uniti o nei suoi territori che usano o sviluppano programmi eseguiti in Microsoft Word prodotti concessi in licenza da Microsoft dopo il 10 gennaio 2010; tali prodotti non si comporteranno come prodotti concessi in licenza prima di tale data o acquistati e concessi in licenza per l'utilizzo al di fuori del Stati Uniti.

 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]

 Quando si esegue il mapping di un elemento XML Schema ripetuto a un documento Microsoft Office Word, Visual Studio aggiunge automaticamente un <xref:Microsoft.Office.Tools.Word.XMLNodes> controllo al documento.

 Per informazioni sul mapping di elementi XML Schema non ripetuti, vedere [procedura: aggiungere controlli XMLNode ai documenti di Word](../vsto/how-to-add-xmlnode-controls-to-word-documents.md).

> [!NOTE]
> Il <xref:Microsoft.Office.Tools.Word.XMLNodes> controllo non è disponibile dalla **casella degli strumenti** o dalla finestra **origini dati** , né può essere creato a livello di codice.

 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

### <a name="to-add-an-xmlnodes-control-to-a-document"></a>Per aggiungere un controllo XMLNodes a un documento

1. Nel documento nella finestra di progettazione di Visual Studio fare clic sulla scheda **Developer** sulla barra multifunzione.

    > [!NOTE]
    > Se la scheda **Sviluppatore** non viene mostrata, è necessario abilitarne la visualizzazione. Per ulteriori informazioni, vedere [procedura: visualizzare la scheda Developer sulla barra multifunzione](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).

2. Nel gruppo **XML** fare clic su **schema**.

     Verrà visualizzata la finestra di dialogo **modelli e componenti** aggiuntivi.

3. Fare clic sulla scheda **XML Schema** .

4. Fare clic su **Aggiungi schema**.

     Verrà visualizzata la finestra di dialogo **Aggiungi schema** .

5. Selezionare un XML Schema che contenga elementi dello schema ripetuti e fare clic su **Apri**.

     Verrà visualizzata la finestra di dialogo **Impostazioni schema** .

6. Assegnare un alias oppure fare clic su **OK** per aggiungere lo schema senza un alias.

     Lo schema viene aggiunto alla finestra di dialogo **Aggiungi schema** .

7. Nella finestra di dialogo **Aggiungi schema** fare clic su **OK**.

     Viene visualizzato il riquadro attività **struttura XML** .

8. Fare clic sull'elemento schema ripetuto nel riquadro attività **struttura XML** per aggiungerlo al documento.

     <xref:Microsoft.Office.Tools.Word.XMLNodes>Viene creato un controllo che viene aggiunto al progetto.

## <a name="see-also"></a>Vedere anche
- [XMLNodes (controllo)](../vsto/xmlnodes-control.md)
- [Automatizzare Word usando oggetti estesi](../vsto/automating-word-by-using-extended-objects.md)
- [Cenni preliminari sugli elementi e sui controlli host](../vsto/host-items-and-host-controls-overview.md)
- [Limitazioni a livello di codice degli elementi e dei controlli host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
