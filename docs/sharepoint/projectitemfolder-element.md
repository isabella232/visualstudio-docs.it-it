---
title: ProjectItemFolder (elemento) | Documenti Microsoft
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
helpviewer_keywords: ProjectItemFolder element
ms.assetid: 15b386dd-f523-4425-9fcc-517325681358
caps.latest.revision: "12"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: c6b5c895f36f3e0b040ce1e3db7cb87cd52e5b9b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="projectitemfolder-element"></a>Elemento ProjectItemFolder
  Rappresenta una cartella mappata.  
  
## <a name="syntax"></a>Sintassi  
  
```  
<ProjectItemFolder Target = "Path of SharePoint folder the mapped folder corresponds to"  
    Type = "Type of deployment for the mapped folder" />  
```  
  
## <a name="type"></a>Tipo  
 **ProjectItemFolderType**  
  
## <a name="attributes-and-elements"></a>Attributi ed elementi  
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.  
  
### <a name="attributes"></a>Attributi  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|**Destinazione**|Richiesto **xs: String** attributo.<br /><br /> Il percorso della cartella di installazione di SharePoint il mapping della cartella corrispondente, rispetto alla cartella radice di distribuzione. Cartella radice di distribuzione è determinata dal tipo di distribuzione specificato per il **tipo** attributo.<br /><br /> Per ulteriori informazioni, vedere le descrizioni per il **percorso distribuzione** e **radice distribuzione** gli elementi nel progetto di proprietà di SharePoint [lo sviluppo di soluzioni SharePoint](../sharepoint/developing-sharepoint-solutions.md).|  
|**Type**|Richiesto **xs: String** attributo.<br /><br /> Il tipo di distribuzione per la cartella mappata. Per ulteriori informazioni sui possibili valori, vedere la descrizione per il **tipo di distribuzione** proprietà degli elementi di progetto SharePoint in [lo sviluppo di soluzioni SharePoint](../sharepoint/developing-sharepoint-solutions.md).|  
  
### <a name="child-elements"></a>Elementi figlio  
 Nessuno.  
  
### <a name="parent-elements"></a>Elementi padre  
  
|Elemento|Descrizione|  
|-------------|-----------------|  
|[ProjectItem](../sharepoint/projectitem-element.md)|Rappresenta un elemento di progetto SharePoint. Questo è l'elemento radice obbligatorio del file con estensione spdata.|  
  
## <a name="remarks"></a>Note  
 Per ulteriori informazioni sui mapping di cartelle, vedere [procedura: aggiungere e rimuovere cartelle mappata](../sharepoint/how-to-add-and-remove-mapped-folders.md).  
  
## <a name="element-information"></a>Informazioni sull'elemento  
  
|||  
|-|-|  
|**Spazio dei nomi**|http://schemas.microsoft.com/VisualStudio/2010/SharePointTools/SharePointProjectItemModel|  
|**Nome dello schema**|Schema di elemento di progetto SharePoint|  
|**File di convalida**|ProjectItemModelSchema.xsd|  
|**Può essere vuoto**|No|  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento allo Schema elemento di progetto SharePoint](../sharepoint/sharepoint-project-item-schema-reference.md)   
 [Procedura: Aggiungere e rimuovere cartelle mappate](../sharepoint/how-to-add-and-remove-mapped-folders.md)  
  
  