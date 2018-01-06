---
title: '&lt;punto di ingresso&gt; elemento (sviluppo per Office in Visual Studio) | Documenti Microsoft'
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
- application manifests [Office development in Visual Studio], <entryPoint> element
- <entryPoint> element
- entryPoint element
ms.assetid: 0c9d22d0-0852-4260-89c6-b83f24e48793
caps.latest.revision: "23"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: a5ef93ab759f4e64607685d3d44fddfbf6c2c2dc
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="ltentrypointgt-element-office-development-in-visual-studio"></a>&lt;punto di ingresso&gt; elemento (sviluppo per Office in Visual Studio)
  Ogni elemento `entryPoint` dello spazio dei nomi `vstav3` identifica un assembly di personalizzazione che deve essere eseguito quando l'applicazione [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] è installata.  
  
## <a name="syntax"></a>Sintassi  
  
```  
<entryPoint class>  
    <assemblyIdentity />  
</entryPoint>  
```  
  
## <a name="elements-and-attributes"></a>Elementi e attributi  
 L'elemento `entryPoint` è obbligatorio e si trova nello spazio dei nomi `vstav3` .  
  
 Ogni elemento `entryPoint` può contenere solo un assembly di personalizzazione. Possono essere definiti più elementi `entryPoint` in un manifesto dell'applicazione.  
  
 L'elemento `entryPoint` presenta gli attributi seguenti.  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|`class`|Obbligatorio. Identifica un assembly di personalizzazione da eseguire. La sintassi per questo attributo è *NamespaceName.ClassName*.|  
  
 `entryPoint` presenta l'elemento seguente:  
  
### <a name="assemblyidentity"></a>assemblyIdentity  
 Obbligatorio. L'elemento `assemblyIdentity` nello spazio dei nomi `vstav3` si riferisce a un elemento `assemblyIdentity` esistente nel manifesto dell'applicazione [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] .  
  
 Il ruolo di `assemblyIdentity` e relativi attributi è definito in [&#60; assemblyIdentity &#62; Elemento &#40; Applicazione ClickOnce &#41; ](/visualstudio/deployment/assemblyidentity-element-clickonce-application).  
  
## <a name="document-level-customization-example"></a>Esempio di personalizzazione a livello di documento  
  
### <a name="description"></a>Descrizione  
 L'esempio di codice seguente illustra elementi `entryPoint` in un manifesto dell'applicazione per una soluzione Office a livello di documento distribuita con [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Questo esempio di codice fa parte di un esempio più esaustivo disponibile in [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md).  
  
### <a name="code"></a>Codice  
  
```  
<vstav3:entryPoint   
  class="ContosoExcelWorkbook.ThisWorkbook">  
  <assemblyIdentity   
    name="ContosoExcelWorkbook"   
    version="1.0.0.0"   
    language="neutral"   
    processorArchitecture="msil" />  
</vstav3:entryPoint>  
<vstav3:entryPoint   
  class="ContosoExcelWorkbook.Sheet1">  
  <assemblyIdentity   
    name="ContosoExcelWorkbook"   
    version="1.0.0.0"   
    language="neutral"   
    processorArchitecture="msil" />  
</vstav3:entryPoint>  
<vstav3:entryPoint   
  class="ContosoExcelWorkbook.Sheet2">  
  <assemblyIdentity   
    name="ContosoExcelWorkbook"   
    version="1.0.0.0"   
    language="neutral"   
    processorArchitecture="msil" />  
</vstav3:entryPoint>  
<vstav3:entryPoint   
  class="ContosoExcelWorkbook.Sheet3">  
  <assemblyIdentity   
    name="ContosoExcelWorkbook"   
    version="1.0.0.0"   
    language="neutral"   
    processorArchitecture="msil" />  
</vstav3:entryPoint>  
```  
  
## <a name="vsto-add-in-example"></a>Esempio di componente aggiuntivo VSTO  
  
### <a name="description"></a>Descrizione  
 L'esempio di codice seguente illustra un elemento `entryPoint` in un manifesto dell'applicazione per una soluzione Office a livello di applicazione distribuita con [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Questo esempio di codice fa parte di un esempio più esaustivo disponibile in [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md).  
  
### <a name="code"></a>Codice  
  
```  
<vstav3:entryPoint   
  class="ContosoOutlookAddIn.ThisAddIn">  
  <assemblyIdentity   
    name="ContosoOutlookAddIn"   
    version="1.0.0.0"   
    language="neutral"   
    processorArchitecture="msil" />  
</vstav3:entryPoint>  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md)   
 [Manifesti di distribuzione per le soluzioni Office](../vsto/deployment-manifests-for-office-solutions.md)   
 [ClickOnce Application Manifest](/visualstudio/deployment/clickonce-application-manifest)  
  
  