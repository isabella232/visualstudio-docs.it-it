---
title: '&lt;Elemento postAction &gt; (Office sviluppo in Visual Studio)'
description: L'elemento postAction dello spazio dei nomi vstav3 contiene gli elementi entrypoint e tutti gli elementi postActionData associati alle azioni post-distribuzione, che vengono eseguite dopo l'installazione Office soluzioni.
ms.date: 02/02/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application manifests [Office development in Visual Studio], <postAction> element
- <postAction> element
- postAction element
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: ec3988628f579023cddf5ff9f49a47d323fa9742
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122032290"
---
# <a name="ltpostactiongt-element-office-development-in-visual-studio"></a>&lt;Elemento postAction &gt; (Office sviluppo in Visual Studio)
  L'elemento `postAction` dello spazio dei nomi `vstav3` contiene gli elementi `entrypoint` e tutti gli elementi `postActionData` associati alle azioni post-distribuzione, che vengono eseguite dopo l'installazione delle soluzioni Office.

## <a name="syntax"></a>Sintassi

```xml
<postAction>
  <entryPoint>
  </entryPoint>
  <postActionData>
  </postActionData>
</postAction>
```

## <a name="elements-and-attributes"></a>Elementi e attributi
 L'elemento `postAction` è facoltativo e si trova nello spazio dei nomi `vstav3` . Per ogni azione post-distribuzione è definito un elemento `postAction` in un manifesto dell'applicazione.

 L'elemento `postAction` non ha attributi.

 `postAction` presenta gli elementi seguenti:

### <a name="entrypoint"></a>entryPoint
 facoltativo. Il ruolo dell'elemento nello spazio dei nomi è definito `entryPoint` `vstav3` in&#60;[entryPoints ](../vsto/entrypoints-element-office-development-in-visual-studio.md)&#62; elemento &#40;Office sviluppo in Visual Studio&#41;.

### <a name="postactiondata"></a>postActionData
 facoltativo. Il ruolo dell'elemento nello spazio dei nomi è definito&#60;elemento `postActionData` `vstav3`&#62; [postActionData ](../vsto/postactiondata-element-office-development-in-visual-studio.md)&#40;Office sviluppo in Visual Studio&#41;.

## <a name="post-deployment-action-example"></a>Esempio di azione post-distribuzione

### <a name="description"></a>Descrizione
 L'esempio di codice seguente illustra l'elemento `postAction` in un manifesto dell'applicazione per una soluzione Office distribuita tramite [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Questo esempio di codice fa parte di un esempio più ampio fornito in [Manifesti dell'applicazione per Office soluzioni](../vsto/application-manifests-for-office-solutions.md).

### <a name="code"></a>Codice

```xml
<vstav3:postAction>
  <vstav3:entryPoint
    class="PostDeploymentAction.PostDeploymentActionSample">
    <assemblyIdentity
      name="PostDeploymentAction"
      version="1.0.0.0"
      language="neutral"
      processorArchitecture="msil" />
  </vstav3:entryPoint>
  <vstav3:postActionData>
  </vstav3:postActionData>
</vstav3:postAction>
```

## <a name="see-also"></a>Vedi anche

- [Manifesti dell'applicazione per Office soluzioni](../vsto/application-manifests-for-office-solutions.md)
- [Manifesti di distribuzione per Office soluzioni](../vsto/deployment-manifests-for-office-solutions.md)
- [ClickOnce manifesto dell'applicazione](../deployment/clickonce-application-manifest.md)
