---
title: ProjectItemFolder (elemento) | Documenti Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ProjectItemFolder element
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 3509588baa700cc6d280c01c2456b4736b8eb58d
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/01/2018
ms.locfileid: "34691872"
---
# <a name="projectitemfolder-element"></a>Elemento ProjectItemFolder
  Rappresenta una cartella mappata.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
<ProjectItemFolder Target = "Path of SharePoint folder the mapped folder corresponds to"  
    Type = "Type of deployment for the mapped folder" />  
```  
  
## <a name="type"></a>Tipo  
 **ProjectItemFolderType**  
  
## <a name="attributes-and-elements"></a>Attributi ed elementi  
 Le sezioni seguenti descrivono gli attributi, gli elementi figlio e gli elementi padre.  
  
### <a name="attributes"></a>Attributi  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|**Destinazione**|Richiesto **xs: string** attributo.<br /><br /> Il percorso della cartella di installazione di SharePoint il mapping della cartella corrispondente, rispetto alla cartella radice di distribuzione. Cartella radice di distribuzione è determinata dal tipo di distribuzione specificato per il **tipo** attributo.<br /><br /> Per ulteriori informazioni, vedere le descrizioni per il **percorso distribuzione** e **radice distribuzione** gli elementi nel progetto di proprietà di SharePoint [lo sviluppo di soluzioni SharePoint](../sharepoint/developing-sharepoint-solutions.md).|  
|**Type**|Richiesto **xs: String** attributo.<br /><br /> Il tipo di distribuzione per la cartella mappata. Per ulteriori informazioni sui possibili valori, vedere la descrizione per il **tipo di distribuzione** proprietà degli elementi di progetto SharePoint in [lo sviluppo di soluzioni SharePoint](../sharepoint/developing-sharepoint-solutions.md).|  
  
### <a name="child-elements"></a>Elementi figlio  
 Nessuno.  
  
### <a name="parent-elements"></a>Elementi padre  
  
|Elemento|Descrizione|  
|-------------|-----------------|  
|[ProjectItem](../sharepoint/projectitem-element.md)|Rappresenta un elemento di progetto SharePoint. Questo elemento è l'elemento radice obbligatorio del `.spdata` file.|  
  
## <a name="remarks"></a>Note  
 Per ulteriori informazioni sui mapping di cartelle, vedere [procedura: aggiungere e rimuovere cartelle mappata](../sharepoint/how-to-add-and-remove-mapped-folders.md).  
  
## <a name="element-information"></a>Informazioni sull'elemento  
  
|||  
|-|-|  
|**Spazio dei nomi**|HTTP<nolink>: //schemas.microsoft.com/VisualStudio/2010/<br>SharePointTools/SharePointProjectItemModel|  
|**Nome dello schema**|Schema di elemento di progetto SharePoint|  
|**File di convalida**|ProjectItemModelSchema.xsd|  
|**Può essere vuoto**|No|  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento allo Schema elemento di progetto SharePoint](../sharepoint/sharepoint-project-item-schema-reference.md)   
 [Procedura: Aggiungere e rimuovere cartelle mappate](../sharepoint/how-to-add-and-remove-mapped-folders.md)  
  
  