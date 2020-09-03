---
title: Elemento ExtensionData | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ExtensionData element
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 3b700239f97153cef94ab1d7010ad16ed9aa6001
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "85546562"
---
# <a name="extensiondata-element"></a>ExtensionData (elemento)
  Rappresenta una raccolta di elementi di dati personalizzati associati all'elemento del progetto SharePoint.

## <a name="syntax"></a>Sintassi

```xml
<ExtensionData>
  <ExtensionDataItem.../>
</ExtensionData>
```

## <a name="attributes-and-elements"></a>Attributi ed elementi
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.

### <a name="attributes"></a>Attributes
 Nessuno.

### <a name="child-elements"></a>Elementi figlio

|Elemento|Descrizione|
|-------------|-----------------|
|[ExtensionDataItem](../sharepoint/extensiondataitem-element.md)|Elemento facoltativo.<br /><br /> Rappresenta un elemento di dati personalizzato associato all'elemento del progetto SharePoint, in formato chiave/valore. Sia la chiave che il valore devono essere stringhe.|

### <a name="parent-elements"></a>Elementi padre

|Elemento|Descrizione|
|-------------|-----------------|
|[ProjectItem](../sharepoint/projectitem-element.md)|Rappresenta un elemento del progetto SharePoint. Questo elemento è l'elemento radice obbligatorio del `.spdata` file.|

## <a name="remarks"></a>Osservazioni
 Quando si associano dati personalizzati a un elemento del progetto SharePoint usando la <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> proprietà di un <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem> oggetto, Visual Studio salva i dati nell'elemento **ExtensionData** del `.spdata` file per l'elemento di progetto. Per ulteriori informazioni, vedere [salvare i dati nelle estensioni del sistema del progetto SharePoint](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md).

## <a name="element-information"></a>Informazioni sull'elemento

|Proprietà|Valore|
|-|-|
|**Namespace**|http: \/ \/ schemas.Microsoft.com/VisualStudio/<br>2010/SharePointTools/SharePointProjectItemModel|
|**Nome schema**|Schema dell'elemento del progetto SharePoint|
|**File di convalida**|ProjectItemModelSchema. xsd|
|**Può essere vuoto**|No|

## <a name="see-also"></a>Vedere anche
- [Riferimento allo schema degli elementi di progetto SharePoint](../sharepoint/sharepoint-project-item-schema-reference.md)
