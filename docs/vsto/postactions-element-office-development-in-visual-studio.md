---
title: '&lt;Elemento postActions &gt; (Office sviluppo)'
description: L'elemento postActions dello spazio dei nomi vstav3 contiene tutti gli elementi postAction che descrivono le azioni post-distribuzione, che vengono eseguite dopo l'installazione Office soluzioni.
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application manifests [Office development in Visual Studio], <postActions> element
- postActions element
- <postActions> element
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 9051d2a4947057eed815b234880702c198426949
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122147778"
---
# <a name="ltpostactionsgt-element-office-development"></a>&lt;Elemento postActions &gt; (Office sviluppo)
  L'elemento `postActions` dello spazio dei nomi `vstav3` contiene tutti gli elementi `postAction` che descrivono le azioni post-distribuzione, che vengono eseguite dopo l'installazione delle soluzioni Office.

## <a name="syntax"></a>Sintassi

```xml
<postActions>
  <postAction>
    <entryPoint>
    </entryPoint>
    <postActionData>
    </postActionData>
  </postAction>
</postActions>
```

## <a name="elements-and-attributes"></a>Elementi e attributi
 L'elemento `postActions` è facoltativo e si trova nello spazio dei nomi `vstav3` . Viene definito un solo elemento `postActions` in un manifesto dell'applicazione.

 L'elemento `postActions` non ha attributi.

 `postActions` presenta l'elemento seguente:

### <a name="postaction"></a>postAction
 facoltativo. Il ruolo dell'elemento nello spazio dei nomi è definito `postAction` `vstav3` in&#60;[postAction&#62;'elemento ](../vsto/postaction-element-office-development-in-visual-studio.md)&#40;Office sviluppo in Visual Studio&#41;.

## <a name="post-deployment-action-example"></a>Esempio di azione post-distribuzione

### <a name="description"></a>Descrizione
 L'esempio di codice seguente illustra l'elemento `postActions` in un manifesto dell'applicazione per una soluzione Office distribuita con [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Questo esempio di codice fa parte di un esempio più ampio fornito nei [manifesti dell'applicazione per Office soluzioni](../vsto/application-manifests-for-office-solutions.md).

### <a name="code"></a>Codice

```xml
<vstav3:postActions>
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
</vstav3:postActions>
```

## <a name="see-also"></a>Vedi anche

- [Manifesti dell'applicazione per Office soluzioni](../vsto/application-manifests-for-office-solutions.md)
- [Manifesti di distribuzione per Office soluzioni](../vsto/deployment-manifests-for-office-solutions.md)
- [ClickOnce manifesto dell'applicazione](../deployment/clickonce-application-manifest.md)
