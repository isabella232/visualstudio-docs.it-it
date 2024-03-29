---
title: Elemento ProjectItemFile | Microsoft Docs
description: Ottenere informazioni di riferimento sull'elemento ProjectItemFile, che rappresenta un file di elemento di progetto nel riferimento XML Schema dell'elemento SharePoint progetto.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ProjectItemFile element
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: 065bb202420549462597ccea7cece0a3c3485c4b
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126710128"
---
# <a name="projectitemfile-element"></a>ProjectItemFile (elemento)
  Rappresenta un SharePoint file, ad esempio il file dell'elemento Feature, da includere con l'elemento di progetto quando viene distribuito in SharePoint.

## <a name="syntax"></a>Sintassi

```xml
<ProjectItemFile Source = "Name of the file"
    Target = "Deployment path of the file"
    Type = "Type of deployment for the file" />
```

## <a name="type"></a>Tipo
 **ProjectItemFileType**

## <a name="attributes-and-elements"></a>Attributi ed elementi
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.

### <a name="attributes"></a>Attributi

|Attributo|Descrizione|
|---------------|-----------------|
|**Origine**|Attributo **xs:string** obbligatorio.<br /><br /> Nome del file da distribuire con l'elemento di progetto.|
|**Destinazione**|Attributo **xs:string** facoltativo.<br /><br /> Percorso in cui il file verrà distribuito in SharePoint, relativo alla cartella radice della distribuzione. La cartella radice della distribuzione è determinata dal tipo di distribuzione specificato **dall'attributo Type.** Se **l'attributo** Target non viene specificato, il file verrà distribuito in una cartella con il nome specificato **nell'attributo Source.**<br /><br /> Per altre informazioni, vedere le  descrizioni  per le proprietà Percorso di distribuzione e Radice distribuzione SharePoint progetto in Sviluppare [SharePoint soluzioni](../sharepoint/developing-sharepoint-solutions.md).|
|**Tipo**|Attributo **xs:string** obbligatorio.<br /><br /> Tipo di distribuzione per il file. Per altre informazioni sui valori possibili, vedere la descrizione per la proprietà **Tipo** di distribuzione SharePoint di progetto in Sviluppare [SharePoint soluzioni](../sharepoint/developing-sharepoint-solutions.md).|

### <a name="child-elements"></a>Elementi figlio
 Nessuno.

### <a name="parent-elements"></a>Elementi padre

|Elemento|Descrizione|
|-------------|-----------------|
|[File](../sharepoint/files-element.md)|Specifica i file da includere con l'SharePoint di progetto quando viene distribuito in SharePoint.|

## <a name="remarks"></a>Commenti
 SharePoint i file a cui si fa in genere riferimento negli elementi **ProjectItemFile** includono i file di elemento Feature (*Elements.xml*), i file di schema per le definizioni di elenco (*Schema.xml*) e i file di definizione della web part per Web part (*webpart*).

## <a name="element-information"></a>Informazioni sull'elemento

|Proprietà|Valore|
|-|-|
|**Namespace**|http: \/ \/ schemas.microsoft.com/VisualStudio/<br>2010/SharePointTools/SharePointProjectItemModel|
|**Nome schema**|SharePoint Project schema dell'elemento|
|**File di convalida**|ProjectItemModelSchema.xsd|
|**Può essere vuoto**|No|

## <a name="see-also"></a>Vedere anche
- [SharePoint riferimento allo schema dell'elemento di progetto](../sharepoint/sharepoint-project-item-schema-reference.md)
