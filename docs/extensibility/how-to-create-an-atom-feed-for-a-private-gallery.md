---
title: 'Procedura: Creare un feed Atom per una raccolta privata | Microsoft Docs'
description: È possibile creare un feed Atom (RSS) in un percorso Intranet che contiene estensioni e aggiungere il feed a Estensioni e aggiornamenti come raccolta privata.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- Atom feed, VSIX private galleries
- VSIX private galleries, Atom feed
ms.assetid: 5897f538-9c41-486f-97d9-a1976d20d9fd
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: eff01da3538e1a2d36b18031e7871c64461ed83f0340b0e0a177f7b080f505b3
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121376469"
---
# <a name="how-to-create-an-atom-feed-for-a-private-gallery"></a>Procedura: Creare un feed Atom per una raccolta privata
È possibile creare un feed Atom (RSS) in un percorso Intranet che contiene estensioni e aggiungere il feed a Estensioni e **aggiornamenti** come raccolta privata. Per altre informazioni, vedere [Private Galleries](../extensibility/private-galleries.md) (Raccolte private).

## <a name="create-an-atom-feed"></a>Creare un feed Atom
 Per creare un feed Atom come raccolta privata, è prima di tutto necessario raccogliere le estensioni (file con estensione *vsix)* in una cartella. Se necessario, è possibile organizzarli in sottocartelle. Sono necessarie anche le risorse seguenti:

- Un *atom.xml* file che rende disponibili le estensioni come raccolta privata. Per informazioni su come connettere il file *atom.xml* ad **Estensioni e aggiornamenti,** vedere [Raccolte private](../extensibility/private-galleries.md).

- Cartella che contiene tutti i file di immagine estratti dalle estensioni, ad esempio schermate. Il *atom.xml* file contiene collegamenti relativi a queste immagini in modo che siano disponibili in **Estensioni e aggiornamenti**.

  Si supponga, ad esempio, di aver raccolto le due estensioni seguenti in una cartella:

- *Template_Wizard_239.vsix*, che è un modello di progetto VSIX vuoto.

- *SelectionHighlight.vsix,* che è uno strumento per evidenziare tutte le istanze di una parola selezionata.

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

 Si noti che i due tag di collegamento fanno riferimento alle schermate nella cartella generata delle immagini.

## <a name="see-also"></a>Vedi anche
- [Raccolte private](../extensibility/private-galleries.md)
