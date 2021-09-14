---
title: Elemento ExtensionData | Microsoft Docs
description: Visualizzare le informazioni di riferimento sull'elemento ExtensionData, che è un elemento nello schema SharePoint dell'elemento di progetto.
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
ms.openlocfilehash: ec317073601f766dab2042ab6c77542914e87b59
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126625254"
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
|[ExtensionDataItem](../sharepoint/extensiondataitem-element.md)|Elemento facoltativo.<br /><br /> Rappresenta un elemento di dati personalizzato associato all'SharePoint progetto, in formato chiave/valore. Sia la chiave che il valore devono essere stringhe.|

### <a name="parent-elements"></a>Elementi padre

|Elemento|Descrizione|
|-------------|-----------------|
|[ProjectItem](../sharepoint/projectitem-element.md)|Rappresenta un SharePoint di progetto. Questo elemento è l'elemento radice obbligatorio del `.spdata` file.|

## <a name="remarks"></a>Commenti
 Quando si associano dati personalizzati a un elemento di progetto SharePoint usando la proprietà di un oggetto, Visual Studio salva i dati nell'elemento ExtensionData nel file per l'elemento <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem> di  `.spdata` progetto. Per altre informazioni, vedere [Salvare i dati nelle estensioni del SharePoint di progetto.](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md)

## <a name="element-information"></a>Informazioni sull'elemento

|Proprietà|Valore|
|-|-|
|**Namespace**|http: \/ \/ schemas.microsoft.com/VisualStudio/<br>2010/SharePointTools/SharePointProjectItemModel|
|**Nome schema**|SharePoint Project schema dell'elemento|
|**File di convalida**|ProjectItemModelSchema.xsd|
|**Può essere vuoto**|No|

## <a name="see-also"></a>Vedere anche
- [SharePoint sullo schema dell'elemento di progetto](../sharepoint/sharepoint-project-item-schema-reference.md)
