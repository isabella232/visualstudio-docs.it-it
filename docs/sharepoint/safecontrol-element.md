---
title: Elemento SafeControl | Microsoft Docs
description: Ottenere informazioni sull'elemento SafeControl, che rappresenta un controllo ASPX o una web part contrassegnata come sicura per l'accesso da parte di un utente SharePoint pagina ASPX di un sito web.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SafeControl element
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: 04db1be46cbc2ff3830b00f9c3866e2859485a6f755514ea28333cada757190d
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121244173"
---
# <a name="safecontrol-element"></a>SafeControl (elemento)
  Rappresenta un controllo ASPX o una web part designata come sicura per l'accesso da parte di qualsiasi utente in qualsiasi pagina ASPX del SharePoint sito.

## <a name="syntax"></a>Sintassi

```xml
<SafeControl Assembly = "Name of assembly that contains the safe control"
    IsSafe = "true/false"
    IsSafeAgainstScript = "true/false"
    Name = "Name of this safe control entry"
    Namespace = "Namespace of the safe control"
    TypeName = "Type of the safe control" />
```

## <a name="attributes-and-elements"></a>Attributi ed elementi
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.

### <a name="attributes"></a>Attributi

|Attributo|Descrizione|
|---------------|-----------------|
|**Assembly**|Attributo **xs:string facoltativo.**<br /><br /> Nome dell'assembly in cui è definito il controllo ASPX o la web part. Per impostazione predefinita, questo attributo usa **$SharePoint.Project. Parametro sostituibile AssemblyFullName$** per il nome dell'assembly. Per altre informazioni, vedere [Parametri sostituibili.](../sharepoint/replaceable-parameters.md)|
|**IsSafe**|Attributo **xs:boolean facoltativo.**<br /><br /> Specifica se l'accesso al controllo ASPX o alla web part è sicuro per gli utenti non attendibili.|
|**IsSafeAgainstScript**|Attributo **xs:boolean facoltativo.**<br /><br /> Specifica se gli utenti non attendibili possono visualizzare o modificare le proprietà del controllo ASPX o della web part.|
|**Nome**|Attributo **xs:string facoltativo.**<br /><br /> Nome di questa voce di controllo sicuro nell'insieme.|
|**Namespace**|Attributo **xs:string facoltativo.**<br /><br /> Spazio dei nomi del controllo ASPX o della web part.|
|**Typename**|Attributo **xs:string facoltativo.**<br /><br /> Nome del tipo del controllo ASPX o della web part.|

### <a name="child-elements"></a>Elementi figlio
 Nessuno.

### <a name="parent-elements"></a>Elementi padre

|Elemento|Descrizione|
|-------------|-----------------|
|[SafeControls](../sharepoint/safecontrols-element.md)|Rappresenta una raccolta di controlli ASPX e Web part designati come sicuri per l'accesso da parte di qualsiasi utente in qualsiasi pagina ASPX nel SharePoint web.|

## <a name="remarks"></a>Commenti
 Per altre informazioni sui controlli sicuri, vedere Fornire informazioni sulla [creazione di pacchetti e sulla distribuzione negli elementi del progetto.](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)

## <a name="element-information"></a>Informazioni sull'elemento

|Proprietà|Valore|
|-|-|
|**Namespace**|http: \/ \/ schemas.microsoft.com/VisualStudio/<br>2010/SharePointTools/SharePointProjectItemModel|
|**Nome schema**|SharePoint Project schema dell'elemento|
|**File di convalida**|ProjectItemModelSchema.xsd|
|**Può essere vuoto**|No|

## <a name="see-also"></a>Vedere anche
- [SharePoint sullo schema dell'elemento di progetto](../sharepoint/sharepoint-project-item-schema-reference.md)
- [Fornire informazioni sulla creazione di pacchetti e sulla distribuzione negli elementi del progetto](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)
