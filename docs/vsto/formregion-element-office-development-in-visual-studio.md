---
title: '&lt;formRegion&gt; elemento (sviluppo per Office in Visual Studio) | Documenti Microsoft'
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
helpviewer_keywords: application manifests [Office development in Visual Studio], <formRegion> element
ms.assetid: d397cf31-c0ef-47f0-860a-cd816e4bf6eb
caps.latest.revision: "23"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: bc425459cee4b4398ead78939283ab4db6efc134
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="ltformregiongt-element-office-development-in-visual-studio"></a>&lt;formRegion&gt; elemento (sviluppo per Office in Visual Studio)
  L'elemento `formRegion` dello spazio dei nomi `vstov4` identifica un'area del modulo di Microsoft Office Outlook associata a un componente aggiuntivo VSTO.  
  
## <a name="syntax"></a>Sintassi  
  
```  
<formRegion  
  name>  
  <messageClass  
    name/>  
</formRegion>  
```  
  
## <a name="elements-and-attributes"></a>Elementi e attributi  
 L'elemento `formRegion` dello spazio dei nomi `vstov4` identifica un'area del modulo associata a un componente aggiuntivo VSTO di Outlook. È obbligatorio solo per i componenti aggiuntivi VSTO di Outlook che includono aree del modulo.  
  
 Possono esserci più elementi `formRegion` definiti all'interno di un elemento `formRegions` per un componente aggiuntivo VSTO singolo.  
  
 L'elemento `formRegion` presenta l'attributo seguente:  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|`name`|Obbligatorio. Identifica il nome dell'area del modulo.|  
  
 L'elemento `formRegion` ha gli elementi figlio seguenti.  
  
### <a name="messageclass"></a>messageClass  
 L'elemento `messageClass` identifica il modulo di Outlook associato all'area del modulo.  
  
 L'elemento `messageClass` presenta l'attributo seguente:  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|`name`|Obbligatorio. Identifica il modulo associato all'area del modulo.|  
  
## <a name="example"></a>Esempio  
 L'esempio di codice seguente illustra un elemento `formRegion` in un manifesto dell'applicazione per un componente aggiuntivo VSTO di Outlook distribuito con [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Esistono tre classi di messaggi associate a questa unica area del modulo. Questo esempio di codice fa parte di un esempio più esaustivo disponibile in [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md).  
  
```  
<vstov4:formRegion  
    name="OutlookAddIn1.FormRegion1">  
  <vstov4:messageClass name="IPM.Note" />  
  <vstov4:messageClass name="IPM.Contact" />  
  <vstov4:messageClass name="IPM.Appointment" />  
</vstov4:formRegion>  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Creazione di aree del modulo di Outlook](../vsto/creating-outlook-form-regions.md)   
 [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md)   
 [Manifesti di distribuzione per le soluzioni Office](../vsto/deployment-manifests-for-office-solutions.md)   
 [ClickOnce Application Manifest](/visualstudio/deployment/clickonce-application-manifest)  
  
  