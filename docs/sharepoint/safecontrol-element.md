---
title: Elemento SafeControl | Microsoft Docs
description: Ottenere informazioni sull'elemento SafeControl, che rappresenta un controllo ASPX o una Web part contrassegnata come sicura per l'accesso di un utente in una pagina ASPX del sito di SharePoint.
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 36a8b0ed45fbdb8d2dfe8e93a027a47adf407587
ms.sourcegitcommit: 02f14db142dce68d084dcb0a19ca41a16f5bccff
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/23/2020
ms.locfileid: "95440623"
---
# <a name="safecontrol-element"></a>SafeControl (elemento)
  Rappresenta una Web part o un controllo ASPX designato come sicuro per qualsiasi utente per accedere a qualsiasi pagina ASPX nel sito di SharePoint.

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

### <a name="attributes"></a>Attributes

|Attributo|Descrizione|
|---------------|-----------------|
|**Assembly**|Attributo **xs: String** facoltativo.<br /><br /> Nome dell'assembly in cui è definito il controllo ASPX o la Web part. Per impostazione predefinita, questo attributo usa il parametro **$SharePoint. Project. AssemblyFullName $** sostituibile per il nome dell'assembly. Per ulteriori informazioni, vedere [parametri sostituibili](../sharepoint/replaceable-parameters.md).|
|**Sicurezza**|Attributo **xs: Boolean** facoltativo.<br /><br /> Specifica se il controllo o la Web part ASPX è protetta per l'accesso agli utenti non attendibili.|
|**IsSafeAgainstScript**|Attributo **xs: Boolean** facoltativo.<br /><br /> Specifica se gli utenti non attendibili possono visualizzare o modificare le proprietà del controllo o della web part ASPX.|
|**Nome**|Attributo **xs: String** facoltativo.<br /><br /> Nome della voce di controllo sicura nella raccolta.|
|**Spazio dei nomi**|Attributo **xs: String** facoltativo.<br /><br /> Spazio dei nomi del controllo o della web part ASPX.|
|**TypeName**|Attributo **xs: String** facoltativo.<br /><br /> Nome del tipo del controllo ASPX o della web part.|

### <a name="child-elements"></a>Elementi figlio
 No.

### <a name="parent-elements"></a>Elementi padre

|Elemento|Descrizione|
|-------------|-----------------|
|[SafeControls](../sharepoint/safecontrols-element.md)|Rappresenta una raccolta di controlli ASPX e Web part designati come sicuri per qualsiasi utente per accedere a qualsiasi pagina ASPX nel sito di SharePoint.|

## <a name="remarks"></a>Commenti
 Per ulteriori informazioni sui controlli sicuri, vedere [fornire informazioni sulla creazione di pacchetti e sulla distribuzione negli elementi di progetto](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md).

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
