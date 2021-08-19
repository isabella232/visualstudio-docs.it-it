---
title: Elemento ProjectItemFolder | Microsoft Docs
description: Ottenere informazioni di riferimento sull'elemento ProjectItemFolder, che rappresenta una cartella mappata nel riferimento XML Schema SharePoint elemento di progetto.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ProjectItemFolder element
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: 3873a4cbf50d216f3574c2ef8ce90255d3eb5d7b
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122084129"
---
# <a name="projectitemfolder-element"></a>ProjectItemFolder (elemento)
  Rappresenta una cartella mappata.

## <a name="syntax"></a>Sintassi

```xml
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
|**Destinazione**|Obbligatorio **xs: attributo** stringa.<br /><br /> Percorso della cartella nel SharePoint a cui corrisponde la cartella mappata, relativa alla cartella radice della distribuzione. La cartella radice della distribuzione è determinata dal tipo di distribuzione specificato **dall'attributo Type.**<br /><br /> Per altre informazioni, vedere le  descrizioni  per le proprietà Percorso di distribuzione e Radice di distribuzione SharePoint di progetto in Sviluppare [SharePoint soluzioni](../sharepoint/developing-sharepoint-solutions.md).|
|**Tipo**|Attributo **xs:string** obbligatorio.<br /><br /> Tipo di distribuzione per la cartella mappata. Per altre informazioni sui valori possibili, vedere la descrizione per la proprietà **Tipo** di distribuzione SharePoint di progetto in Sviluppare [SharePoint soluzioni](../sharepoint/developing-sharepoint-solutions.md).|

### <a name="child-elements"></a>Elementi figlio
 Nessuno.

### <a name="parent-elements"></a>Elementi padre

|Elemento|Descrizione|
|-------------|-----------------|
|[ProjectItem](../sharepoint/projectitem-element.md)|Rappresenta un SharePoint di progetto. Questo elemento è l'elemento radice obbligatorio del file *spdata.*|

## <a name="remarks"></a>Commenti
 Per altre informazioni sulle cartelle mappate, vedere [Procedura: aggiungere e rimuovere cartelle mappate](../sharepoint/how-to-add-and-remove-mapped-folders.md).

## <a name="element-information"></a>Informazioni sull'elemento

|Proprietà|Valore|
|-|-|
|**Namespace**|http: \/ \/ schemas.microsoft.com/VisualStudio/2010/<br>SharePointTools/SharePointProjectItemModel|
|**Nome schema**|SharePoint Project schema dell'elemento|
|**File di convalida**|ProjectItemModelSchema.xsd|
|**Può essere vuoto**|No|

## <a name="see-also"></a>Vedere anche
- [SharePoint riferimento allo schema dell'elemento di progetto](../sharepoint/sharepoint-project-item-schema-reference.md)
- [Procedura: aggiungere e rimuovere cartelle mappate](../sharepoint/how-to-add-and-remove-mapped-folders.md)
