---
title: 'Procedura: eseguire il mapping degli schemi a documenti di Word in Visual Studio'
description: Informazioni su come è possibile eseguire il mapping di un XML Schema a un documento Microsoft Office Word mentre il documento è aperto in Visual Studio.
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
ms.workload:
- office
ms.openlocfilehash: 082d5fe4fbcc7f66709770c16d3c9a1a2811e60d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99900924"
---
# <a name="how-to-map-schemas-to-word-documents-inside-visual-studio"></a>Procedura: eseguire il mapping degli schemi a documenti di Word in Visual Studio
  **Importante** Le informazioni contenute in questo argomento riguardanti Microsoft Word sono presentate esclusivamente per il vantaggio e l'utilizzo di singoli utenti e organizzazioni che si trovano al di fuori del Stati Uniti e dei suoi territori o che utilizzano o sviluppano programmi eseguiti in Microsoft Word, che sono stati concessi in licenza da Microsoft prima del gennaio 2010, quando Microsoft ha rimosso un'implementazione di particolari funzionalità correlate a XML personalizzato da Microsoft Word. Queste informazioni relative a Microsoft Word non possono essere lette o usate da singoli utenti o organizzazioni nel Stati Uniti o nei suoi territori che usano o sviluppano programmi eseguiti in Microsoft Word prodotti concessi in licenza da Microsoft dopo il 10 gennaio 2010; tali prodotti non si comporteranno come prodotti concessi in licenza prima di tale data o acquistati e concessi in licenza per l'utilizzo al di fuori del Stati Uniti.

 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]

 È possibile eseguire il mapping di un XML Schema a un documento mentre il documento è aperto in Visual Studio. Si usano gli stessi strumenti Microsoft Office Word usati quando il documento è aperto all'esterno di Visual Studio. Il progetto di Office crea gli stessi oggetti se si esegue il mapping dello schema al documento prima o dopo aver creato la soluzione Word.

## <a name="to-map-an-xml-schema-to-a-word-document-in-visual-studio"></a>Per eseguire il mapping di un XML Schema a un documento di Word in Visual Studio

1. Aprire il documento di Word o il progetto di modello all'interno di Visual Studio.

2. Fare clic nel documento per spostare lo stato attivo sulla finestra di progettazione.

3. Sulla barra multifunzione fare clic sulla scheda **Developer** .

    > [!NOTE]
    > Se la scheda **Sviluppatore** non viene mostrata, è necessario abilitarne la visualizzazione. Per ulteriori informazioni, vedere [procedura: visualizzare la scheda Developer sulla barra multifunzione](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).

4. Nel gruppo **XML** fare clic su **schema**.

     Verrà visualizzata la finestra di dialogo **modelli e componenti** aggiuntivi.

5. Fare clic sulla scheda **XML Schema** .

6. Fare clic su **Aggiungi schema**.

     Verrà visualizzata la finestra di dialogo **Aggiungi schema** .

7. Individuare il file di schema, selezionarlo e quindi fare clic su **Apri**.

     Verrà visualizzata la finestra di dialogo **Impostazioni schema** .

8. Assegnare un alias oppure fare clic su **OK** per aggiungere lo schema senza un alias.

9. Fare clic su **OK**.

     Verrà visualizzata la finestra **struttura XML** .

10. Trascinare gli elementi dalla finestra **struttura XML** alle posizioni nel documento in cui si desidera creare i controlli corrispondenti.

## <a name="see-also"></a>Vedi anche
- [Procedura: eseguire il mapping di schemi a fogli di fogli di Visual Studio](../vsto/how-to-map-schemas-to-worksheets-inside-visual-studio.md)
- [XML Schema e dati nelle personalizzazioni a livello di documento](../vsto/xml-schemas-and-data-in-document-level-customizations.md)
