---
title: Elemento ProjectOutputFile | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ProjectOutputFile element
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 2673b22bf502f019f0a10361c9d0cef9d5ac1b8c
ms.sourcegitcommit: 3d37c2460584f6c61769be70ef29c1a67397cf14
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/21/2019
ms.locfileid: "58322532"
---
# <a name="projectoutputfile-element"></a>ProjectOutputFile (elemento)
  Rappresenta l'output di un progetto separato da includere con l'elemento del progetto quando viene distribuito in SharePoint.

## <a name="syntax"></a>Sintassi

```xml
<ProjectOutputFile ProjectId = "GUID of the project"
    ProjectPath = "Relative path of the project"
    Target = "Deployment path of the project output"
    Type = "Type of deployment for the project output" />
```

## <a name="type"></a>Tipo
 **ProjectOutputFileType**

## <a name="attributes-and-elements"></a>Attributi ed elementi
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.

### <a name="attributes"></a>Attributi

|Attributo|Descrizione|
|---------------|-----------------|
|**ProjectId**|Obbligatorio **xs: String** attributo.<br /><br /> Il GUID del progetto dipendente che include l'output a cui si desidera includere. Ciò corrisponde alla **ProjectGuid** elemento nel file di progetto dipendente.|
|**ProjectPath**|Obbligatorio **xs: String** attributo.<br /><br /> Il percorso relativo, incluso il nome di file di progetto, del progetto dipendente che include l'output da includere. Questo percorso è relativo alla cartella radice del progetto SharePoint che contiene l'elemento di progetto SharePoint.|
|**Destinazione**|Facoltativo **xs: String** attributo.<br /><br /> Il percorso in cui l'output del progetto dipendente verrà distribuito nel server SharePoint, relativo alla cartella radice di distribuzione. Cartella radice di distribuzione è determinata dal tipo di distribuzione specificato per il **tipo** attributo.<br /><br /> Per altre informazioni, vedere le descrizioni per le **percorso di distribuzione** e **Deployment Root** le proprietà di SharePoint elementi nel progetto [SharePoint sviluppare soluzioni](../sharepoint/developing-sharepoint-solutions.md).|
|**Type**|Obbligatorio **xs: String** attributo.<br /><br /> Il tipo di distribuzione da usare per l'output del progetto dipendente. Per altre informazioni sui possibili valori, vedere la descrizione per il **tipo di distribuzione** proprietà di elementi di progetto SharePoint in [soluzioni SharePoint sviluppare](../sharepoint/developing-sharepoint-solutions.md).|

### <a name="child-elements"></a>Elementi figlio
 Nessuno.

### <a name="parent-elements"></a>Elementi padre

|Elemento|Descrizione|
|-------------|-----------------|
|[File](../sharepoint/files-element.md)|Specifica i file da includere con l'elemento del progetto SharePoint quando viene distribuito in SharePoint.|

## <a name="remarks"></a>Note
 Usare la **ProjectOutputFile** elemento da includere nella distribuzione dell'elemento del progetto SharePoint, l'output di un progetto. È possibile specificare un altro progetto o il progetto stesso che contiene l'elemento del progetto. Per altre informazioni, vedere [fornire le informazioni di creazione di pacchetti e distribuzione negli elementi di progetto](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md).

## <a name="element-information"></a>Informazioni sull'elemento

|||
|-|-|
|**Spazio dei nomi**|http:\/\/schemas.microsoft.com/VisualStudio/<br>2010/SharePointTools/SharePointProjectItemModel|
|**Nome dello schema**|Schema degli elementi di progetto SharePoint|
|**File di convalida**|ProjectItemModelSchema.xsd|
|**Può essere vuoto**|No|

## <a name="see-also"></a>Vedere anche
- [Riferimento dello schema elementi di progetto SharePoint](../sharepoint/sharepoint-project-item-schema-reference.md)
- [Fornire le informazioni di creazione di pacchetti e distribuzione negli elementi di progetto](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)
- [Sviluppare soluzioni SharePoint](../sharepoint/developing-sharepoint-solutions.md)
