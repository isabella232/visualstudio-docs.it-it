---
title: ExtensionDataItem (elemento) | Documenti Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ExtensionDataItem element
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 48c29cb41c80d75c6f873171b7e9c758a2513612
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/01/2018
ms.locfileid: "34691937"
---
# <a name="extensiondataitem-element"></a>Elemento ExtensionDataItem
  Un elemento di dati personalizzato che viene associato all'elemento di progetto SharePoint, nel formato di chiave/valore. La chiave e valore devono essere stringhe.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
<ExtensionDataItem Key = "Key of the data item"  
    Value = "Value of the data item" />  
```  
  
## <a name="attributes-and-elements"></a>Attributi ed elementi  
 Le sezioni seguenti descrivono gli attributi, gli elementi figlio e gli elementi padre.  
  
### <a name="attributes"></a>Attributi  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|**Key**|Richiesto **xs: string** attributo.<br /><br /> La chiave utilizzata per archiviare e recuperare l'elemento di dati.|  
|**Valore**|Richiesto **xs: String** attributo.<br /><br /> Il valore dell'elemento di dati.|  
  
### <a name="child-elements"></a>Elementi figlio  
 Nessuno.  
  
### <a name="parent-elements"></a>Elementi padre  
  
|Elemento|Descrizione|  
|-------------|-----------------|  
|[ExtensionData](../sharepoint/extensiondata-element.md)|Rappresenta una raccolta di elementi di dati personalizzati associati all'elemento di progetto SharePoint.|  
  
## <a name="remarks"></a>Note  
 Quando si associano dati personalizzati a un elemento di progetto SharePoint tramite il <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> proprietà di un <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem> dell'oggetto, Visual Studio salva i dati in un nuovo **ExtensionDataItem** elemento il `.spdata` file per il elemento di progetto. Per ulteriori informazioni, vedere [salvataggio dei dati nelle estensioni del sistema del progetto SharePoint](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md).  
  
## <a name="element-information"></a>Informazioni sull'elemento  
  
|||  
|-|-|  
|**Spazio dei nomi**|HTTP<nolink>: //schemas.microsoft.com/VisualStudio/<br>2010/SharePointTools/SharePointProjectItemModel| 
|**Nome dello schema**|Schema di elemento di progetto SharePoint|  
|**File di convalida**|ProjectItemModelSchema.xsd|  
|**Può essere vuoto**|No|  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento allo schema degli elementi di progetto SharePoint](../sharepoint/sharepoint-project-item-schema-reference.md)  
  
  