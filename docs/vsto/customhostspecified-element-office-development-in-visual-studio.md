---
title: '&lt;Elemento customHostSpecified &gt; (Office sviluppo in Visual Studio)'
description: Informazioni su come l'elemento customHostSpecified indichi che questa soluzione non è un'applicazione autonoma.
titleSuffix: ''
ms.custom: seodec18, SEO-VS-2020
ms.date: 02/02/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application manifests [Office development in Visual Studio], <customHostSpecified> element
- <customHostSpecified> element
- customHostSpecified element
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 9c2e9595b3ff10c1769aa1546637fd6743b27358
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122148324"
---
# <a name="ltcustomhostspecifiedgt-element-office-development-in-visual-studio"></a>&lt;Elemento customHostSpecified &gt; (Office sviluppo in Visual Studio)
  `customHostSpecified`L'elemento indica che questa soluzione non è un'applicazione autonoma. Office soluzioni contengono componenti ospitati all'interno Microsoft Office applicazioni.

## <a name="syntax"></a>Sintassi

```xml
<customHostSpecified />
```

## <a name="elements-and-attributes"></a>Elementi e attributi
 `customHostSpecified`L'elemento è obbligatorio per Office soluzioni. Questo elemento si trova nello spazio dei nomi e specifica che questa distribuzione contiene un componente che verrà distribuito all'interno di un host personalizzato e non `co.v1` è un'applicazione autonoma.

 Questo elemento è un elemento figlio del primo `<entrypoint>` elemento nel manifesto dell'applicazione. Non possono essere presenti altri elementi figlio in tale elemento `<entrypoint>` o verrà generato un errore di convalida durante [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] l'installazione.

 Questo elemento non ha attributi e nessun elemento figlio.

## <a name="example"></a>Esempio
 L'esempio di codice seguente illustra `customHostSpecified` l'elemento in un manifesto dell'applicazione per una Office soluzione. Questo esempio di codice fa parte di un esempio più ampio fornito nei [manifesti dell'applicazione per Office soluzioni](../vsto/application-manifests-for-office-solutions.md).

```xml
<entryPoint>
    <co.v1:customHostSpecified />
</entryPoint>
```

## <a name="see-also"></a>Vedi anche

- [Manifesti dell'applicazione per Office soluzioni](../vsto/application-manifests-for-office-solutions.md)
- [Manifesti di distribuzione per Office soluzioni](../vsto/deployment-manifests-for-office-solutions.md)
- [ClickOnce manifesto dell'applicazione](../deployment/clickonce-application-manifest.md)