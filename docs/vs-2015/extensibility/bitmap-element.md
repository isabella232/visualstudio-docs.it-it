---
title: Elemento bitmap | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- VSCT XML schema elements, Bitmaps
- Bitmaps element (VSCT XML schema)
ms.assetid: edcd7891-f4e7-416d-809d-5e2eed9f17e4
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 38d1ad621b22e9007ed36e642b95b0999890521a
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49878362"
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
|guid|Obbligatorio. GUID dell'identificatore di comando/ID GUID.<br /><br /> L'attributo guid per una mappa di bit non è associato alcun pacchetto VSPackage o un altro gruppo di comando.  Deve essere univoco per la definizione della bitmap e non deve essere utilizzata per altri scopi.|  
|resID|ID dell'identificatore di comando/ID GUID. È necessario il resID o l'attributo href.<br /><br /> L'attributo resID è un ID di risorsa di numero intero che determina la striscia di bitmap che deve essere caricato durante l'unione di tabelle di comando.  Durante il caricamento nella tabella del comando, le bitmap specificate mediante l'ID di risorsa verranno caricate dalla risorsa dello stesso modulo.|  
|usedList|Obbligatorio se è presente l'attributo resID. Consente di selezionare le immagini disponibili nella striscia di bitmap.|  
|href|Percorso alla bitmap. È necessario il resID o l'attributo href.<br /><br /> Percorso di inclusione viene cercato il file di immagine indicata, che è incorporato nel file binario risulta.  Durante il merge nella tabella di comando, l'immagine viene copiata ed è necessario alcuna ricerca delle risorse aggiuntive o caricamento.  Se l'attributo usedList non è presente, nell'elenco di tutte le immagini sono disponibili. **Nota:** immagini possono essere specificate in uno dei numerosi formati che includono. bmp, PNG e. gif.  Le versioni precedenti del compilatore non supporta le immagini bitmap a 32 bit che dispone di informazioni alfa per la trasparenza parziale. La soluzione alternativa per queste versioni consiste nell'usare il formato. PNG.|  
|Condizione|Facoltativo. Visualizzare [attributi condizionali](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### <a name="child-elements"></a>Elementi figlio  
 Nessuno.  
  
### <a name="parent-elements"></a>Elementi padre  
  
|Elemento|Descrizione|  
|-------------|-----------------|  
|[Elemento Bitmaps](../extensibility/bitmaps-element.md)|Raggruppa gli elementi mappa di bit.|  
  
## <a name="example"></a>Esempio  
  
```  
<Bitmap guid="guidWidgetIcons" href="WidgetToolbarIcons_32.bmp" />  
<Bitmap guid="guidWidgetIcons2" resID="IDBMP_WIDGETICONS"  
  usedList="1, 2, 3, 4"/>  
```  
  
## <a name="see-also"></a>Vedere anche  
 [File Visual Studio Command Table (VSCT)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

