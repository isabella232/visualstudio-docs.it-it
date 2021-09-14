---
title: Elemento FeatureProperty | Microsoft Docs
description: Visualizzare le informazioni di riferimento sull'elemento FeatureProperty, che è un elemento nello schema SharePoint dell'elemento di progetto.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- FeatureProperty element
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: 01536094bdb9fd084b32ce56429d085f5f377f8f
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126625217"
---
# <a name="featureproperty-element"></a>FeatureProperty (elemento)
  Rappresenta una proprietà personalizzata inclusa in un oggetto Feature quando viene distribuita in SharePoint. Dopo aver distribuito una funzionalità, è possibile accedere alla proprietà nel codice.

## <a name="syntax"></a>Sintassi

```xml
<FeatureProperty Key = "Key of the property value"
    Value = "Property value" />
```

## <a name="attributes-and-elements"></a>Attributi ed elementi
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.

### <a name="attributes"></a>Attributi

|Attributo|Descrizione|
|---------------|-----------------|
|**Chiave**|Attributo **xs:string** obbligatorio.<br /><br /> Chiave utilizzata per archiviare e recuperare il valore della proprietà. Ogni proprietà deve avere una chiave univoca all'interno della funzionalità.|
|**Valore**|Attributo **xs:string** obbligatorio.<br /><br /> Valore della proprietà.|

### <a name="child-elements"></a>Elementi figlio
 Nessuno.

### <a name="parent-elements"></a>Elementi padre

|Elemento|Descrizione|
|-------------|-----------------|
|[Proprietà funzionalità](../sharepoint/featureproperties-element.md)|Rappresenta una raccolta di valori di proprietà inclusi in un oggetto Feature quando viene distribuito in SharePoint.|

## <a name="remarks"></a>Commenti
 Per altre informazioni sulle proprietà delle funzionalità, vedere [Fornire informazioni sul pacchetto e sulla distribuzione negli elementi del progetto.](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)

## <a name="element-information"></a>Informazioni sull'elemento

|Proprietà|Valore|
|-|-|
|**Namespace**|http: \/ \/ schemas.microsoft.com/VisualStudio/<br>2010/SharePointTools/SharePointProjectItemModel|
|**Nome schema**|SharePoint Project schema dell'elemento|
|**File di convalida**|ProjectItemModelSchema.xsd|
|**Può essere vuoto**|No|

## <a name="see-also"></a>Vedere anche
- [SharePoint sullo schema dell'elemento di progetto](../sharepoint/sharepoint-project-item-schema-reference.md)
- [Fornire informazioni sulla creazione di pacchetti e sulla distribuzione negli elementi del progetto](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)
