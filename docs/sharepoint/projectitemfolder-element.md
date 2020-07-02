---
title: Elemento ProjectItemFolder | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ProjectItemFolder element
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 38f8f70cc6480554441809e33c4083735600fbbb
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/30/2020
ms.locfileid: "85539815"
---
# <a name="projectitemfolder-element"></a>ProjectItemFolder (elemento)
  Rappresenta una cartella mappata.

## <a name="syntax"></a>Sintassi

```xml
<ProjectItemFolder Target = "Path of SharePoint folder the mapped folder corresponds to"
    Type = "Type of deployment for the mapped folder" />
```

## <a name="type"></a>Type
 **ProjectItemFolderType**

## <a name="attributes-and-elements"></a>Attributi ed elementi
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.

### <a name="attributes"></a>Attributi

|Attributo|Descrizione|
|---------------|-----------------|
|**Destinazione**|Attributo **xs: String** obbligatorio.<br /><br /> Percorso della cartella nell'installazione di SharePoint a cui corrisponde la cartella mappata, relativa alla cartella radice della distribuzione. La cartella radice di distribuzione è determinata dal tipo di distribuzione specificato dall'attributo **Type** .<br /><br /> Per ulteriori informazioni, vedere le descrizioni del **percorso di distribuzione** e delle proprietà **radice di distribuzione** degli elementi del progetto SharePoint in [sviluppare soluzioni SharePoint](../sharepoint/developing-sharepoint-solutions.md).|
|**Tipo**|Attributo **xs: String** obbligatorio.<br /><br /> Tipo di distribuzione per la cartella mappata. Per ulteriori informazioni sui valori possibili, vedere la descrizione della proprietà **tipo di distribuzione** degli elementi del progetto SharePoint in [sviluppare soluzioni SharePoint](../sharepoint/developing-sharepoint-solutions.md).|

### <a name="child-elements"></a>Elementi figlio
 No.

### <a name="parent-elements"></a>Elementi padre

|Elemento|Descrizione|
|-------------|-----------------|
|[ProjectItem](../sharepoint/projectitem-element.md)|Rappresenta un elemento del progetto SharePoint. Questo elemento è l'elemento radice obbligatorio del file con *estensione spdata* .|

## <a name="remarks"></a>Osservazioni
 Per altre informazioni sulle cartelle mappate, vedere [procedura: aggiungere e rimuovere cartelle mappate](../sharepoint/how-to-add-and-remove-mapped-folders.md).

## <a name="element-information"></a>Informazioni sull'elemento

|Proprietà|Valore|
|-|-|
|**Namespace**|http: \/ \/ schemas.Microsoft.com/VisualStudio/2010/<br>SharePointTools/SharePointProjectItemModel|
|**Nome schema**|Schema dell'elemento del progetto SharePoint|
|**File di convalida**|ProjectItemModelSchema. xsd|
|**Può essere vuoto**|No|

## <a name="see-also"></a>Vedere anche
- [Riferimento allo schema degli elementi di progetto SharePoint](../sharepoint/sharepoint-project-item-schema-reference.md)
- [Procedura: aggiungere e rimuovere cartelle mappate](../sharepoint/how-to-add-and-remove-mapped-folders.md)
