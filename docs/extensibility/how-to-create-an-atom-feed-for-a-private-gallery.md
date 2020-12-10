---
title: 'Procedura: creare un feed Atom per una raccolta privata | Microsoft Docs'
description: È possibile creare un feed Atom (RSS) in un percorso Intranet che contiene le estensioni e aggiungere il feed ad estensioni e aggiornamenti come raccolta privata.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- Atom feed, VSIX private galleries
- VSIX private galleries, Atom feed
ms.assetid: 5897f538-9c41-486f-97d9-a1976d20d9fd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 833d75d7dfd18e863664e6d3d17d65a4e08b4d77
ms.sourcegitcommit: d10f37dfdba5d826e7451260c8370fd1efa2c4e4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/10/2020
ms.locfileid: "96994147"
---
# <a name="how-to-create-an-atom-feed-for-a-private-gallery"></a>Procedura: creare un feed Atom per una raccolta privata
È possibile creare un feed Atom (RSS) in un percorso Intranet che contiene le estensioni e aggiungere il feed ad **estensioni e aggiornamenti** come raccolta privata. Per altre informazioni, vedere [Private Galleries](../extensibility/private-galleries.md) (Raccolte private).

## <a name="create-an-atom-feed"></a>Creare un feed Atom
 Per creare un feed Atom come raccolta privata, è necessario innanzitutto raccogliere le estensioni (file *VSIX* ) in una cartella. Se lo si desidera, è possibile organizzarle in sottocartelle. Sono necessarie anche le risorse seguenti:

- Un file *atom.xml* che rende le estensioni disponibili come raccolta privata. Per informazioni su come connettere il file di *atom.xml* a **estensioni e aggiornamenti**, vedere [raccolte private](../extensibility/private-galleries.md).

- Cartella che contiene i file di immagine estratti dalle estensioni (ad esempio, schermate). Il file di *atom.xml* contiene collegamenti relativi a queste immagini in modo che siano disponibili in **estensioni e aggiornamenti**.

  Si supponga, ad esempio, di aver raccolto le due estensioni seguenti in una cartella:

- *Template_Wizard_239. vsix*, ovvero un modello di progetto VSIX vuoto.

- *SelectionHighlight. vsix*, uno strumento che consente di evidenziare tutte le istanze di una parola selezionata.

  Il contenuto del file *atom.xml* sarà simile all'esempio seguente:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<feed xmlns="http://www.w3.org/2005/Atom">
  <title type="text" />
  <id>uuid:bcecded5-97c8-4d24-96f1-7d9e16652433;id=1</id>
  <updated>2011-04-14T21:25:48Z</updated>
  <entry>
    <id>SelectionHighlight..a14874d2-8199-4a60-af8a-11d6447813aa</id>
    <title type="text">Highlight all occurrences of selected word</title>
    <summary type="text">This extends the editor to highlight ....</summary>
    <published>2011-04-14T14:24:51-07:00</published>
    <updated>2011-04-14T14:24:22-07:00</updated>
    <author>
      <name>Microsoft</name>
    </author>
    <link rel="icon" href="VSIXImages/SelectionHighlight..a14874d2-8199-4a60-af8a-11d6447813aa_Icon_SelectionHighlightIcon.jpg" />
    <link rel="previewimage" href="VSIXImages/SelectionHighlight..a14874d2-8199-4a60-af8a-11d6447813aa_PreviewImage_SelectionHighlight.jpg" />
    <content type="application/octet-stream" src="SelectionHighlight.vsix" />
    <Vsix xmlns="http://schemas.microsoft.com/developer/vsx-syndication-schema/2010" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
      <Id>SelectionHighlight..a14874d2-8199-4a60-af8a-11d6447813aa</Id>
      <Version>1.31</Version>
      <References />
      <Rating xsi:nil="true" />
      <RatingCount xsi:nil="true" />
      <DownloadCount xsi:nil="true" />
    </Vsix>
  </entry>
  <entry>
    <id>Template_Wizard_239.Microsoft.3b38a7e3-5cbc-4389-a92a-d82tyc2ed592</id>
    ...
  </entry>
</feed>
```

 Si noti che i due tag di collegamento fanno riferimento a schermate nella cartella generata di immagini.

## <a name="see-also"></a>Vedere anche
- [Raccolte private](../extensibility/private-galleries.md)
