---
title: SharePoint Project riferimento allo schema dell'elemento | Microsoft Docs
description: Vedere una panoramica del riferimento SharePoint XML Schema dell'elemento di progetto (ProjectItemModelSchema.xsd), usato per convalidare il contenuto dei file con estensione spdata.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: 5dbeefe02cf917ac03aeb558acdb5c609543952e
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122115512"
---
# <a name="sharepoint-project-item-schema-reference"></a>SharePoint riferimento allo schema dell'elemento di progetto
  Visual Studio lo schema SharePoint elemento di progetto per convalidare il contenuto dei *file con estensione spdata.* Un file *con estensione spdata* specifica il contenuto e il comportamento di un SharePoint di progetto. Per altre informazioni sul contenuto degli elementi SharePoint progetto, vedere Creare modelli di elemento e modelli di progetto per SharePoint [di progetto](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).

 Lo schema SharePoint elemento di progetto è denominato ProjectItemModelSchema.xsd e viene installato per impostazione predefinita in %Programmi (x86)%\Microsoft Visual Studio 11.0\Xml\Schemas.

 L'elemento radice è [l'elemento ProjectItem.](../sharepoint/projectitem-element.md) Nella tabella seguente vengono descritti tutti gli elementi definiti dallo schema.

|Elemento|Descrizione|
|-------------|-----------------|
|[ExtensionData](../sharepoint/extensiondata-element.md)|Rappresenta una raccolta di elementi di dati personalizzati associati all'SharePoint di progetto.|
|[ExtensionDataItem](../sharepoint/extensiondataitem-element.md)|Rappresenta un elemento di dati personalizzato associato all'SharePoint di progetto, in formato chiave/valore. Sia la chiave che il valore devono essere stringhe.|
|[Proprietà delle funzionalità](../sharepoint/featureproperties-element.md)|Rappresenta una raccolta di valori di proprietà inclusi in una funzionalità quando viene distribuita in SharePoint. Dopo aver distribuito una funzionalità, è possibile accedere ai valori delle proprietà nel codice.|
|[Proprietà FeatureProperty](../sharepoint/featureproperty-element.md)|Rappresenta una proprietà personalizzata inclusa in una funzionalità quando viene distribuita in SharePoint. Dopo aver distribuito una funzionalità, è possibile accedere alla proprietà nel codice.|
|[File](../sharepoint/files-element.md)|Specifica i file da distribuire con l'SharePoint di progetto, ad esempio un file di elemento Feature o l'output di un progetto.|
|[ProjectItem](../sharepoint/projectitem-element.md)|Rappresenta un SharePoint di progetto.|
|[ProjectItemFile](../sharepoint/projectitemfile-element.md)|Rappresenta un SharePoint file, ad esempio il file dell'elemento Feature, da includere con l'elemento di progetto quando viene distribuito in SharePoint.|
|[ProjectItemFolder](../sharepoint/projectitemfolder-element.md)|Rappresenta una cartella mappata.|
|[ProjectOutputFile](../sharepoint/projectoutputfile-element.md)|Rappresenta l'output di un progetto da includere con l'elemento di progetto quando viene distribuito in SharePoint.|
|[SafeControl](../sharepoint/safecontrol-element.md)|Rappresenta un controllo ASPX o una web part designata come sicura per l'accesso di qualsiasi utente in qualsiasi pagina ASPX SharePoint sito.|
|[SafeControls](../sharepoint/safecontrols-element.md)|Rappresenta una raccolta di controlli ASPX e Web part designati come sicuri per l'accesso di qualsiasi utente in qualsiasi pagina ASPX nel SharePoint sito.|

## <a name="see-also"></a>Vedi anche
- [Creare modelli di elemento e modelli di progetto per SharePoint di progetto](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)
