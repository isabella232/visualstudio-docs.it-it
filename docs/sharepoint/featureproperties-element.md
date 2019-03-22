---
title: Elemento FeatureProperties | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- FeatureProperties element
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 6860a91067daa6da1d4223ae5060385087ad3433
ms.sourcegitcommit: 3d37c2460584f6c61769be70ef29c1a67397cf14
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/21/2019
ms.locfileid: "58323529"
---
# <a name="featureproperties-element"></a>FeatureProperties (elemento)
  Raccolta di valori di proprietà che sono inclusi in una funzione quando viene distribuito in SharePoint. Dopo aver distribuita una funzionalità, è possibile accedere i valori delle proprietà nel codice.

## <a name="syntax"></a>Sintassi

```xml
<FeatureProperties>
  <FeatureProperty.../>
</FeatureProperties>
```

## <a name="attributes-and-elements"></a>Attributi ed elementi
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.

### <a name="attributes"></a>Attributi
 Nessuno.

### <a name="child-elements"></a>Elementi figlio

|Elemento|Descrizione|
|-------------|-----------------|
|[FeatureProperty](../sharepoint/featureproperty-element.md)|Elemento facoltativo.<br /><br /> Rappresenta una proprietà personalizzata, nel formato di chiave/valore.|

### <a name="parent-elements"></a>Elementi padre

|Elemento|Descrizione|
|-------------|-----------------|
|[ProjectItem](../sharepoint/projectitem-element.md)|Rappresenta un elemento del progetto SharePoint. Questo elemento l'elemento radice obbligatorio del `.spdata` file.|

## <a name="remarks"></a>Note
 Per altre informazioni sulle proprietà di funzionalità, vedere [fornire le informazioni di creazione di pacchetti e distribuzione negli elementi di progetto](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md).

## <a name="element-information"></a>Informazioni sull'elemento

|Elemento|Descrizione|
|-------------|-----------------|
|**Spazio dei nomi**|http:\/\/schemas.microsoft.com/VisualStudio/<br>2010/SharePointTools/SharePointProjectItemModel|
|**Nome dello schema**|Schema degli elementi di progetto SharePoint|
|**File di convalida**|ProjectItemModelSchema.xsd|
|**Può essere vuoto**|No|

## <a name="see-also"></a>Vedere anche
- [Riferimento dello schema elementi di progetto SharePoint](../sharepoint/sharepoint-project-item-schema-reference.md)
- [Fornire le informazioni di creazione di pacchetti e distribuzione negli elementi di progetto](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)
