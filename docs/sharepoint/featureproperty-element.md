---
title: Elemento FeatureProperty | Microsoft Docs
description: Visualizzare le informazioni di riferimento sull'elemento FeatureProperty, che è un elemento nello schema dell'elemento del progetto SharePoint.
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
ms.workload:
- office
ms.openlocfilehash: 070866b9dd14d974eb976b22bf7a79907e2c5d9e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99876667"
---
# <a name="featureproperty-element"></a>FeatureProperty (elemento)
  Rappresenta una proprietà personalizzata inclusa con una funzionalità quando viene distribuita in SharePoint. Dopo la distribuzione di una funzionalità, è possibile accedere alla proprietà nel codice.

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
|**Chiave**|Attributo **xs: String** obbligatorio.<br /><br /> Chiave utilizzata per archiviare e recuperare il valore della proprietà. Ogni proprietà deve avere una chiave univoca all'interno della funzionalità.|
|**Valore**|Attributo **xs: String** obbligatorio.<br /><br /> Valore della proprietà.|

### <a name="child-elements"></a>Elementi figlio
 Nessuna.

### <a name="parent-elements"></a>Elementi padre

|Elemento|Descrizione|
|-------------|-----------------|
|[FeatureProperties](../sharepoint/featureproperties-element.md)|Rappresenta una raccolta di valori di proprietà inclusi in una funzionalità quando viene distribuita in SharePoint.|

## <a name="remarks"></a>Commenti
 Per ulteriori informazioni sulle proprietà delle funzionalità, vedere la pagina relativa [alla fornitura di informazioni sui pacchetti e sulla distribuzione negli elementi di progetto](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md).

## <a name="element-information"></a>Informazioni sull'elemento

|Proprietà|Valore|
|-|-|
|**Namespace**|http: \/ \/ schemas.Microsoft.com/VisualStudio/<br>2010/SharePointTools/SharePointProjectItemModel|
|**Nome schema**|Schema dell'elemento del progetto SharePoint|
|**File di convalida**|ProjectItemModelSchema. xsd|
|**Può essere vuoto**|No|

## <a name="see-also"></a>Vedere anche
- [Riferimento allo schema degli elementi di progetto SharePoint](../sharepoint/sharepoint-project-item-schema-reference.md)
- [Fornire informazioni sulla creazione di pacchetti e sulla distribuzione negli elementi di progetto](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)
