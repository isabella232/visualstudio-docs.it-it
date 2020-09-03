---
title: 'Procedura: localizzare una funzionalità | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- features [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, localizing
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: b0d15654ba48b6c95cf2b2f7fa4f9cd665f0959a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "86016143"
---
# <a name="how-to-localize-a-feature"></a>Procedura: localizzare una funzionalità
  Per impostazione predefinita, i titoli e le descrizioni delle funzionalità usano valori di stringa hardcoded. Per localizzare il titolo e la descrizione della funzionalità, sostituire le stringhe con espressioni che fanno riferimento a risorse localizzate.

## <a name="localize-a-feature"></a>Localizzare una funzionalità

#### <a name="to-localize-a-feature"></a>Per localizzare una funzionalità

1. In **Esplora soluzioni**aprire il menu di scelta rapida per il nodo **Feature1** , quindi scegliere **Aggiungi risorsa funzionalità**.

2. Nella finestra di dialogo **Aggiungi risorsa** scegliere **lingua** inglese dall'elenco come impostazioni cultura per il file di risorse della funzionalità della lingua predefinita.

3. Ripetere il passaggio precedente per ogni lingua localizzata, selezionando le lingue desiderate per i file di risorse della funzionalità localizzati.

     Vengono creati file di risorse di funzionalità separati, uno per la lingua predefinita e uno per ogni lingua localizzata da supportare.

4. Aprire ogni file di risorse nell'Editor risorse e immettere tutti gli ID di stringa e i relativi valori.

     Ad esempio, nel file di risorse della funzionalità predefinita, immettere un ID di stringa **title** con un valore del **titolo della funzionalità**e un secondo ID di stringa **Description** con un valore della **Descrizione della funzionalità My**. Per ogni file di risorse localizzato, utilizzare gli stessi ID di stringa utilizzati nella risorsa della funzionalità predefinita, ma immettere stringhe localizzate per i valori.

5. Dopo aver immesso tutti i valori delle risorse, aprire il menu di scelta rapida per la funzionalità (ad esempio, *Feature1. feature*), quindi scegliere **Visualizza finestra di progettazione** per aprire la funzionalità nella finestra di progettazione della funzionalità.

6. Per localizzare i campi **titolo** e **Descrizione** nella funzionalità, usare il formato seguente per immettere i valori nelle caselle:

     `$Resources:` *ID stringa*

     Ad esempio, immettere $Resources:**title** nella casella **titolo funzionalità** e $Resources:**Description** nella casella **Descrizione funzionalità** .

     Gli ID di stringa devono corrispondere a quelli utilizzati nei file di risorse.

7. Premere il tasto **F5** per compilare ed eseguire l'applicazione.

8. In SharePoint aprire il menu **Azioni sito** , scegliere **Impostazioni sito**e quindi nella sezione **Azioni sito** scegliere il collegamento **Gestisci caratteristiche sito** .

9. In SharePoint modificare la lingua di visualizzazione dal valore predefinito.

     Il titolo e la descrizione della funzionalità localizzata vengono visualizzati nell'applicazione. Per visualizzare le risorse localizzate, è necessario che nel server SharePoint sia installato un Language Pack corrispondente alle impostazioni cultura del file di risorse.

## <a name="see-also"></a>Vedere anche
- [Localizzare le soluzioni SharePoint](../sharepoint/localizing-sharepoint-solutions.md)
- [Procedura: aggiungere un file di risorse](../sharepoint/how-to-add-a-resource-file.md)
- [Procedura: localizzare il markup ASPX](../sharepoint/how-to-localize-aspx-markup.md)
- [Procedura: localizzare il codice](../sharepoint/how-to-localize-code.md)
