---
title: Elemento FeatureProperties | Microsoft Docs
description: Visualizzare le informazioni di riferimento sull'elemento FeatureProperties, che è un elemento nello schema SharePoint dell'elemento di progetto.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- FeatureProperties element
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: d3bfb1a8e53c72f4a3d70e69658d78f8c336e9cf
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126625248"
---
# <a name="featureproperties-element"></a>FeatureProperties (elemento)
  Raccolta di valori di proprietà inclusi in una funzionalità quando viene distribuita in SharePoint. Dopo aver distribuito una funzionalità, è possibile accedere ai valori delle proprietà nel codice.

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
|[Proprietà Funzionalità](../sharepoint/featureproperty-element.md)|Elemento facoltativo.<br /><br /> Rappresenta una proprietà personalizzata, in formato chiave/valore.|

### <a name="parent-elements"></a>Elementi padre

|Elemento|Descrizione|
|-------------|-----------------|
|[ProjectItem](../sharepoint/projectitem-element.md)|Rappresenta un elemento SharePoint progetto. Questo elemento è l'elemento radice obbligatorio del `.spdata` file.|

## <a name="remarks"></a>Commenti
 Per altre informazioni sulle proprietà delle funzionalità, vedere [Fornire informazioni sulla creazione di pacchetti e sulla distribuzione negli elementi del progetto.](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)

## <a name="element-information"></a>Informazioni sull'elemento

|Elemento|Descrizione|
|-------------|-----------------|
|**Namespace**|http: \/ \/ schemas.microsoft.com/VisualStudio/<br>2010/SharePointTools/SharePointProjectItemModel|
|**Nome schema**|SharePoint Project schema dell'elemento|
|**File di convalida**|ProjectItemModelSchema.xsd|
|**Può essere vuoto**|No|

## <a name="see-also"></a>Vedere anche
- [SharePoint sullo schema dell'elemento di progetto](../sharepoint/sharepoint-project-item-schema-reference.md)
- [Fornire informazioni sulla creazione di pacchetti e sulla distribuzione negli elementi del progetto](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)
