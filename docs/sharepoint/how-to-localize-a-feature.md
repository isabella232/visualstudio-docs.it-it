---
title: 'Procedura: localizzare una funzionalità | Microsoft Docs'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- features [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, localizing
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: c143016aaec81c65c118923ff9513bb4607353dc
ms.sourcegitcommit: d9e4ea95d0ea70827de281754067309a517205a1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/29/2018
ms.locfileid: "37118951"
---
# <a name="how-to-localize-a-feature"></a>Procedura: localizzare una funzionalità
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
 [Localizzazione di soluzioni SharePoint](../sharepoint/localizing-sharepoint-solutions.md)   
 [Procedura: aggiungere un file di risorse](../sharepoint/how-to-add-a-resource-file.md)   
 [Procedura: localizzare il markup ASPX](../sharepoint/how-to-localize-aspx-markup.md)   
 [Procedura: localizzare il codice](../sharepoint/how-to-localize-code.md)  
  
