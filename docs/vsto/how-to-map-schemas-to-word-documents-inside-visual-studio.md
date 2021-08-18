---
title: "Procedura: Eseguire il mapping di schemi a documenti di Word all'interno Visual Studio"
description: Informazioni su come eseguire il mapping di uno schema XML a Microsoft Office documento di Word mentre il documento è aperto in Visual Studio.
titleSuffix: ''
ms.custom: seodec18, SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- XML schemas [Office development in Visual Studio], mapping
- mappings [Office development in Visual Studio], XML schemas to Word documents
- Word [Office development in Visual Studio], mapping XML schemas
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: e14283c61480796e58cd2f5df0b055fb66ce2ac5
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122083440"
---
# <a name="how-to-map-schemas-to-word-documents-inside-visual-studio"></a>Procedura: Eseguire il mapping di schemi a documenti di Word all'interno Visual Studio
  **Importante** Le informazioni contenute in questo argomento relative a Microsoft Word vengono presentate esclusivamente a vantaggio e all'uso di singoli utenti e organizzazioni che si trovano all'esterno del Stati Uniti e dei relativi territori o che usano o sviluppano programmi eseguiti su prodotti Microsoft Word concessi in licenza da Microsoft prima di gennaio 2010, quando Microsoft ha rimosso un'implementazione di particolari funzionalità correlate al codice XML personalizzato da Microsoft Word. Queste informazioni relative Microsoft Word non possono essere lette o usate da singoli utenti o organizzazioni nel Stati Uniti o nei relativi territori che usano o sviluppano programmi eseguiti su prodotti Microsoft Word concessi in licenza da Microsoft dopo il 10 gennaio 2010; Tali prodotti non si comporteranno come i prodotti concessi in licenza prima di tale data o acquistati e concessi in licenza per l'uso al di fuori del Stati Uniti.

 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]

 È possibile eseguire il mapping di uno schema XML a un documento mentre il documento è aperto in Visual Studio. Usare gli stessi strumenti Microsoft Office Word utilizzati quando il documento è aperto all'esterno Visual Studio. Il Office crea gli stessi oggetti indipendentemente dal fatto che lo schema venga mappato al documento prima o dopo la creazione della soluzione Word.

## <a name="to-map-an-xml-schema-to-a-word-document-in-visual-studio"></a>Per eseguire il mapping di uno schema XML a un documento di Word in Visual Studio

1. Aprire il progetto di documento o modello di Word all'interno Visual Studio.

2. Fare clic nel documento per spostare lo stato attivo sulla finestra di progettazione.

3. Sulla barra multifunzione fare clic sulla **scheda** Sviluppatore.

    > [!NOTE]
    > Se la scheda **Sviluppatore** non viene mostrata, è necessario abilitarne la visualizzazione. Per altre informazioni, vedere [Procedura: Visualizzare la scheda Sviluppatore sulla barra multifunzione.](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md)

4. Nel gruppo **XML** fare clic su **Schema**.

     Verrà **visualizzata la finestra di dialogo Modelli** e componenti aggiuntivi .

5. Fare clic **sulla scheda XML Schema** .

6. Fare clic **su Aggiungi schema.**

     Verrà **visualizzata la finestra** di dialogo Aggiungi schema .

7. Passare al file di schema, selezionarlo e quindi fare clic su **Apri.**

     Verrà **visualizzata la Impostazioni** schema .

8. Assegnare un alias o fare clic **su OK** per aggiungere lo schema senza un alias.

9. Fare clic su **OK**.

     Verrà **visualizzata la finestra Struttura XML.**

10. Trascinare elementi dalla **finestra Struttura XML** nelle posizioni del documento in cui si desidera creare i controlli corrispondenti.

## <a name="see-also"></a>Vedi anche
- [Procedura: Eseguire il mapping degli schemi ai fogli di lavoro all'interno Visual Studio](../vsto/how-to-map-schemas-to-worksheets-inside-visual-studio.md)
- [Xml Schema e dati nelle personalizzazioni a livello di documento](../vsto/xml-schemas-and-data-in-document-level-customizations.md)
