---
title: '&lt;&gt;elemento customHostSpecified (sviluppo per Office in Visual Studio)'
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: e8327c6e154f051f5ce79d41ceaa696e330c794f
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/08/2020
ms.locfileid: "96848131"
---
# <a name="ltcustomhostspecifiedgt-element-office-development-in-visual-studio"></a>&lt;&gt;elemento customHostSpecified (sviluppo per Office in Visual Studio)
  L' `customHostSpecified` elemento indica che questa soluzione non è un'applicazione autonoma. Le soluzioni Office contengono componenti ospitati all'interno di Microsoft Office applicazioni.

## <a name="syntax"></a>Sintassi

```xml
<customHostSpecified />
```

## <a name="elements-and-attributes"></a>Elementi e attributi
 L' `customHostSpecified` elemento è obbligatorio per le soluzioni Office. Questo elemento si trova nello `co.v1` spazio dei nomi e specifica che questa distribuzione contiene un componente che verrà distribuito all'interno di un host personalizzato e non è un'applicazione autonoma.

 Questo elemento è un elemento figlio del primo `<entrypoint>` elemento nel manifesto dell'applicazione. Non possono essere presenti altri elementi figlio in tale `<entrypoint>` elemento o [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] verrà generato un errore di convalida durante l'installazione.

 Questo elemento non ha attributi e nessun elemento figlio.

## <a name="example"></a>Esempio
 Nell'esempio di codice seguente viene illustrato l' `customHostSpecified` elemento in un manifesto dell'applicazione per una soluzione Office. Questo esempio di codice fa parte di un esempio più ampio fornito nei [manifesti dell'applicazione per le soluzioni Office](../vsto/application-manifests-for-office-solutions.md).

```xml
<entryPoint>
    <co.v1:customHostSpecified />
</entryPoint>
```

## <a name="see-also"></a>Vedi anche

- [Manifesti dell'applicazione per le soluzioni Office](../vsto/application-manifests-for-office-solutions.md)
- [Manifesti della distribuzione per le soluzioni Office](../vsto/deployment-manifests-for-office-solutions.md)
- [Manifesto dell'applicazione ClickOnce](../deployment/clickonce-application-manifest.md)