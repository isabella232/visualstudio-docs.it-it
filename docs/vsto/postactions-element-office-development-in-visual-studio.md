---
title: '&lt;postActions&gt; elemento (sviluppo per Office in Visual Studio) | Documenti Microsoft'
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application manifests [Office development in Visual Studio], <postActions> element
- postActions element
- <postActions> element
ms.assetid: 6e487549-fdd6-49bd-be7a-b91f1f964594
caps.latest.revision: "16"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: d3635a92f40f2ed313ca08dcc6357900ac002a60
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="ltpostactionsgt-element-office-development-in-visual-studio"></a>&lt;postActions&gt; elemento (sviluppo per Office in Visual Studio)
  L'elemento `postActions` dello spazio dei nomi `vstav3` contiene tutti gli elementi `postAction` che descrivono le azioni post-distribuzione, che vengono eseguite dopo l'installazione delle soluzioni Office.  
  
## <a name="syntax"></a>Sintassi  
  
```  
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
 Facoltativo. Il ruolo del `postAction` elemento il `vstav3` dello spazio dei nomi è definito in [&#60; postAction &#62; Elemento &#40; sviluppo per Office in Visual Studio &#41; ](../vsto/postaction-element-office-development-in-visual-studio.md).  
  
## <a name="post-deployment-action-example"></a>Esempio di azione post-distribuzione  
  
### <a name="description"></a>Descrizione  
 L'esempio di codice seguente illustra l'elemento `postActions` in un manifesto dell'applicazione per una soluzione Office distribuita con [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Questo esempio di codice fa parte di un esempio più esaustivo disponibile in [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md).  
  
### <a name="code"></a>Codice  
  
```  
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
  
## <a name="see-also"></a>Vedere anche  
 [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md)   
 [Manifesti di distribuzione per le soluzioni Office](../vsto/deployment-manifests-for-office-solutions.md)   
 [ClickOnce Application Manifest](/visualstudio/deployment/clickonce-application-manifest)  
  
  