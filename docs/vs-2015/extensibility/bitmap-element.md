---
title: Elemento bitmap | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- VSCT XML schema elements, Bitmaps
- Bitmaps element (VSCT XML schema)
ms.assetid: edcd7891-f4e7-416d-809d-5e2eed9f17e4
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: fc1fb57c7ec43421b211b29cfd6ab97b24a1864c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68184737"
---
# <a name="bitmap-element"></a>Elemento Bitmap
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Definisce una bitmap. La bitmap viene caricata da una risorsa o da un file.  
  
## <a name="syntax"></a>Sintassi  
  
```  
<Bitmap guid="guidImages" href="images\MyImage.bmp" usedList="bmp1, bmp2, bmp3" />  
```  
  
## <a name="attributes-and-elements"></a>Attributi ed elementi  
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.  
  
### <a name="attributes"></a>Attributi  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|guid|Obbligatorio. GUID dell'identificatore del comando GUID/ID.<br /><br /> L'attributo GUID per una bitmap non è associato ad alcun VSPackage o altro gruppo di comandi.  Deve essere univoco per la definizione di bitmap e non deve essere usato per altri scopi.|  
|Da un Resid|ID dell'identificatore del comando GUID/ID. È necessario specificare l'attributo da un Resid o href.<br /><br /> L'attributo da un Resid è un ID di risorsa integer che determina l'elenco bitmap da caricare durante l'Unione della tabella dei comandi.  Quando viene caricata la tabella dei comandi, le bitmap specificate dall'ID risorsa verranno caricate dalla risorsa dello stesso modulo.|  
|utilizzato|Obbligatorio se è presente l'attributo da un Resid. Seleziona le immagini disponibili nell'elenco bitmap.|  
|href|Percorso della bitmap. È necessario specificare l'attributo da un Resid o href.<br /><br /> Il percorso di inclusione viene cercato per il file di immagine indicato, incorporato nel file binario risultante.  Durante l'Unione della tabella dei comandi, l'immagine viene copiata e non è necessaria alcuna ricerca o carico aggiuntivo per le risorse.  Se l'attributo used non è presente, sono disponibili tutte le immagini nella striscia. **Nota:**  Le immagini possono essere fornite in uno dei diversi formati che includono. bmp,. png e. gif.  Le versioni precedenti del compilatore non supportavano immagini bitmap a 32 bit contenenti informazioni Alpha per la trasparenza parziale. La soluzione alternativa per queste versioni consiste nell'usare il formato png.|  
|Condizione|facoltativo. Vedere [attributi condizionali](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### <a name="child-elements"></a>Elementi figlio  
 Nessuno.  
  
### <a name="parent-elements"></a>Elementi padre  
  
|Elemento|Descrizione|  
|-------------|-----------------|  
|[Elemento Bitmaps](../extensibility/bitmaps-element.md)|Raggruppa gli elementi bitmap.|  
  
## <a name="example"></a>Esempio  
  
```  
<Bitmap guid="guidWidgetIcons" href="WidgetToolbarIcons_32.bmp" />  
<Bitmap guid="guidWidgetIcons2" resID="IDBMP_WIDGETICONS"  
  usedList="1, 2, 3, 4"/>  
```  
  
## <a name="see-also"></a>Vedere anche  
 [File Visual Studio Command Table (con estensione vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
