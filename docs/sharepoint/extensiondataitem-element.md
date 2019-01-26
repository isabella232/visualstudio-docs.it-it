---
title: Elemento ExtensionDataItem | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ExtensionDataItem element
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 5f5a547194de87a7fe151c3530720a078ca01438
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/24/2019
ms.locfileid: "54873080"
---
# <a name="extensiondataitem-element"></a>ExtensionDataItem (elemento)
  Un elemento di dati personalizzate che è associato l'elemento del progetto SharePoint, nel formato di chiave/valore. Sia la chiave e valore devono essere stringhe.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
<ExtensionDataItem Key = "Key of the data item"  
    Value = "Value of the data item" />  
```  
  
## <a name="attributes-and-elements"></a>Attributi ed elementi
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.  
  
### <a name="attributes"></a>Attributi  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|**Key**|Obbligatorio **xs: string** attributo.<br /><br /> La chiave utilizzata per archiviare e recuperare l'elemento di dati.|  
|**Valore**|Obbligatorio **xs: String** attributo.<br /><br /> Il valore dell'elemento di dati.|  
  
### <a name="child-elements"></a>Elementi figlio
 Nessuno.  
  
### <a name="parent-elements"></a>Elementi padre
  
|Elemento|Descrizione|  
|-------------|-----------------|  
|[ExtensionData](../sharepoint/extensiondata-element.md)|Rappresenta una raccolta di elementi di dati personalizzati associati con l'elemento del progetto SharePoint.|  
  
## <a name="remarks"></a>Note  
 Quando si associano dati personalizzati con un elemento del progetto SharePoint con il <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> proprietà di un <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem> Visual Studio salva i dati in un nuovo oggetto **ExtensionDataItem** elemento il `.spdata` file per il elemento del progetto. Per altre informazioni, vedere [salvare i dati nelle estensioni del sistema del progetto SharePoint](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md).  
  
## <a name="element-information"></a>Informazioni sull'elemento
  
|||  
|-|-|  
|**Spazio dei nomi**|http<nolink>://schemas.microsoft.com/VisualStudio/<br>2010/SharePointTools/SharePointProjectItemModel| 
|**Nome dello schema**|Schema degli elementi di progetto SharePoint|  
|**File di convalida**|ProjectItemModelSchema.xsd|  
|**Può essere vuoto**|No|  
  
## <a name="see-also"></a>Vedere anche
 [Riferimento dello schema elementi di progetto SharePoint](../sharepoint/sharepoint-project-item-schema-reference.md)  
