---
title: '&lt;friendlyName&gt; elemento (sviluppo per Office in Visual Studio) | Documenti Microsoft'
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
helpviewer_keywords: application manifests [Office development in Visual Studio], <friendlyName> element
ms.assetid: 80250fbf-fccf-4baa-948e-ace7f4449e9c
caps.latest.revision: "19"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 9b08121ffb9a9320f7a0d8a8828ee166f94bfa0a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="ltfriendlynamegt-element-office-development-in-visual-studio"></a>&lt;friendlyName&gt; elemento (sviluppo per Office in Visual Studio)
  L'elemento `friendlyName` dello spazio dei nomi `vstov4` archivia il nome visualizzato nell'elenco dei programmi installati.  
  
## <a name="syntax"></a>Sintassi  
  
```  
<friendlyName>  
</friendlyName>  
```  
  
## <a name="elements-and-attributes"></a>Elementi e attributi  
 L'elemento `friendlyName` si trova nello spazio dei nomi `vstov4` . Il valore viene visualizzato nell'elenco dei programmi installati nel computer e nella finestra di dialogo del componente aggiuntivo VSTO COM delle applicazioni Microsoft Office.  
  
 L'elemento `friendlyName` è privo di attributi o elementi figlio.  
  
## <a name="vsto-add-in-example"></a>Esempio di componente aggiuntivo VSTO  
  
### <a name="description"></a>Descrizione  
 L'esempio di codice seguente illustra l'elemento `friendlyName` in una soluzione a livello di applicazione distribuita con [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Questo esempio di codice fa parte di un esempio più esaustivo disponibile in [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md).  
  
### <a name="code"></a>Codice  
  
```  
<vstov4:friendlyName>  
  ContosoOutlookAddIn  
</vstov4:friendlyName>  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md)   
 [Manifesti di distribuzione per le soluzioni Office](../vsto/deployment-manifests-for-office-solutions.md)   
 [ClickOnce Application Manifest](/visualstudio/deployment/clickonce-application-manifest)  
  
  