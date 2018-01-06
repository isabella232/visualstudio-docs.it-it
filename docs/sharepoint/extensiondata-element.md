---
title: ExtensionData (elemento) | Documenti Microsoft
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords: ExtensionData element
ms.assetid: caf6843b-dcf5-4688-a9eb-a424aae1beab
caps.latest.revision: "11"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: c678e75de7c05563d064b873af9d913db602082a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="extensiondata-element"></a>Elemento ExtensionData
  Rappresenta una raccolta di elementi di dati personalizzati associati all'elemento di progetto SharePoint.  
  
## <a name="syntax"></a>Sintassi  
  
```  
<ExtensionData>  
  <ExtensionDataItem.../>  
</ExtensionData>  
```  
  
## <a name="attributes-and-elements"></a>Attributi ed elementi  
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.  
  
### <a name="attributes"></a>Attributi  
 Nessuno.  
  
### <a name="child-elements"></a>Elementi figlio  
  
|Elemento|Descrizione|  
|-------------|-----------------|  
|[ExtensionDataItem](../sharepoint/extensiondataitem-element.md)|Elemento facoltativo.<br /><br /> Rappresenta un elemento di dati personalizzato associato all'elemento di progetto SharePoint, nel formato di chiave/valore. La chiave e valore devono essere stringhe.|  
  
### <a name="parent-elements"></a>Elementi padre  
  
|Elemento|Descrizione|  
|-------------|-----------------|  
|[ProjectItem](../sharepoint/projectitem-element.md)|Rappresenta un elemento di progetto SharePoint. Questo è l'elemento radice obbligatorio del file con estensione spdata.|  
  
## <a name="remarks"></a>Note  
 Quando si associano dati personalizzati a un elemento di progetto SharePoint tramite il <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> proprietà di un <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem> dell'oggetto, Visual Studio salva i dati per il **ExtensionData** elemento nel file con estensione spdata per l'elemento del progetto. Per ulteriori informazioni, vedere [salvataggio dei dati nelle estensioni del sistema del progetto SharePoint](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md).  
  
## <a name="element-information"></a>Informazioni sull'elemento  
  
|||  
|-|-|  
|**Spazio dei nomi**|http://schemas.microsoft.com/VisualStudio/2010/SharePointTools/SharePointProjectItemModel|  
|**Nome dello schema**|Schema di elemento di progetto SharePoint|  
|**File di convalida**|ProjectItemModelSchema.xsd|  
|**Può essere vuoto**|No|  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento allo schema degli elementi di progetto SharePoint](../sharepoint/sharepoint-project-item-schema-reference.md)  
  
  