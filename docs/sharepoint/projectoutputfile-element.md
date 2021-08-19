---
title: Elemento ProjectOutputFile | Microsoft Docs
description: Ottenere informazioni di riferimento sull'elemento ProjectOutputFile, che rappresenta l'output di un progetto separato nel riferimento XML Schema dell'elemento SharePoint progetto.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ProjectOutputFile element
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: 9a8ecbe4c9214487f1e5d93462bace0af1d58165
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122130897"
---
# <a name="projectoutputfile-element"></a>ProjectOutputFile (elemento)
  Rappresenta l'output di un progetto separato da includere con l'elemento di progetto quando viene distribuito in SharePoint.

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
|**ProjectId**|Attributo **xs:string** obbligatorio.<br /><br /> GUID del progetto dipendente che contiene l'output da includere. Corrisponde **all'elemento ProjectGuid** nel file di progetto dipendente.|
|**ProjectPath**|Attributo **xs:string** obbligatorio.<br /><br /> Percorso relativo, incluso il nome del file di progetto, del progetto dipendente con l'output da includere. Questo percorso è relativo alla cartella radice del progetto SharePoint che contiene l'elemento SharePoint progetto.|
|**Destinazione**|Attributo **xs:string** facoltativo.<br /><br /> Percorso in cui l'output del progetto dipendente deve essere distribuito nel server SharePoint, relativo alla cartella radice della distribuzione. La cartella radice della distribuzione è determinata dal tipo di distribuzione specificato **dall'attributo Type.**<br /><br /> Per altre informazioni, vedere le  descrizioni  per le proprietà Percorso di distribuzione e Radice di distribuzione SharePoint di progetto in Sviluppare [SharePoint soluzioni](../sharepoint/developing-sharepoint-solutions.md).|
|**Tipo**|Attributo **xs:string** obbligatorio.<br /><br /> Tipo di distribuzione da utilizzare per l'output del progetto dipendente. Per altre informazioni sui valori possibili, vedere la descrizione per la proprietà **Tipo** di distribuzione SharePoint di progetto in Sviluppare [SharePoint soluzioni](../sharepoint/developing-sharepoint-solutions.md).|

### <a name="child-elements"></a>Elementi figlio
 Nessuno.

### <a name="parent-elements"></a>Elementi padre

|Elemento|Descrizione|
|-------------|-----------------|
|[File](../sharepoint/files-element.md)|Specifica i file da includere con l'SharePoint di progetto quando viene distribuito in SharePoint.|

## <a name="remarks"></a>Commenti
 Usare **l'elemento ProjectOutputFile** per includere l'output di un progetto nella distribuzione dell SharePoint di progetto. È possibile specificare un progetto diverso o lo stesso progetto che contiene l'elemento di progetto. Per altre informazioni, vedere Fornire informazioni [sulla creazione di pacchetti e sulla distribuzione negli elementi del progetto.](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)

## <a name="element-information"></a>Informazioni sull'elemento

|Proprietà|Valore|
|-|-|
|**Namespace**|http: \/ \/ schemas.microsoft.com/VisualStudio/<br>2010/SharePointTools/SharePointProjectItemModel|
|**Nome schema**|SharePoint Project schema dell'elemento|
|**File di convalida**|ProjectItemModelSchema.xsd|
|**Può essere vuoto**|No|

## <a name="see-also"></a>Vedere anche
- [SharePoint riferimento allo schema dell'elemento di progetto](../sharepoint/sharepoint-project-item-schema-reference.md)
- [Fornire informazioni sulla creazione di pacchetti e sulla distribuzione negli elementi del progetto](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)
- [Sviluppare soluzioni SharePoint](../sharepoint/developing-sharepoint-solutions.md)
