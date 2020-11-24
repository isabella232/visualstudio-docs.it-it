---
title: Elemento ProjectItemFile | Microsoft Docs
description: Ottenere informazioni di riferimento sull'elemento ProjectItemFile, che rappresenta un file di elemento di progetto nell'elemento del progetto SharePoint XML Schema riferimento.
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 099f20926487b09240219f04d9bce4a79709f6e6
ms.sourcegitcommit: 02f14db142dce68d084dcb0a19ca41a16f5bccff
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/23/2020
ms.locfileid: "95440805"
---
# <a name="projectitemfile-element"></a>ProjectItemFile (elemento)
  Rappresenta un file di SharePoint, ad esempio un file degli elementi della funzionalità, da includere con l'elemento del progetto quando viene distribuito in SharePoint.

## <a name="syntax"></a>Sintassi

```xml
<ProjectItemFile Source = "Name of the file"
    Target = "Deployment path of the file"
    Type = "Type of deployment for the file" />
```

## <a name="type"></a>Type
 **ProjectItemFileType**

## <a name="attributes-and-elements"></a>Attributi ed elementi
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.

### <a name="attributes"></a>Attributes

|Attributo|Descrizione|
|---------------|-----------------|
|**Origine**|Attributo **xs: String** obbligatorio.<br /><br /> Nome del file da distribuire con l'elemento del progetto.|
|**Destinazione**|Attributo **xs: String** facoltativo.<br /><br /> Percorso in cui il file verrà distribuito in SharePoint rispetto alla cartella radice di distribuzione. La cartella radice di distribuzione è determinata dal tipo di distribuzione specificato dall'attributo **Type** . Se l'attributo di **destinazione** non è specificato, il file verrà distribuito in una cartella con il nome specificato nell'attributo di **origine** .<br /><br /> Per ulteriori informazioni, vedere le descrizioni del **percorso di distribuzione** e delle proprietà **radice di distribuzione** degli elementi del progetto SharePoint in [sviluppare soluzioni SharePoint](../sharepoint/developing-sharepoint-solutions.md).|
|**Tipo**|Attributo **xs: String** obbligatorio.<br /><br /> Tipo di distribuzione per il file. Per ulteriori informazioni sui valori possibili, vedere la descrizione della proprietà **tipo di distribuzione** degli elementi del progetto SharePoint in [sviluppare soluzioni SharePoint](../sharepoint/developing-sharepoint-solutions.md).|

### <a name="child-elements"></a>Elementi figlio
 No.

### <a name="parent-elements"></a>Elementi padre

|Elemento|Descrizione|
|-------------|-----------------|
|[File](../sharepoint/files-element.md)|Specifica i file da includere con l'elemento del progetto SharePoint quando viene distribuito in SharePoint.|

## <a name="remarks"></a>Commenti
 I file di SharePoint a cui viene in genere fatto riferimento negli elementi **ProjectItemFile** includono i file degli elementi della funzionalità (*Elements.xml*), i file di schema per le definizioni di elenco (*Schema.xml*) e i file di definizione della web part per Web part (*. WebPart*).

## <a name="element-information"></a>Informazioni sull'elemento

|Proprietà|Valore|
|-|-|
|**Namespace**|http: \/ \/ schemas.Microsoft.com/VisualStudio/<br>2010/SharePointTools/SharePointProjectItemModel|
|**Nome schema**|Schema dell'elemento del progetto SharePoint|
|**File di convalida**|ProjectItemModelSchema. xsd|
|**Può essere vuoto**|No|

## <a name="see-also"></a>Vedere anche
- [Riferimento allo schema degli elementi di progetto SharePoint](../sharepoint/sharepoint-project-item-schema-reference.md)
