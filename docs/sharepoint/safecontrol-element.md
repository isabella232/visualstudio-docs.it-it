---
title: Elemento SafeControl | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SafeControl element
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: e6b47254a80c9cdadab6ca18f2fb8c3e8540fbd0
ms.sourcegitcommit: 3d37c2460584f6c61769be70ef29c1a67397cf14
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/21/2019
ms.locfileid: "58324565"
---
# <a name="safecontrol-element"></a>SafeControl (elemento)
  Rappresenta un controllo ASPX o una Web Part che è designato come protetto per tutti gli utenti accedere in qualsiasi pagina ASPX nel sito di SharePoint.

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
|**Assembly**|Facoltativo **xs: String** attributo.<br /><br /> Il nome dell'assembly in cui è definito il controllo ASPX o una Web Part. Per impostazione predefinita, questo attributo Usa il **$SharePoint.Project.AssemblyFullName$** parametro sostituibile per il nome dell'assembly. Per altre informazioni, vedere [parametri sostituibili](../sharepoint/replaceable-parameters.md).|
|**IsSafe**|Facoltativo **xs: Boolean** attributo.<br /><br /> Specifica se il controllo ASPX o una Web Part è sicura per gli utenti non attendibili di accedere.|
|**IsSafeAgainstScript**|Facoltativo **xs: Boolean** attributo.<br /><br /> Specifica se gli utenti non attendibili possono visualizzare o modificare le proprietà del controllo ASPX o Web Part.|
|**Name**|Facoltativo **xs: String** attributo.<br /><br /> Il nome di questa voce di controllo sicura nell'insieme.|
|**Spazio dei nomi**|Facoltativo **xs: String** attributo.<br /><br /> Lo spazio dei nomi del controllo ASPX o Web Part.|
|**TypeName**|Facoltativo **xs: String** attributo.<br /><br /> Il nome del tipo del controllo ASPX o Web Part.|

### <a name="child-elements"></a>Elementi figlio
 Nessuno.

### <a name="parent-elements"></a>Elementi padre

|Elemento|Descrizione|
|-------------|-----------------|
|[SafeControls](../sharepoint/safecontrols-element.md)|Rappresenta una raccolta di controlli ASPX e Web part che sono definiti come sicuri per tutti gli utenti accedere in qualsiasi pagina ASPX nel sito di SharePoint.|

## <a name="remarks"></a>Note
 Per altre informazioni sui controlli sicuri, vedere [fornire le informazioni di creazione di pacchetti e distribuzione negli elementi di progetto](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md).

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
