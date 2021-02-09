---
title: Elemento files | Microsoft Docs
description: Consente di visualizzare le informazioni di riferimento sull'elemento files, che è un elemento nello schema dell'elemento del progetto SharePoint.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Files element
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 653e48a2e9b6a68db94fd66660da85f4dec20927
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99876647"
---
# <a name="files-element"></a>Files (elemento)
  Specifica i file da distribuire con l'elemento del progetto SharePoint, ad esempio i file degli elementi delle funzionalità e l'output dei progetti non SharePoint dipendenti.

## <a name="syntax"></a>Sintassi

```xml
<Files>
  <ProjectItemFile.../>
  <ProjectOutputFile.../>
</Files>
```

## <a name="type"></a>Tipo
 **FileCollectionType**

## <a name="attributes-and-elements"></a>Attributi ed elementi
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.

### <a name="attributes"></a>Attributi
 Nessuna.

### <a name="child-elements"></a>Elementi figlio

|Elemento|Descrizione|
|-------------|-----------------|
|[ProjectItemFile](../sharepoint/projectitemfile-element.md)|Elemento **ProjectItemFileType** facoltativo.<br /><br /> Rappresenta un file di SharePoint, ad esempio un file degli elementi della funzionalità, da includere con l'elemento del progetto quando viene distribuito in SharePoint.|
|[ProjectOutputFile](../sharepoint/projectoutputfile-element.md)|Elemento **ProjectOutputFileType** facoltativo.<br /><br /> Rappresenta l'output di un progetto da includere con l'elemento del progetto quando viene distribuito in SharePoint.|

### <a name="parent-elements"></a>Elementi padre

|Elemento|Descrizione|
|-------------|-----------------|
|[ProjectItem](../sharepoint/projectitem-element.md)|Rappresenta un elemento del progetto SharePoint. Questo elemento è l'elemento radice obbligatorio del `.spdata` file.|

## <a name="element-information"></a>Informazioni sull'elemento

|Proprietà|Valore|
|-|-|
|**Namespace**|http: \/ \/ schemas.Microsoft.com/VisualStudio/<br>2010/SharePointTools/SharePointProjectItemModel|
|**Nome schema**|Schema dell'elemento del progetto SharePoint|
|**File di convalida**|ProjectItemModelSchema. xsd|
|**Può essere vuoto**|No|

## <a name="see-also"></a>Vedere anche
- [Riferimento allo schema degli elementi di progetto SharePoint](../sharepoint/sharepoint-project-item-schema-reference.md)
