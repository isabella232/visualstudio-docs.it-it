---
description: L'elemento friendlyName dello spazio dei nomi vstov4 archivia il nome visualizzato nell'elenco dei programmi installati.
title: '&lt;Elemento friendlyName &gt; (Office sviluppo in Visual Studio)'
titleSuffix: ''
ms.custom: seodec18
ms.date: 02/02/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application manifests [Office development in Visual Studio], <friendlyName> element
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 887c28cdd81f4f3176dcf29804fa9f6ec4b27123
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122083609"
---
# <a name="ltfriendlynamegt-element-office-development-in-visual-studio"></a>&lt;Elemento friendlyName &gt; (Office sviluppo in Visual Studio)
  L'elemento `friendlyName` dello spazio dei nomi `vstov4` archivia il nome visualizzato nell'elenco dei programmi installati.

## <a name="syntax"></a>Sintassi

```xml
<friendlyName>
</friendlyName>
```

## <a name="elements-and-attributes"></a>Elementi e attributi
 L'elemento `friendlyName` si trova nello spazio dei nomi `vstov4` . Il valore viene visualizzato nell'elenco dei programmi installati nel computer e nella finestra di dialogo del componente aggiuntivo VSTO COM delle applicazioni Microsoft Office.

 L'elemento `friendlyName` è privo di attributi o elementi figlio.

## <a name="vsto-add-in-example"></a>VSTO Esempio di componente aggiuntivo

### <a name="description"></a>Descrizione
 L'esempio di codice seguente illustra l'elemento `friendlyName` in una soluzione a livello di applicazione distribuita con [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Questo esempio di codice fa parte di un esempio più ampio fornito nei [manifesti dell'applicazione per Office soluzioni](../vsto/application-manifests-for-office-solutions.md).

### <a name="code"></a>Codice

```xml
<vstov4:friendlyName>
  ContosoOutlookAddIn
</vstov4:friendlyName>
```

## <a name="see-also"></a>Vedi anche

- [Manifesti dell'applicazione per Office soluzioni](../vsto/application-manifests-for-office-solutions.md)
- [Manifesti di distribuzione per Office soluzioni](../vsto/deployment-manifests-for-office-solutions.md)
- [ClickOnce manifesto dell'applicazione](../deployment/clickonce-application-manifest.md)
