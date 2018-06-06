---
title: Elemento file | Documenti Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Files element
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 330c408aa0e283eb282b93f77726ccc5d9547795
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/05/2018
ms.locfileid: "34766906"
---
# <a name="files-element"></a>Files (elemento)
  Specifica i file da distribuire con l'elemento del progetto SharePoint, ad esempio i file di elemento di funzionalità e l'output dei progetti SharePoint dipendenti.  
  
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
|[ProjectItemFile](../sharepoint/projectitemfile-element.md)|Parametro facoltativo **ProjectItemFileType** elemento.<br /><br /> Rappresenta un file di SharePoint, ad esempio file di elemento di funzionalità, per includere l'elemento di progetto quando viene distribuito in SharePoint.|  
|[ProjectOutputFile](../sharepoint/projectoutputfile-element.md)|Parametro facoltativo **ProjectOutputFileType** elemento.<br /><br /> Rappresenta l'output di un progetto da includere nell'elemento di progetto quando viene distribuito in SharePoint.|  
  
### <a name="parent-elements"></a>Elementi padre
  
|Elemento|Descrizione|  
|-------------|-----------------|  
|[ProjectItem](../sharepoint/projectitem-element.md)|Rappresenta un elemento di progetto SharePoint. Questo elemento di elemento radice obbligatorio del `.spdata` file.|  
  
## <a name="element-information"></a>Informazioni sull'elemento
  
|||  
|-|-|  
|**Spazio dei nomi**|HTTP<nolink>: //schemas.microsoft.com/VisualStudio/<br>2010/SharePointTools/SharePointProjectItemModel|  
|**Nome dello schema**|Schema di elemento di progetto SharePoint|  
|**File di convalida**|ProjectItemModelSchema.xsd|  
|**Può essere vuoto**|No|  
  
## <a name="see-also"></a>Vedere anche
 [Riferimento allo schema degli elementi di progetto SharePoint](../sharepoint/sharepoint-project-item-schema-reference.md)  
  
  
