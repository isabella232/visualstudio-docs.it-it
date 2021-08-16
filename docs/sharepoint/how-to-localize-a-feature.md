---
title: 'Procedura: Localizzare una funzionalità | Microsoft Docs'
description: Informazioni su come localizzare i titoli e le descrizioni delle funzionalità SharePoint sostituendo i valori stringa hard-coded con espressioni che fanno riferimento alle risorse localizzate.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: 71bf8d8c9d211fea35ee4f9d603c439ebaf911ed89da292d2ef40a7b83b7ac7f
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121385224"
---
# <a name="how-to-localize-a-feature"></a>Procedura: Localizzare una funzionalità
  Per impostazione predefinita, i titoli e le descrizioni delle funzionalità usano valori stringa hard-coded. Per localizzare il titolo e la descrizione della funzionalità, sostituire le stringhe con espressioni che fanno riferimento alle risorse localizzate.

## <a name="localize-a-feature"></a>Localizzare una funzionalità

#### <a name="to-localize-a-feature"></a>Per localizzare una funzionalità

1. In **Esplora soluzioni** aprire il menu di scelta rapida per il **nodo Feature1** e quindi scegliere **Aggiungi risorsa funzionalità**.

2. Nella finestra **di dialogo Aggiungi** risorsa scegliere Lingua **invariante** dall'elenco come impostazioni cultura per il file di risorse delle funzionalità della lingua predefinito.

3. Ripetere il passaggio precedente per ogni lingua localizzata, selezionando le lingue desiderate per i file di risorse della funzionalità localizzati.

     Vengono creati file di risorse di funzionalità separati, uno per la lingua predefinita e uno per ogni lingua localizzata da supportare.

4. Aprire ogni file di risorse nell'Editor risorse e immettere tutti gli ID di stringa e i relativi valori.

     Ad esempio, nel file di risorse della  funzionalità predefinito immettere un ID stringa title con valore **My Feature Title** e un secondo ID stringa **Descrizione** con il valore **My Feature Description**. Per ogni file di risorse localizzato, utilizzare gli stessi ID di stringa utilizzati nella risorsa della funzionalità predefinita, ma immettere stringhe localizzate per i valori.

5. Dopo aver immesso tutti i valori delle risorse, aprire il menu di scelta  rapida per la funzionalità, ad esempio *Feature1.feature,* e quindi scegliere Progettazione visualizzazioni per aprire la funzionalità in Progettazione funzionalità.

6. Per localizzare i **campi Titolo** **e** Descrizione nella funzionalità, usare il formato seguente per immettere i valori nelle rispettive caselle:

     `$Resources:` *ID stringa*

     Ad esempio, immettere $Resources:**Titolo** nella casella **Titolo** funzionalità e $Resources:**Descrizione** nella **casella Descrizione** funzionalità.

     Gli ID di stringa devono corrispondere a quelli utilizzati nei file di risorse.

7. Scegliere il **tasto F5** per compilare ed eseguire l'applicazione.

8. In SharePoint aprire il menu **Azioni** sito, scegliere Impostazioni sito **e** quindi nella sezione **Azioni** sito scegliere il collegamento **Gestisci funzionalità** sito.

9. In SharePoint modificare la lingua di visualizzazione rispetto all'impostazione predefinita.

     Il titolo e la descrizione della funzionalità localizzata vengono visualizzati nell'applicazione. Per visualizzare le risorse localizzate, SharePoint server deve essere installato un language pack corrispondente alle impostazioni cultura del file di risorse.

## <a name="see-also"></a>Vedi anche
- [Localizzare SharePoint soluzioni](../sharepoint/localizing-sharepoint-solutions.md)
- [Procedura: Aggiungere un file di risorse](../sharepoint/how-to-add-a-resource-file.md)
- [Procedura: Localizzare il markup ASPX](../sharepoint/how-to-localize-aspx-markup.md)
- [Procedura: Localizzare il codice](../sharepoint/how-to-localize-code.md)
