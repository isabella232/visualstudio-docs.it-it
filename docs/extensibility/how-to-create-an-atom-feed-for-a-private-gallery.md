---
title: 'Procedura: Creare un Atom per una raccolta privata di Feed | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Atom feed, VSIX private galleries
- VSIX private galleries, Atom feed
ms.assetid: 5897f538-9c41-486f-97d9-a1976d20d9fd
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 0f761bd99fe13822c0e3a5abdb35be85bd3395ef
ms.sourcegitcommit: 01185dadd2fa1f9a040d2a366869f1a5e1d18e0f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/11/2019
ms.locfileid: "54227915"
---
# <a name="how-to-create-an-atom-feed-for-a-private-gallery"></a>Procedura: Creare un feed Atom per una raccolta privata
È possibile creare un Atom (RSS) feed da un percorso intranet che contiene le estensioni e aggiunta il feed a **estensioni e aggiornamenti** come una raccolta privata. Per altre informazioni, vedere [raccolte Private](../extensibility/private-galleries.md).  
  
## <a name="create-an-atom-feed"></a>Creare un feed Atom  
 Per creare un feed come una raccolta privata Atom, è prima di tutto raccogliere le estensioni (*VSIX* file) in una cartella. È possibile organizzarle in sottocartelle, se si desidera. È necessario anche le risorse seguenti:  
  
- Un' *atom.xml* file che rende disponibili le estensioni come una raccolta privata. Per informazioni su come connettere il *atom.xml* del file ai **estensioni e aggiornamenti**, vedere [raccolte Private](../extensibility/private-galleries.md).  
  
- Una cartella che contiene tutti i file di immagine che sono stati estratti dalle estensioni (ad esempio, schermate). Il *atom.xml* file contiene i collegamenti relativi a queste immagini in modo che siano disponibili nei **estensioni e aggiornamenti**.  
  
  Si supponga, ad esempio, che sono state raccolte le due estensioni seguenti in una cartella:  
  
- *Template_Wizard_239.VSIX*, ovvero un modello di progetto VSIX vuoto.  
  
- *SelectionHighlight.vsix*, ovvero uno strumento per evidenziare tutte le istanze di una parola selezionata.  
  
  Il contenuto del *atom.xml* file sarà simile al seguente:  
  
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
  
 Si noti che i due tag di collegamento vedere catture di schermata nella cartella delle immagini generata.  
  
## <a name="see-also"></a>Vedere anche  
 [Raccolte private](../extensibility/private-galleries.md)
