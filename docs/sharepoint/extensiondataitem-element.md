---
title: Elemento ExtensionDataItem | Microsoft Docs
description: Visualizzare le informazioni di riferimento sull'elemento ExtensionDataItem, che è un elemento nello schema SharePoint dell'elemento di progetto.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ExtensionDataItem element
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: b99d9a267b8fb18ec8e238191382d71f558fc3d3
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126625253"
---
# <a name="extensiondataitem-element"></a>ExtensionDataItem (elemento)
  Elemento di dati personalizzato associato all'elemento SharePoint progetto, in formato chiave/valore. Sia la chiave che il valore devono essere stringhe.

## <a name="syntax"></a>Sintassi

```xml
<ExtensionDataItem Key = "Key of the data item"
    Value = "Value of the data item" />
```

## <a name="attributes-and-elements"></a>Attributi ed elementi
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.

### <a name="attributes"></a>Attributi

|Attributo|Descrizione|
|---------------|-----------------|
|**Chiave**|Obbligatorio **xs: attributo** stringa.<br /><br /> Chiave utilizzata per archiviare e recuperare l'elemento di dati.|
|**Valore**|Attributo **xs:string** obbligatorio.<br /><br /> Valore dell'elemento di dati.|

### <a name="child-elements"></a>Elementi figlio
 Nessuno.

### <a name="parent-elements"></a>Elementi padre

|Elemento|Descrizione|
|-------------|-----------------|
|[ExtensionData](../sharepoint/extensiondata-element.md)|Rappresenta una raccolta di elementi di dati personalizzati associati all'SharePoint di progetto.|

## <a name="remarks"></a>Commenti
 Quando si associano dati personalizzati a un elemento di progetto SharePoint usando la proprietà di un oggetto, Visual Studio salva i dati in un nuovo <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem> elemento **ExtensionDataItem** nel file per l'elemento di `.spdata` progetto. Per altre informazioni, vedere [Salvare i dati nelle estensioni del SharePoint di progetto.](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md)

## <a name="element-information"></a>Informazioni sull'elemento

|Proprietà|Valore|
|-|-|
|**Namespace**|http: \/ \/ schemas.microsoft.com/VisualStudio/<br>2010/SharePointTools/SharePointProjectItemModel|
|**Nome schema**|SharePoint Project schema dell'elemento|
|**File di convalida**|ProjectItemModelSchema.xsd|
|**Può essere vuoto**|No|

## <a name="see-also"></a>Vedere anche
- [SharePoint sullo schema dell'elemento di progetto](../sharepoint/sharepoint-project-item-schema-reference.md)
