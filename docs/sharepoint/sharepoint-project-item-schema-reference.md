---
title: Riferimento allo Schema elemento di progetto SharePoint | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- FeatureProperty element
- SafeControls element
- SafeControl element
- .spdata files
- ExtensionData element
- FeatureProperties element
- ProjectOutputFile element
- Files element
- ProjectItemFolder element
- ProjectItemFile element
- ExtensionDataItem element
- ProjectItem element
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: c261115b21d1067b7494d09ad8031b3f4dc5a8c5
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/24/2019
ms.locfileid: "54864917"
---
# <a name="sharepoint-project-item-schema-reference"></a>Riferimento dello schema elementi di progetto SharePoint
  Visual Studio Usa lo schema di elemento di progetto SharePoint per convalidare il contenuto del *spdata* file. Un' *spdata* file specifica il contenuto e il comportamento di un elemento di progetto SharePoint. Per altre informazioni sul contenuto di elementi di progetto SharePoint, vedere [creare elementi di modelli e i modelli di progetto per gli elementi di progetto SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).  
  
 Lo schema di elemento di progetto SharePoint viene denominato ProjectItemModelSchema.xsd e viene installato per impostazione predefinita in % programmi (x86)%\Microsoft Visual Studio 11.0\Xml\Schemas.  
  
 L'elemento radice è il [ProjectItem](../sharepoint/projectitem-element.md) elemento. La tabella seguente descrive tutti gli elementi definiti dallo schema.  
  
|Elemento|Descrizione|  
|-------------|-----------------|  
|[ExtensionData](../sharepoint/extensiondata-element.md)|Rappresenta una raccolta di elementi di dati personalizzati associati con l'elemento del progetto SharePoint.|  
|[ExtensionDataItem](../sharepoint/extensiondataitem-element.md)|Rappresenta un elemento di dati personalizzati associati all'elemento di progetto SharePoint, nel formato di chiave/valore. Sia la chiave e valore devono essere stringhe.|  
|[FeatureProperties](../sharepoint/featureproperties-element.md)|Rappresenta una raccolta di valori di proprietà che sono inclusi in una funzione quando viene distribuito in SharePoint. Dopo aver distribuita una funzionalità, è possibile accedere i valori delle proprietà nel codice.|  
|[FeatureProperty](../sharepoint/featureproperty-element.md)|Rappresenta una proprietà personalizzata che è inclusa in una funzione quando viene distribuito in SharePoint. Dopo aver distribuita una funzionalità, è possibile accedere alla proprietà nel codice.|  
|[File](../sharepoint/files-element.md)|Specifica i file da distribuire con l'elemento di progetto SharePoint, ad esempio un file di elemento di funzionalità o l'output di un progetto.|  
|[ProjectItem](../sharepoint/projectitem-element.md)|Rappresenta un elemento del progetto SharePoint.|  
|[ProjectItemFile](../sharepoint/projectitemfile-element.md)|Rappresenta un file di SharePoint, ad esempio file di elemento di funzionalità, da includere con l'elemento del progetto quando viene distribuito in SharePoint.|  
|[ProjectItemFolder](../sharepoint/projectitemfolder-element.md)|Rappresenta una cartella mappata.|  
|[ProjectOutputFile](../sharepoint/projectoutputfile-element.md)|Rappresenta l'output di un progetto da includere con l'elemento del progetto quando viene distribuito in SharePoint.|  
|[SafeControl](../sharepoint/safecontrol-element.md)|Rappresenta un controllo ASPX o una Web Part che è designato come protetto per tutti gli utenti accedere in qualsiasi pagina ASPX nel sito di SharePoint.|  
|[SafeControls](../sharepoint/safecontrols-element.md)|Rappresenta una raccolta di controlli ASPX e Web part che sono definiti come sicuri per tutti gli utenti accedere in qualsiasi pagina ASPX nel sito di SharePoint.|  
  
## <a name="see-also"></a>Vedere anche
 [Creare modelli di elementi e modelli di progetto per elementi di progetto SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)  
