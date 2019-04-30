---
title: Elemento SafeControls | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SafeControls element
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: ce943416bba84c46ce7b709c3d2bdb6ddb3e4447
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63009558"
---
# <a name="safecontrols-element"></a>SafeControls (elemento)
  Raccolta di controlli ASPX e Web part che sono designate come protette per tutti gli utenti accedere in qualsiasi pagina ASPX nel sito di SharePoint.

## <a name="syntax"></a>Sintassi

```xml
<SafeControls>
  <SafeControl.../>
</SafeControls>
```

## <a name="attributes-and-elements"></a>Attributi ed elementi
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.

### <a name="attributes"></a>Attributi
 Nessuno.

### <a name="child-elements"></a>Elementi figlio

|Elemento|Descrizione|
|-------------|-----------------|
|[SafeControl](../sharepoint/safecontrol-element.md)|Elemento facoltativo.<br /><br /> Rappresenta un controllo ASPX o una Web Part che è designato come protetto per tutti gli utenti accedere in qualsiasi pagina ASPX nel sito di SharePoint.|

### <a name="parent-elements"></a>Elementi padre

|Elemento|Descrizione|
|-------------|-----------------|
|[ProjectItem](../sharepoint/projectitem-element.md)|Rappresenta un elemento del progetto SharePoint. Questo elemento l'elemento radice obbligatorio del *spdata* file.|

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
