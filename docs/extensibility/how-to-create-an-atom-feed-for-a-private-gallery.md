---
title: 'Procedura: Creare un feed atomo per una galleria privata Documenti Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Atom feed, VSIX private galleries
- VSIX private galleries, Atom feed
ms.assetid: 5897f538-9c41-486f-97d9-a1976d20d9fd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c72fbf2d3973ffd84de1cf6f33788c43511c3ce4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711004"
---
# <a name="how-to-create-an-atom-feed-for-a-private-gallery"></a>Procedura: Creare un feed Atom per una raccolta privataHow to: Create an Atom feed for a private gallery
È possibile creare un feed Atom (RSS) in un percorso Intranet contenente estensioni e aggiungere il feed a **Estensioni e aggiornamenti** come raccolta privata. Per altre informazioni, vedere [Private Galleries](../extensibility/private-galleries.md) (Raccolte private).

## <a name="create-an-atom-feed"></a>Creare un feed Atom
 Per creare un feed Atom come raccolta privata, è innanzitutto necessario raccogliere le estensioni (file*VSIX)* in una cartella. Se lo si desidera, è possibile organizzarli in sottocartelle. Sono inoltre necessarie le seguenti risorse:

- Un file *atom.xml* che rende le estensioni disponibili come raccolta privata. Per informazioni su come connettere il file *atom.xml* a **Estensioni e aggiornamenti**, vedere [Raccolte private](../extensibility/private-galleries.md).

- Una cartella che contiene tutti i file di immagine estratti dalle estensioni (ad esempio, schermate). Il file *atom.xml* contiene collegamenti relativi a queste immagini in modo che siano disponibili in **Estensioni e aggiornamenti**.

  Si supponga, ad esempio, di aver raccolto le due estensioni seguenti in una cartella:

- *Template_Wizard_239.vsix*, che è un modello di progetto VSIX vuoto.

- *SelectionHighlight.vsix*, che è uno strumento per evidenziare tutte le istanze di una parola selezionata.

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

 Si noti che i due tag di collegamento fanno riferimento alle schermate nella cartella delle immagini generate.

## <a name="see-also"></a>Vedere anche
- [Gallerie private](../extensibility/private-galleries.md)
