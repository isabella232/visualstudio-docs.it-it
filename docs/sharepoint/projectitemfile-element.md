---
title: Elemento ProjectItemFile | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ProjectItemFile element
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 73578d564714ff6e596dca62942f12e24589d235
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/24/2019
ms.locfileid: "54867742"
---
# <a name="projectitemfile-element"></a>ProjectItemFile (elemento)
  Rappresenta un file di SharePoint, ad esempio file di elemento di funzionalità, da includere con l'elemento del progetto quando viene distribuito in SharePoint.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
<ProjectItemFile Source = "Name of the file"  
    Target = "Deployment path of the file"  
    Type = "Type of deployment for the file" />  
```  
  
## <a name="type"></a>Tipo  
 **ProjectItemFileType**  
  
## <a name="attributes-and-elements"></a>Attributi ed elementi
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.  
  
### <a name="attributes"></a>Attributi  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|**Origine**|Obbligatorio **xs: String** attributo.<br /><br /> Il nome del file da distribuire con l'elemento del progetto.|  
|**Destinazione**|Facoltativo **xs: String** attributo.<br /><br /> Il percorso in cui verrà distribuito il file in SharePoint, relativo alla cartella radice di distribuzione. Cartella radice di distribuzione è determinata dal tipo di distribuzione specificato per il **tipo** attributo. Se il **destinazione** attributo viene omesso, il file verrà distribuito in una cartella con il nome specificato nella **origine** attributo.<br /><br /> Per altre informazioni, vedere le descrizioni per le **percorso di distribuzione** e **Deployment Root** le proprietà di SharePoint elementi nel progetto [SharePoint sviluppare soluzioni](../sharepoint/developing-sharepoint-solutions.md).|  
|**Type**|Obbligatorio **xs: String** attributo.<br /><br /> Il tipo di distribuzione per il file. Per altre informazioni sui possibili valori, vedere la descrizione per il **tipo di distribuzione** proprietà di elementi di progetto SharePoint in [soluzioni SharePoint sviluppare](../sharepoint/developing-sharepoint-solutions.md).|  
  
### <a name="child-elements"></a>Elementi figlio
 Nessuno.  
  
### <a name="parent-elements"></a>Elementi padre
  
|Elemento|Descrizione|  
|-------------|-----------------|  
|[File](../sharepoint/files-element.md)|Specifica i file da includere con l'elemento del progetto SharePoint quando viene distribuito in SharePoint.|  
  
## <a name="remarks"></a>Note  
 I file di SharePoint che in genere fanno riferimento a **ProjectItemFile** gli elementi includono i file di elemento di funzionalità (*Elements. XML*), file di schema per le definizioni di elenco (*schema*) e i file di definizione di Web Part per Web part (*WebPart*).  
  
## <a name="element-information"></a>Informazioni sull'elemento
  
|||  
|-|-|  
|**Spazio dei nomi**|http<nolink>://schemas.microsoft.com/VisualStudio/<br>2010/SharePointTools/SharePointProjectItemModel|  
|**Nome dello schema**|Schema degli elementi di progetto SharePoint|  
|**File di convalida**|ProjectItemModelSchema.xsd|  
|**Può essere vuoto**|No|  
  
## <a name="see-also"></a>Vedere anche
 [Riferimento dello schema elementi di progetto SharePoint](../sharepoint/sharepoint-project-item-schema-reference.md)  
