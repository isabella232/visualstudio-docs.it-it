---
title: 'Procedura: Mappare schemi a documenti di Word in Visual Studio'
titleSuffix: ''
ms.custom: seodec18
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- XML schemas [Office development in Visual Studio], mapping
- mappings [Office development in Visual Studio], XML schemas to Word documents
- Word [Office development in Visual Studio], mapping XML schemas
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 37cdbc07f5defe0c6f8d5613795d2a9c6142521f
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/21/2019
ms.locfileid: "56644705"
---
# <a name="how-to-map-schemas-to-word-documents-inside-visual-studio"></a>Procedura: Mappare schemi a documenti di Word in Visual Studio
  **Importante** le informazioni definite in questo argomento relative a Microsoft Word sono presentati in modo esclusivo per il vantaggio e uso di singoli utenti e le organizzazioni che si trovano di fuori degli Stati Uniti e dei relativi territori o che usano o lo sviluppo i programmi eseguiti su, i prodotti di Microsoft Word che sono stati concessi in licenza da Microsoft prima di gennaio del 2010 quando Microsoft ha rimosso un'implementazione di una funzionalità specifica correlato a XML personalizzata da Microsoft Word. Queste informazioni relative a Microsoft Word non possono essere lette o utilizzate dagli singoli individui o organizzazioni negli Stati Uniti o relativo territori che usano o lo sviluppo di programmi in esecuzione in, i prodotti di Microsoft Word che sono stati concessi in licenza da Microsoft dopo il 10 gennaio 2010 ; tali prodotti non si comporterà come prodotti concessi in licenza prima di tale data o acquistati e concesso in licenza per l'utilizzo di fuori degli Stati Uniti.

 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]

 È possibile eseguire il mapping di un XML schema a un documento mentre il documento è aperto in Visual Studio. Si usano gli stessi strumenti di Microsoft Office Word utilizzata quando il documento viene aperto all'esterno di Visual Studio. Il progetto di Office consente di creare gli stessi oggetti se lo schema è mappato al documento prima o dopo aver creato la soluzione di Word.

## <a name="to-map-an-xml-schema-to-a-word-document-in-visual-studio"></a>Eseguire il mapping di un XML schema a un documento di Word in Visual Studio

1.  Aprire il progetto di modello o documento di Word in Visual Studio.

2.  Fare clic nel documento per spostare lo stato attivo alla finestra di progettazione.

3.  Sulla barra multifunzione, fare clic sui **sviluppatore** scheda.

    > [!NOTE]
    >  Se la scheda **Sviluppatore** non viene mostrata, è necessario abilitarne la visualizzazione. Per altre informazioni, vedere [Procedura: Visualizzare la scheda sviluppo nella barra multifunzione](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).

4.  Nel **XML** gruppo, fare clic su **Schema**.

     Il **modelli e componenti aggiuntivi** verrà visualizzata la finestra di dialogo.

5.  Scegliere il **XML Schema** scheda.

6.  Fare clic su **aggiungere lo Schema**.

     Il **Aggiungi Schema** verrà visualizzata la finestra di dialogo.

7.  Passare al file di schema, selezionarlo e quindi fare clic su **aperto**.

     Il **le impostazioni dello Schema** verrà visualizzata la finestra di dialogo.

8.  Assegnare un alias o fare clic su **OK** aggiungere lo schema senza un alias.

9. Fare clic su **OK**.

     Il **struttura XML** verrà visualizzata la finestra.

10. Trascinare gli elementi dal **struttura XML** finestra per le posizioni all'interno del documento in cui si desidera corrispondenti controlli da creare.

## <a name="see-also"></a>Vedere anche
- [Procedura: Mappare schemi a fogli di lavoro in Visual Studio](../vsto/how-to-map-schemas-to-worksheets-inside-visual-studio.md)
- [XML schema e dati nelle personalizzazioni a livello di documento](../vsto/xml-schemas-and-data-in-document-level-customizations.md)
