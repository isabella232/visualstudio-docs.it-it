---
title: SafeControls (elemento) | Documenti Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SafeControls element
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 99235ad0852ab211a93fa2241d0d86ccb2fd8b51
ms.sourcegitcommit: 1466ac0f49ebf7448ea4507ae3f79acb25d51d3e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/22/2018
---
# <a name="safecontrols-element"></a>Elemento SafeControls
  Raccolta di controlli ASPX e dalle Web part sono designate come protette per tutti gli utenti di accedere in qualsiasi pagina ASPX nel sito di SharePoint.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
<SafeControls>  
  <SafeControl.../>  
</SafeControls>  
```  
  
## <a name="attributes-and-elements"></a>Attributi ed elementi  
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.  
  
### <a name="attributes"></a>Attributi  
 Nessuno.  
  
### <a name="child-elements"></a>Elementi figlio  
  
|Elemento|Descrizione|  
|-------------|-----------------|  
|[SafeControl](../sharepoint/safecontrol-element.md)|Elemento facoltativo.<br /><br /> Rappresenta un controllo ASPX o una Web Part che è designato come protetto per qualsiasi utente di accedere in qualsiasi pagina ASPX nel sito di SharePoint.|  
  
### <a name="parent-elements"></a>Elementi padre  
  
|Elemento|Descrizione|  
|-------------|-----------------|  
|[ProjectItem](../sharepoint/projectitem-element.md)|Rappresenta un elemento di progetto SharePoint. Questo elemento di elemento radice obbligatorio del `.spdata` file.|  
  
## <a name="remarks"></a>Note  
 Per ulteriori informazioni sui controlli sicuri, vedere [che fornisce informazioni sui pacchetti e distribuzione negli elementi di progetto](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md).  
  
## <a name="element-information"></a>Informazioni sull'elemento  
  
|||  
|-|-|  
|**Spazio dei nomi**|http://schemas.microsoft.com/VisualStudio/2010/SharePointTools/SharePointProjectItemModel|  
|**Nome dello schema**|Schema di elemento di progetto SharePoint|  
|**File di convalida**|ProjectItemModelSchema.xsd|  
|**Può essere vuoto**|No|  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento allo Schema elemento di progetto SharePoint](../sharepoint/sharepoint-project-item-schema-reference.md)   
 [Specifica delle informazioni sui pacchetti e sulla distribuzione negli elementi di progetto](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)  
  
  