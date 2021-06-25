---
title: Elemento Bitmap | Microsoft Docs
description: L'elemento Bitmap definisce una bitmap. La bitmap viene caricata da una risorsa o da un file. Questo articolo contiene un esempio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- VSCT XML schema elements, Bitmaps
- Bitmaps element (VSCT XML schema)
ms.assetid: edcd7891-f4e7-416d-809d-5e2eed9f17e4
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: c8f3daf25a3ffe025bcdef65dbaa6def942d0fb4
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/25/2021
ms.locfileid: "112903320"
---
# <a name="bitmap-element"></a>Elemento Bitmap
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
|guid|Obbligatorio. GUID dell'identificatore del comando GUID/ID.<br /><br /> L'attributo guid per una bitmap non è associato ad alcun VSPackage o a un altro gruppo di comandi.  Deve essere univoco per la definizione della bitmap e non deve essere usato per altri scopi.|
|Resid|ID dell'identificatore del comando GUID/ID. L'attributo resID o href è obbligatorio.<br /><br /> L'attributo resID è un ID risorsa integer che determina la striscia bitmap da caricare durante l'unione della tabella dei comandi.  Quando viene caricata la tabella dei comandi, le bitmap specificate dall'ID risorsa verranno caricate dalla risorsa dello stesso modulo.|
|usedList|Obbligatorio se è presente l'attributo resID. Seleziona le immagini disponibili nella striscia bitmap.|
|href|Percorso della bitmap. L'attributo resID o href è obbligatorio.<br /><br /> Nel percorso di inclusione viene cercato il file di immagine indicato, incorporato nel file binario risultante.  Durante l'unione della tabella dei comandi, l'immagine viene copiata e non è necessaria alcuna ricerca o caricamento di risorse aggiuntive.  Se l'attributo usedList non è presente, tutte le immagini nella striscia sono disponibili. **Nota:**  Le immagini possono essere fornite in uno dei diversi formati che includono.bmp *,* *.png* e *.gif*.  Le versioni precedenti del compilatore non supportavano immagini bitmap a 32 bit con informazioni alfa per la trasparenza parziale. La soluzione alternativa per queste versioni consiste nell'usare il *.png* predefinito.|
|Condizione|facoltativo. Vedere [Attributi condizionali](../extensibility/vsct-xml-schema-conditional-attributes.md).|

### <a name="child-elements"></a>Elementi figlio
 Nessuno.

### <a name="parent-elements"></a>Elementi padre

|Elemento|Descrizione|
|-------------|-----------------|
|[Elemento Bitmaps](../extensibility/bitmaps-element.md)|Raggruppa gli elementi Bitmap.|

## <a name="example"></a>Esempio

```
<Bitmap guid="guidWidgetIcons" href="WidgetToolbarIcons_32.bmp" />
<Bitmap guid="guidWidgetIcons2" resID="IDBMP_WIDGETICONS"
  usedList="1, 2, 3, 4"/>
```

## <a name="see-also"></a>Vedere anche
- [Visual Studio file di tabella dei comandi (con estensione vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
