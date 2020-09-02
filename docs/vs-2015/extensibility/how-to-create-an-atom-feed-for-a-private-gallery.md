---
title: 'Procedura: creare un feed Atom per una raccolta privata | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Atom feed, VSIX private galleries
- VSIX private galleries, Atom feed
ms.assetid: 5897f538-9c41-486f-97d9-a1976d20d9fd
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f6d4ba78028774e8fbf8e281afa2855781dab43a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204207"
---
# <a name="how-to-create-an-atom-feed-for-a-private-gallery"></a>Procedura: Creare un feed atom per una raccolta privata
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

È possibile creare un feed Atom (RSS) in un percorso Intranet che contiene le estensioni e aggiungere il feed ad **estensioni e aggiornamenti** come raccolta privata. Per altre informazioni, vedere [raccolte private](../extensibility/private-galleries.md).  
  
## <a name="creating-an-atom-feed"></a>Creazione di un feed Atom  
 Per creare un feed Atom come raccolta privata, è necessario innanzitutto raccogliere le estensioni (file VSIX) in una cartella. Se lo si desidera, è possibile organizzarle in sottocartelle. Sono necessarie anche le risorse seguenti:  
  
- Un file atom.xml che rende le estensioni disponibili come raccolta privata. Per informazioni su come connettere il file di atom.xml a **estensioni e aggiornamenti**, vedere [raccolte private](../extensibility/private-galleries.md).  
  
- Cartella che contiene i file di immagine estratti dalle estensioni (ad esempio, schermate). Il file di atom.xml contiene collegamenti relativi a queste immagini in modo che siano disponibili in **estensioni e aggiornamenti**.  
  
  Si supponga, ad esempio, di aver raccolto le due estensioni seguenti in una cartella:  
  
- Template_Wizard_239. vsix, ovvero un modello di progetto VSIX vuoto.  
  
- SelectionHighlight. vsix, uno strumento che consente di evidenziare tutte le istanze di una parola selezionata.  
  
  Il contenuto del file atom.xml sarà simile all'esempio seguente:  
  
```  
  <?xml version="1.0" encoding="utf-8" ?>   
- <feed xmlns="http://www.w3.org/2005/Atom">  
  <title type="text" />   
  <id>uuid:bcecded5-97c8-4d24-96f1-7d9e16652433;id=1</id>   
  <updated>2011-04-14T21:25:48Z</updated>   
- <entry>  
  <id>SelectionHighlight..a14874d2-8199-4a60-af8a-11d6447813aa</id>   
  <title type="text">Highlight all occurrences of selected word</title>   
  <summary type="text">This extends the editor to highlight ….</summary>   
  <published>2011-04-14T14:24:51-07:00</published>   
  <updated>2011-04-14T14:24:22-07:00</updated>   
- <author>  
  <name>Microsoft</name>   
  </author>  
  <link rel="icon" href="VSIXImages/SelectionHighlight..a14874d2-8199-4a60-af8a-11d6447813aa_Icon_SelectionHighlightIcon.jpg" />   
  <link rel="previewimage" href="VSIXImages/SelectionHighlight..a14874d2-8199-4a60-af8a-11d6447813aa_PreviewImage_SelectionHighlight.jpg" />   
  <content type="application/octet-stream" src="SelectionHighlight.vsix" />   
- <Vsix xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns="http://schemas.microsoft.com/developer/vsx-syndication-schema/2010">  
  <Id>SelectionHighlight..a14874d2-8199-4a60-af8a-11d6447813aa</Id>   
  <Version>1.31</Version>   
  <References />   
  <Rating xsi:nil="true" />   
  <RatingCount xsi:nil="true" />   
  <DownloadCount xsi:nil="true" />   
  </Vsix>  
  </entry>  
- <entry>  
  <id>Template_Wizard_239.Microsoft.3b38a7e3-5cbc-4389-a92a-d82tyc2ed592</id>   
  …  
  </entry>  
  </feed>  
  
```  
  
 Si noti che i due tag di collegamento fanno riferimento a schermate nella cartella generata di immagini.  
  
## <a name="see-also"></a>Vedere anche  
 [Raccolte private](../extensibility/private-galleries.md)
