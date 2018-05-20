---
title: '&lt;Descrizione&gt; elemento (sviluppo per Office in Visual Studio)'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- description element
- <description> element
- application manifests [Office development in Visual Studio], <description> element
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 9fcdac1e950d98394b5703322f40dd1823b246f6
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/17/2018
---
# <a name="ltdescriptiongt-element-office-development-in-visual-studio"></a>&lt;Descrizione&gt; elemento (sviluppo per Office in Visual Studio)
  L'elemento `description` dello spazio dei nomi `vstov4` archivia la descrizione della soluzione Office che viene visualizzata nella finestra di dialogo dei componenti aggiuntivi COM delle applicazioni di Microsoft Office.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
<description>  
</description>  
```  
  
## <a name="elements-and-attributes"></a>Elementi e attributi  
 Facoltativo. L'elemento `description` si trova nello spazio dei nomi `vstov4` . Contiene la descrizione del componente aggiuntivo che viene visualizzata nella finestra di dialogo dei componenti aggiuntivi COM delle applicazioni di Microsoft Office.  
  
 L'elemento `description` è privo di attributi o elementi.  
  
## <a name="vsto-add-in-example"></a>Esempio di componente aggiuntivo VSTO  
  
### <a name="description"></a>Descrizione  
 L'esempio di codice seguente illustra l'elemento `description` in una soluzione a livello di applicazione distribuita tramite [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Questo esempio di codice fa parte di un esempio più esaustivo disponibile [manifesti dell'applicazione per le soluzioni Office](../vsto/application-manifests-for-office-solutions.md).  
  
### <a name="code"></a>Codice  
  
```xml  
<vstov4:description>  
  ContosoOutlookAddIn - Outlook add-in   
  created with Visual Studio Tools for Office  
</vstov4:description>  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Manifesti dell'applicazione per le soluzioni Office](../vsto/application-manifests-for-office-solutions.md)   
 [Manifesti della distribuzione per le soluzioni Office](../vsto/deployment-manifests-for-office-solutions.md)   
 [Manifesto dell'applicazione ClickOnce](/visualstudio/deployment/clickonce-application-manifest)  
  
  