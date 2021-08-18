---
title: Creazione di colonne del sito, tipi di contenuto ed elenchi per SharePoint | Microsoft Docs
titleSuffix: ''
description: Creare colonne del sito, tipi di contenuto ed elenchi per SharePoint. Visual Studio fornisce modelli di elemento di progetto per questi tipi di SharePoint elementi.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.ListDesigner.ContentTypeSetting
- VS.SharePointTools.ContentTypeDesigner.CommonPropertiesPage
- VS.SharePointTools.ListDesigner.CreatingLists
- VS.SharePointTools.ListDesigner.ListPage
- VS.SharePointTools.ListDesigner.ViewPage
- VS.SharePointTools.ListDesigner.CommonPropertiesPage
- VS.SharePointTools.ContentTypeDesigner.ColumnsPage
dev_langs:
- VB
- CSharp
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: 40ca1ca19e15e0e25e4decf6a3b932a3bcbf78b5
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122149442"
---
# <a name="create-site-columns-content-types-and-lists-for-sharepoint"></a>Creare colonne del sito, tipi di contenuto ed elenchi per SharePoint
  Visual Studio fornisce modelli di elemento di progetto per molti elementi  SharePoint fondamentali diversi, inclusi elenchi e tipi di *contenuto,* entrambi in grado di incorporare colonne del sito (o *campi*). Grazie alle nuove finestre di progettazione per i tipi di contenuto e gli elenchi, la creazione di questi elementi non è mai stata più facile.

## <a name="site-columns"></a>Colonne del sito
 Le colonne del sito sono uno degli elementi più semplici che si possono aggiungere a un progetto di SharePoint. Una colonna del sito rappresenta un tipo di dati, ad esempio un numero di telefono, un commento o il nome della città di un contatto in un elenco di contatti.

 Grazie al nuovo modello per gli elementi di progetto delle colonne del sito, la creazione di queste colonne è più semplice rispetto alle versioni precedenti di Visual Studio. Dopo aver creato una nuova colonna del sito, è possibile modificare il codice XML nel file *Elements.xml* della colonna del sito per includere le informazioni desiderate, ad esempio il nome visualizzato, il tipo di dati e il gruppo in cui si desidera che la colonna del sito venga visualizzata in SharePoint. Per altre informazioni sulle colonne del sito, vedere [Introduzione alle colonne.](/previous-versions/office/developer/sharepoint-2010/ms450825(v=office.14))

## <a name="content-types-and-lists"></a>Tipi di contenuto ed elenchi
 I tipi di contenuto e gli elenchi sono tra gli elementi più frequentemente utilizzati in SharePoint.

 Con un tipo di contenuto vengono definiti i metadati, il flusso di lavoro e il comportamento di una categoria di elementi in un elenco o in una raccolta documenti di SharePoint. Ad esempio, è possibile creare un tipo di contenuto per le informazioni in un elenco di contatti o in un elenco di attività. In un tipo di contenuto del contatto possono essere incluse colonne come quelle relative al nome, alla posta elettronica, al numero di telefono e all'indirizzo. Un tipo di contenuto definito a livello di sito è indipendente da qualsiasi elenco o raccolta documenti nel sito. È possibile utilizzare lo stesso tipo di contenuto con diversi elenchi o raccolte documenti nel sito di SharePoint. È inoltre possibile utilizzare diversi tipi di contenuto nello stesso elenco o raccolta documenti.

 Un elenco è una raccolta di informazioni in SharePoint condivisibile con altri utenti. Gli elenchi sono costituiti da righe di colonne contenenti i dati. Alcuni esempi di elenchi prevedono un elenco di attività, un elenco di contatti e un elenco di annunci.

 Grazie alle nuove finestre di progettazione per il tipo di contenuto e per l'elenco in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], la creazione dei tipi di contenuto e degli elenchi è molto più facile e intuitiva rispetto alle versioni precedenti di Visual Studio. Con l'interfaccia utente è possibile creare visivamente i tipi di contenuto e gli elenchi in modo comune, consentendo di ordinare e raggruppare i dati in elenchi e utilizzare le intestazioni di gruppo. Per altre informazioni sui tipi di contenuto, vedere [Tipi di contenuto.](/previous-versions/office/developer/sharepoint-2010/ms479905(v=office.14)) Per altre informazioni sugli elenchi, vedere [Form elenco e](/previous-versions/office/developer/sharepoint-2010/aa543232(v=office.14)) [Visualizzazioni elenco.](/previous-versions/office/developer/sharepoint-2010/ff604021(v=office.14))

## <a name="related-topics"></a>Argomenti correlati

|Titolo|Descrizione|
|-----------|-----------------|
|[Procedura dettagliata: Creare una colonna del sito, un tipo di contenuto ed un elenco per SharePoint](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md)|Viene illustrato come creare colonne del sito utilizzate in un tipo di contenuto personalizzato. Il tipo di contenuto viene quindi utilizzato in un elenco personalizzato.|

## <a name="see-also"></a>Vedi anche
- [Informazioni di base Sviluppo in SharePoint 2010](/sharepoint/dev/)
