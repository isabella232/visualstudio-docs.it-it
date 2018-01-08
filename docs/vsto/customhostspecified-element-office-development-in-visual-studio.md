---
title: '&lt;customHostSpecified&gt; elemento (sviluppo per Office in Visual Studio) | Documenti Microsoft'
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
- application manifests [Office development in Visual Studio], <customHostSpecified> element
- <customHostSpecified> element
- customHostSpecified element
ms.assetid: 2212b7eb-bf94-4398-b9ea-0ab00203203b
caps.latest.revision: "23"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 7f3a90c9a53059a9b356fe44c6c66fabd5821416
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="ltcustomhostspecifiedgt-element-office-development-in-visual-studio"></a>&lt;customHostSpecified&gt; elemento (sviluppo per Office in Visual Studio)
  Il `customHostSpecified` elemento indica che questa soluzione non è un'applicazione autonoma. Soluzioni Office contengono componenti che sono ospitati all'interno di applicazioni di Microsoft Office.  
  
## <a name="syntax"></a>Sintassi  
  
```  
<customHostSpecified />  
```  
  
## <a name="elements-and-attributes"></a>Elementi e attributi  
 Il `customHostSpecified` elemento è obbligatorio per le soluzioni Office. Questo elemento è presente il `co.v1` dello spazio dei nomi e specifica che la distribuzione contiene un componente che verrà distribuito all'interno di un host personalizzato e non è un'applicazione autonoma.  
  
 Questo è un elemento figlio del primo `<entrypoint>` elemento nel manifesto dell'applicazione. Non può esistere alcun altri elementi figlio che `<entrypoint>` elemento o [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] genererà un errore di convalida durante l'installazione.  
  
 Questo elemento dispone di alcun attributo e non gli elementi figlio.  
  
## <a name="example"></a>Esempio  
 Nell'esempio di codice seguente viene illustrato il `customHostSpecified` elemento in un manifesto dell'applicazione per una soluzione Office. Questo esempio di codice fa parte di un esempio più esaustivo disponibile in [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md).  
  
```  
<entryPoint>  
    <co.v1:customHostSpecified />  
</entryPoint>  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md)   
 [Manifesti di distribuzione per le soluzioni Office](../vsto/deployment-manifests-for-office-solutions.md)   
 [ClickOnce Application Manifest](/visualstudio/deployment/clickonce-application-manifest)  
  
  