---
title: '&lt;postActionData&gt; elemento (sviluppo per Office in Visual Studio) | Documenti Microsoft'
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
- <postActionData> element
- application manifests [Office development in Visual Studio], <postActionData> element
- postActionData element
ms.assetid: e36cbd64-fd27-4413-b293-cf5546fbdfaf
caps.latest.revision: "16"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 27a495182daa76da286fd6ac46773727600ff05d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="ltpostactiondatagt-element-office-development-in-visual-studio"></a>&lt;postActionData&gt; elemento (sviluppo per Office in Visual Studio)
  L'elemento `postActionData` dello spazio dei nomi `vstav3` specifica i dati associati a qualsiasi azione post-distribuzione che viene eseguita dopo l'installazione di soluzioni Office.  
  
## <a name="syntax"></a>Sintassi  
  
```  
<postActionData>  
</postActionData>  
```  
  
## <a name="elements-and-attributes"></a>Elementi e attributi  
 L'elemento `postActionData` è facoltativo e si trova nello spazio dei nomi `vstav3` . Per ogni azione post-distribuzione è definito un elemento `postActionData` in un manifesto dell'applicazione.  
  
 L'elemento `postActions` non ha attributi.  
  
 `postActions` è privo di elementi figlio.  
  
## <a name="post-deployment-action-example"></a>Esempio di azione post-distribuzione  
  
### <a name="description"></a>Descrizione  
 L'esempio di codice seguente illustra l'elemento `postAction` in un manifesto dell'applicazione per una soluzione Office distribuita con [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Questo esempio di codice fa parte di un esempio più esaustivo disponibile in [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md).  
  
### <a name="code"></a>Codice  
  
```  
<vstav3:postActionData>  
  data in any format  
</vstav3:postActionData>  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md)   
 [Manifesti di distribuzione per le soluzioni Office](../vsto/deployment-manifests-for-office-solutions.md)   
 [ClickOnce Application Manifest](/visualstudio/deployment/clickonce-application-manifest)  
  
  