---
title: Riferimento allo schema degli elementi di progetto SharePoint | Microsoft Docs
description: Vedere una panoramica dell'elemento di progetto SharePoint XML Schema riferimento (ProjectItemModelSchema. xsd), che viene usato per convalidare il contenuto dei file con estensione spdata.
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
ms.workload:
- office
ms.openlocfilehash: 466bc68ca002914b64698d7cd87f98ff276bfc0e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99892281"
---
# <a name="sharepoint-project-item-schema-reference"></a>Riferimento allo schema degli elementi di progetto SharePoint
  In Visual Studio viene utilizzato lo schema degli elementi di progetto SharePoint per convalidare il contenuto dei file con *estensione spdata* . Un file con *estensione spdata* specifica il contenuto e il comportamento di un elemento del progetto SharePoint. Per ulteriori informazioni sul contenuto degli elementi del progetto SharePoint, vedere [creare modelli di elementi e modelli di progetto per gli elementi del progetto SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).

 Lo schema dell'elemento del progetto SharePoint è denominato ProjectItemModelSchema. xsd e viene installato per impostazione predefinita in% Program Files (x86)% \ Microsoft Visual Studio 11.0 \ Xml\Schemas.

 L'elemento radice è l'elemento [ProjectItem](../sharepoint/projectitem-element.md) . Nella tabella seguente vengono descritti tutti gli elementi definiti dallo schema.

|Elemento|Descrizione|
|-------------|-----------------|
|[ExtensionData](../sharepoint/extensiondata-element.md)|Rappresenta una raccolta di elementi di dati personalizzati associati all'elemento del progetto SharePoint.|
|[ExtensionDataItem](../sharepoint/extensiondataitem-element.md)|Rappresenta un elemento di dati personalizzato associato all'elemento del progetto SharePoint, in formato chiave/valore. Sia la chiave che il valore devono essere stringhe.|
|[FeatureProperties](../sharepoint/featureproperties-element.md)|Rappresenta una raccolta di valori di proprietà inclusi in una funzionalità quando viene distribuita in SharePoint. Dopo la distribuzione di una funzionalità, è possibile accedere ai valori delle proprietà nel codice.|
|[FeatureProperty](../sharepoint/featureproperty-element.md)|Rappresenta una proprietà personalizzata inclusa con una funzionalità quando viene distribuita in SharePoint. Dopo la distribuzione di una funzionalità, è possibile accedere alla proprietà nel codice.|
|[File](../sharepoint/files-element.md)|Specifica i file da distribuire con l'elemento del progetto SharePoint, ad esempio un file di elemento della funzionalità o l'output di un progetto.|
|[ProjectItem](../sharepoint/projectitem-element.md)|Rappresenta un elemento del progetto SharePoint.|
|[ProjectItemFile](../sharepoint/projectitemfile-element.md)|Rappresenta un file di SharePoint, ad esempio un file degli elementi della funzionalità, da includere con l'elemento del progetto quando viene distribuito in SharePoint.|
|[ProjectItemFolder](../sharepoint/projectitemfolder-element.md)|Rappresenta una cartella mappata.|
|[ProjectOutputFile](../sharepoint/projectoutputfile-element.md)|Rappresenta l'output di un progetto da includere con l'elemento del progetto quando viene distribuito in SharePoint.|
|[SafeControl](../sharepoint/safecontrol-element.md)|Rappresenta una Web part o un controllo ASPX designato come sicuro per qualsiasi utente per accedere a qualsiasi pagina ASPX nel sito di SharePoint.|
|[SafeControls](../sharepoint/safecontrols-element.md)|Rappresenta una raccolta di controlli ASPX e Web part designati come sicuri per qualsiasi utente per accedere a qualsiasi pagina ASPX nel sito di SharePoint.|

## <a name="see-also"></a>Vedi anche
- [Creare modelli di elementi e modelli di progetto per gli elementi di progetto SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)
