---
title: Elemento SafeControls | Microsoft Docs
description: Ottenere informazioni sull'elemento SafeControls, che contiene una raccolta di controlli ASPX o web part contrassegnati come sicuri per l'accesso SharePoint pagina ASPX di un sito web.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SafeControls element
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: 063da0761f15c1a3b39468a810fd5d3055cece62
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122092787"
---
# <a name="safecontrols-element"></a>SafeControls (elemento)
  Raccolta di controlli ASPX e Web part designati come sicuri per l'accesso da parte di qualsiasi utente in qualsiasi pagina ASPX del SharePoint sito.

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
|[SafeControl](../sharepoint/safecontrol-element.md)|Elemento facoltativo.<br /><br /> Rappresenta un controllo ASPX o una web part designata come sicura per l'accesso da parte di qualsiasi utente in qualsiasi pagina ASPX del SharePoint sito.|

### <a name="parent-elements"></a>Elementi padre

|Elemento|Descrizione|
|-------------|-----------------|
|[ProjectItem](../sharepoint/projectitem-element.md)|Rappresenta un SharePoint di progetto. Questo elemento è l'elemento radice obbligatorio del file *con estensione spdata.*|

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
