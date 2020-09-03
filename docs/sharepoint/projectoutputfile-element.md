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
ms.openlocfilehash: 12f399b7a09c18c77482475575ca387a11955762
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "85542389"
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

## <a name="type"></a>Type
 **ProjectOutputFileType**

## <a name="attributes-and-elements"></a>Attributi ed elementi
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.

### <a name="attributes"></a>Attributes

|Attributo|Descrizione|
|---------------|-----------------|
|**ProjectId**|Attributo **xs: String** obbligatorio.<br /><br /> GUID del progetto dipendente con l'output che si desidera includere. Corrisponde all'elemento **ProjectGuid** nel file di progetto dipendente.|
|**ProjectPath**|Attributo **xs: String** obbligatorio.<br /><br /> Percorso relativo, incluso il nome del file di progetto, del progetto dipendente con l'output che si desidera includere. Questo percorso è relativo alla cartella radice del progetto SharePoint che contiene l'elemento del progetto SharePoint.|
|**Destinazione**|Attributo **xs: String** facoltativo.<br /><br /> Percorso in cui deve essere distribuito l'output del progetto dipendente nel server SharePoint rispetto alla cartella radice di distribuzione. La cartella radice di distribuzione è determinata dal tipo di distribuzione specificato dall'attributo **Type** .<br /><br /> Per ulteriori informazioni, vedere le descrizioni del **percorso di distribuzione** e delle proprietà **radice di distribuzione** degli elementi del progetto SharePoint in [sviluppare soluzioni SharePoint](../sharepoint/developing-sharepoint-solutions.md).|
|**Tipo**|Attributo **xs: String** obbligatorio.<br /><br /> Tipo di distribuzione da utilizzare per l'output del progetto dipendente. Per ulteriori informazioni sui valori possibili, vedere la descrizione della proprietà **tipo di distribuzione** degli elementi del progetto SharePoint in [sviluppare soluzioni SharePoint](../sharepoint/developing-sharepoint-solutions.md).|

### <a name="child-elements"></a>Elementi figlio
 Nessuno.

### <a name="parent-elements"></a>Elementi padre

|Elemento|Descrizione|
|-------------|-----------------|
|[File](../sharepoint/files-element.md)|Specifica i file da includere con l'elemento del progetto SharePoint quando viene distribuito in SharePoint.|

## <a name="remarks"></a>Osservazioni
 Utilizzare l'elemento **ProjectOutputFile** per includere l'output di un progetto nella distribuzione dell'elemento del progetto SharePoint. È possibile specificare un progetto diverso o lo stesso progetto che contiene l'elemento del progetto. Per altre informazioni, vedere [fornire informazioni sulla creazione di pacchetti e sulla distribuzione negli elementi di progetto](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md).

## <a name="element-information"></a>Informazioni sull'elemento

|Proprietà|Valore|
|-|-|
|**Namespace**|http: \/ \/ schemas.Microsoft.com/VisualStudio/<br>2010/SharePointTools/SharePointProjectItemModel|
|**Nome schema**|Schema dell'elemento del progetto SharePoint|
|**File di convalida**|ProjectItemModelSchema. xsd|
|**Può essere vuoto**|No|

## <a name="see-also"></a>Vedere anche
- [Riferimento allo schema degli elementi di progetto SharePoint](../sharepoint/sharepoint-project-item-schema-reference.md)
- [Fornire informazioni sulla creazione di pacchetti e sulla distribuzione negli elementi di progetto](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)
- [Sviluppare soluzioni SharePoint](../sharepoint/developing-sharepoint-solutions.md)
