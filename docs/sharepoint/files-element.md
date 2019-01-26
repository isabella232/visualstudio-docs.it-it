---
title: Elemento di file | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Files element
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: b25bb220d3c22af280a486de115193af38c85dbe
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/24/2019
ms.locfileid: "54864527"
---
# <a name="files-element"></a>Files (elemento)
  Specifica i file da distribuire con l'elemento del progetto SharePoint, ad esempio i file di elemento di funzionalità e l'output dei progetti di SharePoint non dipendente.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
<Files>  
  <ProjectItemFile.../>  
  <ProjectOutputFile.../>  
</Files>  
```  
  
## <a name="type"></a>Tipo  
 **FileCollectionType**  
  
## <a name="attributes-and-elements"></a>Attributi ed elementi
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.  
  
### <a name="attributes"></a>Attributi  
 Nessuno.  
  
### <a name="child-elements"></a>Elementi figlio
  
|Elemento|Descrizione|  
|-------------|-----------------|  
|[ProjectItemFile](../sharepoint/projectitemfile-element.md)|Facoltativo **ProjectItemFileType** elemento.<br /><br /> Rappresenta un file di SharePoint, ad esempio file di elemento di funzionalità, da includere con l'elemento del progetto quando viene distribuito in SharePoint.|  
|[ProjectOutputFile](../sharepoint/projectoutputfile-element.md)|Facoltativo **ProjectOutputFileType** elemento.<br /><br /> Rappresenta l'output di un progetto da includere con l'elemento del progetto quando viene distribuito in SharePoint.|  
  
### <a name="parent-elements"></a>Elementi padre
  
|Elemento|Descrizione|  
|-------------|-----------------|  
|[ProjectItem](../sharepoint/projectitem-element.md)|Rappresenta un elemento del progetto SharePoint. Questo elemento l'elemento radice obbligatorio del `.spdata` file.|  
  
## <a name="element-information"></a>Informazioni sull'elemento
  
|||  
|-|-|  
|**Spazio dei nomi**|http<nolink>://schemas.microsoft.com/VisualStudio/<br>2010/SharePointTools/SharePointProjectItemModel|  
|**Nome dello schema**|Schema degli elementi di progetto SharePoint|  
|**File di convalida**|ProjectItemModelSchema.xsd|  
|**Può essere vuoto**|No|  
  
## <a name="see-also"></a>Vedere anche
 [Riferimento dello schema elementi di progetto SharePoint](../sharepoint/sharepoint-project-item-schema-reference.md)  
