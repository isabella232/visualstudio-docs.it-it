---
title: 'Procedura: Localizzare una funzionalità | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: conceptual
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
ms.openlocfilehash: 0d811b27f810ac9becf23513a25937e1a265d305
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/21/2019
ms.locfileid: "56639089"
---
# <a name="how-to-localize-a-feature"></a>Procedura: Localizzare una funzionalità
  Per impostazione predefinita, le descrizioni e titoli delle funzionalità utilizzano i valori di stringa hardcoded. Per localizzare il titolo della funzionalità e la descrizione, sostituire le stringhe con le espressioni che fanno riferimento alle risorse localizzate.

## <a name="localize-a-feature"></a>Localizzare una funzionalità

#### <a name="to-localize-a-feature"></a>Per localizzare una funzionalità

1.  Nella **Esplora soluzioni**, aprire il menu di scelta rapida per il **Feature1** nodo, quindi scegliere **Aggiungi risorsa funzionalità**.

2.  Nel **Aggiungi risorsa** finestra di dialogo, scegliere **lingua invariante** dall'elenco come impostazioni cultura per il file di risorse predefinito funzionalità del linguaggio.

3.  Ripetere il passaggio precedente per ogni lingua localizzata, selezionando le lingue desiderate per i file di risorse della funzionalità localizzati.

     Vengono creati file di risorse di funzionalità separati, uno per la lingua predefinita e uno per ogni lingua localizzata da supportare.

4.  Aprire ogni file di risorse nell'Editor risorse e immettere tutti gli ID di stringa e i relativi valori.

     Ad esempio, nel file di risorse di funzionalità di impostazione predefinita, immettere un ID stringa del **Title** con il valore **My Feature Title**, e un secondo ID di stringa **descrizione** con un valore di **My Feature Description**. Per ogni file di risorse localizzato, utilizzare gli stessi ID di stringa utilizzati nella risorsa della funzionalità predefinita, ma immettere stringhe localizzate per i valori.

5.  Dopo aver immesso tutti i valori della risorsa, aprire il menu di scelta rapida per la funzionalità (ad esempio, *Feature1*), quindi scegliere **Progettazione viste** per aprire la funzionalità nella finestra di progettazione di funzionalità.

6.  Per localizzare il **Title** e **descrizione** campi nella funzionalità, usare il formato seguente per immettere i valori desiderati nelle rispettive caselle:

     `$Resources:` *ID stringa*

     Ad esempio, immettere $Resources:**titolo** nel **Feature Title** box e $Resources:**descrizione** nel **descrizione funzionalità** casella .

     Gli ID di stringa devono corrispondere a quelli utilizzati nei file di risorse.

7.  Scegliere il **F5** chiave per compilare ed eseguire l'applicazione.

8.  In SharePoint, aprire il **Azioni sito** dal menu scegliere **Impostazioni sito**, quindi il **Azioni sito** sezione scegliere il **Gestisci caratteristiche sito** collegamento.

9. In SharePoint, cambiare la lingua di visualizzazione da quello predefinito.

     Il titolo della funzionalità localizzato e la descrizione visualizzata nell'applicazione. Per visualizzare le risorse localizzate, il server di SharePoint deve avere installato un language pack corrispondente alle impostazioni cultura del file di risorse.

## <a name="see-also"></a>Vedere anche
- [Localizzazione di soluzioni SharePoint](../sharepoint/localizing-sharepoint-solutions.md)
- [Procedura: Aggiungere un file di risorse](../sharepoint/how-to-add-a-resource-file.md)
- [Procedura: Localizzare il markup ASPX](../sharepoint/how-to-localize-aspx-markup.md)
- [Procedura: Localizzare il codice](../sharepoint/how-to-localize-code.md)
