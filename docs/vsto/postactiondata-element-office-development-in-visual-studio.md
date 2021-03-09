---
title: '&lt;&gt;elemento postActionData (sviluppo per Office)'
description: L'elemento postActionData dello spazio dei nomi vstav3 specifica i dati associati a qualsiasi azione post-distribuzione che viene eseguita dopo l'installazione delle soluzioni Office.
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- <postActionData> element
- application manifests [Office development in Visual Studio], <postActionData> element
- postActionData element
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: a75f61c6d1f80a127f49d96c4e3f4910c66dd8aa
ms.sourcegitcommit: 8590cf6b3351e82827fd21159beefef0c02bf162
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/08/2021
ms.locfileid: "102470066"
---
# <a name="ltpostactiondatagt-element-office-development"></a>&lt;&gt;elemento postActionData (sviluppo per Office)
  L'elemento `postActionData` dello spazio dei nomi `vstav3` specifica i dati associati a qualsiasi azione post-distribuzione che viene eseguita dopo l'installazione di soluzioni Office.

## <a name="syntax"></a>Sintassi

```xml
<postActionData>
</postActionData>
```

## <a name="elements-and-attributes"></a>Elementi e attributi
 L'elemento `postActionData` è facoltativo e si trova nello spazio dei nomi `vstav3` . Per ogni azione post-distribuzione è definito un elemento `postActionData` in un manifesto dell'applicazione.

 L'elemento `postActions` non ha attributi.

 `postActions` è privo di elementi figlio.

## <a name="post-deployment-action-example"></a>Esempio di azione post-distribuzione

### <a name="description"></a>Descrizione
 L'esempio di codice seguente illustra l'elemento `postAction` in un manifesto dell'applicazione per una soluzione Office distribuita con [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Questo esempio di codice fa parte di un esempio più ampio fornito nei [manifesti dell'applicazione per le soluzioni Office](../vsto/application-manifests-for-office-solutions.md).

### <a name="code"></a>Codice

```xml
<vstav3:postActionData>
  data in any format
</vstav3:postActionData>
```

## <a name="see-also"></a>Vedi anche

- [Manifesti dell'applicazione per le soluzioni Office](../vsto/application-manifests-for-office-solutions.md)
- [Manifesti della distribuzione per le soluzioni Office](../vsto/deployment-manifests-for-office-solutions.md)
- [Manifesto dell'applicazione ClickOnce](../deployment/clickonce-application-manifest.md)
