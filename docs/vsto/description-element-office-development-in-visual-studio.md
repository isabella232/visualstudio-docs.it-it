---
title: '&lt;Descrizione&gt; elemento (sviluppo per Office in Visual Studio) | Documenti Microsoft'
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
- description element
- <description> element
- application manifests [Office development in Visual Studio], <description> element
ms.assetid: 27c90f8c-393d-4557-9371-2e4e3c4a2d95
caps.latest.revision: "21"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 350a9003fcb87a6226e9ea14f7734aa40b9e62db
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="ltdescriptiongt-element-office-development-in-visual-studio"></a>&lt;Descrizione&gt; elemento (sviluppo per Office in Visual Studio)
  L'elemento `description` dello spazio dei nomi `vstov4` archivia la descrizione della soluzione Office che viene visualizzata nella finestra di dialogo dei componenti aggiuntivi COM delle applicazioni di Microsoft Office.  
  
## <a name="syntax"></a>Sintassi  
  
```  
<description>  
</description>  
```  
  
## <a name="elements-and-attributes"></a>Elementi e attributi  
 Facoltativo. L'elemento `description` si trova nello spazio dei nomi `vstov4` . Contiene la descrizione del componente aggiuntivo che viene visualizzata nella finestra di dialogo dei componenti aggiuntivi COM delle applicazioni di Microsoft Office.  
  
 L'elemento `description` è privo di attributi o elementi.  
  
## <a name="vsto-add-in-example"></a>Esempio di componente aggiuntivo VSTO  
  
### <a name="description"></a>description  
 L'esempio di codice seguente illustra l'elemento `description` in una soluzione a livello di applicazione distribuita tramite [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Questo esempio di codice fa parte di un esempio più esaustivo disponibile in [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md).  
  
### <a name="code"></a>Codice  
  
```  
<vstov4:description>  
  ContosoOutlookAddIn - Outlook add-in   
  created with Visual Studio Tools for Office  
</vstov4:description>  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md)   
 [Manifesti di distribuzione per le soluzioni Office](../vsto/deployment-manifests-for-office-solutions.md)   
 [ClickOnce Application Manifest](/visualstudio/deployment/clickonce-application-manifest)  
  
  