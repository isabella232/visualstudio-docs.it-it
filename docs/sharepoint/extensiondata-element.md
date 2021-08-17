---
title: Elemento ExtensionData | Microsoft Docs
description: Visualizzare informazioni di riferimento sull'elemento ExtensionData, che è un elemento nello SharePoint schema dell'elemento di progetto.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ExtensionData element
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: f175c0b4cdc4a9b5fb9537821d2ffcc646d44bf14119a132d7561439e92f5e6a
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121425375"
---
# <a name="extensiondata-element"></a>ExtensionData (elemento)
  Rappresenta una raccolta di elementi di dati personalizzati associati all'SharePoint di progetto.

## <a name="syntax"></a>Sintassi

```xml
<ExtensionData>
  <ExtensionDataItem.../>
</ExtensionData>
```

## <a name="attributes-and-elements"></a>Attributi ed elementi
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.

### <a name="attributes"></a>Attributi
 Nessuno.

### <a name="child-elements"></a>Elementi figlio

|Elemento|Descrizione|
|-------------|-----------------|
|[ExtensionDataItem](../sharepoint/extensiondataitem-element.md)|Elemento facoltativo.<br /><br /> Rappresenta un elemento di dati personalizzato associato all'SharePoint di progetto, in formato chiave/valore. Sia la chiave che il valore devono essere stringhe.|

### <a name="parent-elements"></a>Elementi padre

|Elemento|Descrizione|
|-------------|-----------------|
|[ProjectItem](../sharepoint/projectitem-element.md)|Rappresenta un SharePoint di progetto. Questo elemento è l'elemento radice obbligatorio del `.spdata` file.|

## <a name="remarks"></a>Commenti
 Quando si associano dati personalizzati a un elemento di progetto SharePoint usando la proprietà di un oggetto , Visual Studio salva i dati nell'elemento ExtensionData nel file per l'elemento <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem> di  `.spdata` progetto. Per altre informazioni, vedere [Salvare i dati nelle estensioni del SharePoint di progetto](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md).

## <a name="element-information"></a>Informazioni sull'elemento

|Proprietà|Valore|
|-|-|
|**Namespace**|http: \/ \/ schemas.microsoft.com/VisualStudio/<br>2010/SharePointTools/SharePointProjectItemModel|
|**Nome schema**|SharePoint Project schema dell'elemento|
|**File di convalida**|ProjectItemModelSchema.xsd|
|**Può essere vuoto**|No|

## <a name="see-also"></a>Vedere anche
- [SharePoint riferimento allo schema dell'elemento di progetto](../sharepoint/sharepoint-project-item-schema-reference.md)
