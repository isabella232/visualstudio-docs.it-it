---
title: Elemento FeatureProperty | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- FeatureProperty element
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 3dc58683d2cff7e6c25493924b63666c390cdffc
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53991188"
---
# <a name="featureproperty-element"></a>FeatureProperty (elemento)
  Rappresenta una proprietà personalizzata che è inclusa in una funzione quando viene distribuito in SharePoint. Dopo aver distribuita una funzionalità, è possibile accedere alla proprietà nel codice.  
  
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
|**Key**|Obbligatorio **xs: String** attributo.<br /><br /> La chiave utilizzata per archiviare e recuperare il valore della proprietà. Ogni proprietà devono avere una chiave univoca all'interno della funzionalità.|  
|**Valore**|Obbligatorio **xs: String** attributo.<br /><br /> Valore della proprietà.|  
  
### <a name="child-elements"></a>Elementi figlio
 Nessuno.  
  
### <a name="parent-elements"></a>Elementi padre
  
|Elemento|Descrizione|  
|-------------|-----------------|  
|[FeatureProperties](../sharepoint/featureproperties-element.md)|Rappresenta una raccolta di valori di proprietà che sono inclusi in una funzione quando viene distribuito in SharePoint.|  
  
## <a name="remarks"></a>Note  
 Per altre informazioni sulle proprietà di funzionalità, vedere [fornendo informazioni pacchetto e distribuzione negli elementi di progetto](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md).  
  
## <a name="element-information"></a>Informazioni sull'elemento
  
|||  
|-|-|  
|**Spazio dei nomi**|HTTP<nolink>: //schemas.microsoft.com/VisualStudio/<br>2010/SharePointTools/SharePointProjectItemModel|  
|**Nome dello schema**|Schema degli elementi di progetto SharePoint|  
|**File di convalida**|ProjectItemModelSchema.xsd|  
|**Può essere vuoto**|No|  
  
## <a name="see-also"></a>Vedere anche
 [Riferimento dello schema elementi di progetto SharePoint](../sharepoint/sharepoint-project-item-schema-reference.md)   
 [Fornire le informazioni di creazione di pacchetti e distribuzione negli elementi di progetto](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)  
