---
title: '&lt;documento&gt; elemento (sviluppo per Office in Visual Studio)'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- document element
- application manifests [Office development in Visual Studio], <document> element
- <document> element
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 07d8172ec4e56352c2244aef02d947ac48833ab7
ms.sourcegitcommit: 1466ac0f49ebf7448ea4507ae3f79acb25d51d3e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/22/2018
---
# <a name="ltdocumentgt-element-office-development-in-visual-studio"></a>&lt;documento&gt; elemento (sviluppo per Office in Visual Studio)
  Il `document` elemento il `vstov4` dello spazio dei nomi archivia informazioni specifiche della personalizzazione per le personalizzazioni a livello di documento.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
<document solutionId />  
```  
  
## <a name="elements-and-attributes"></a>Elementi e attributi  
 Obbligatorio solo per le personalizzazioni a livello di documento. Il `document` elemento è incluso il `vstov4` dello spazio dei nomi. Il `document` dispone degli attributi seguenti.  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|`solutionId`|Obbligatorio. Il GUID utilizzato da Visual Studio Tools per Office runtime per identificare in modo univoco una soluzione a livello di documento. Questo valore viene memorizzato come proprietà AssemblyLocation personalizzate del documento. Per altre informazioni, vedere [Cenni preliminari sulle proprietà di documento personalizzato](../vsto/custom-document-properties-overview.md).|  
  
 `document` non contiene elementi figlio.  
  
## <a name="document-level-customization-example"></a>Esempio di personalizzazione a livello di documento  
  
### <a name="description"></a>Descrizione  
 Nell'esempio di codice seguente viene illustrato il `document` elemento in una soluzione Office a livello di documento distribuita tramite [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Questo esempio di codice fa parte di un esempio più esaustivo disponibile [manifesti dell'applicazione per le soluzioni Office](../vsto/application-manifests-for-office-solutions.md).  
  
### <a name="code"></a>Codice  
  
```xml
<vstov4:document   
  solutionId="73e" />  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Manifesti dell'applicazione per le soluzioni Office](../vsto/application-manifests-for-office-solutions.md)   
 [Manifesti della distribuzione per le soluzioni Office](../vsto/deployment-manifests-for-office-solutions.md)   
 [Manifesto dell'applicazione ClickOnce](/visualstudio/deployment/clickonce-application-manifest)  
  
  