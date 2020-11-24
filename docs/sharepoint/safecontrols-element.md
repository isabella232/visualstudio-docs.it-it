---
title: Elemento SafeControls | Microsoft Docs
description: Ottenere informazioni sull'elemento SafeControls, che include una raccolta di controlli o Web part ASPX contrassegnati come sicuri per l'accesso nella pagina ASPX di un sito di SharePoint.
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: c3423d1b6efd106ef7f947bd8573dcd1aa548a66
ms.sourcegitcommit: 02f14db142dce68d084dcb0a19ca41a16f5bccff
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/23/2020
ms.locfileid: "95440675"
---
# <a name="safecontrols-element"></a>SafeControls (elemento)
  Raccolta di controlli e Web part ASPX designati come sicuri per qualsiasi utente per accedere a qualsiasi pagina ASPX nel sito di SharePoint.

## <a name="syntax"></a>Sintassi

```xml
<SafeControls>
  <SafeControl.../>
</SafeControls>
```

## <a name="attributes-and-elements"></a>Attributi ed elementi
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.

### <a name="attributes"></a>Attributes
 No.

### <a name="child-elements"></a>Elementi figlio

|Elemento|Descrizione|
|-------------|-----------------|
|[SafeControl](../sharepoint/safecontrol-element.md)|Elemento facoltativo.<br /><br /> Rappresenta una Web part o un controllo ASPX designato come sicuro per qualsiasi utente per accedere a qualsiasi pagina ASPX nel sito di SharePoint.|

### <a name="parent-elements"></a>Elementi padre

|Elemento|Descrizione|
|-------------|-----------------|
|[ProjectItem](../sharepoint/projectitem-element.md)|Rappresenta un elemento del progetto SharePoint. Questo elemento è l'elemento radice obbligatorio del file con *estensione spdata* .|

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
