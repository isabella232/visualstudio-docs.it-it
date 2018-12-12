---
title: '&lt;appAddin&gt; elemento (sviluppo per Office in Visual Studio)'
titleSuffix: ''
ms.custom: ''
ms.date: 02/02/2017
ms.technology: office-development
ms.prod: visual-studio-dev15
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application manifests [Office development in Visual Studio], <appAddin> element
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: 3160f153bb6775cf5b2541abf4f75069c818f82b
ms.sourcegitcommit: 20c0991d737c540750c613c380cd4cf5bb07de51
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/11/2018
ms.locfileid: "53248072"
---
# <a name="ltappaddingt-element-office-development-in-visual-studio"></a>&lt;appAddin&gt; elemento (sviluppo per Office in Visual Studio)
  Il **appAddin** dell'elemento il `vstov4` dello spazio dei nomi archivia le informazioni specifiche della personalizzazione per componenti aggiuntivi VSTO.  
  
## <a name="syntax"></a>Sintassi  
  
```xml 
<appAddin  
  application  
  loadBehavior  
  keyName>  
  <friendlyName>  
  <description>  
  <formRegions></formRegions>  
</appAddin>  
```  
  
## <a name="elements-and-attributes"></a>Gli elementi e attributi  
 Il **appAddin** elemento è obbligatorio e si trova il `vstov4` dello spazio dei nomi. È presente una sola **appAddin** elemento definito in un manifesto dell'applicazione.  
  
 Il **appAddin** elemento ha gli attributi seguenti.  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|**Applicazione**|Obbligatorio. Identifica l'applicazione di Microsoft Office. Il valore può essere uno dei seguenti: Excel, InfoPath, Outlook, PowerPoint, Project, Visio o Word.|  
|**LoadBehavior**|Facoltativo. Per impostazione predefinita, il **loadBehavior** viene abilitato impostando questo valore. Per il debug, il componente aggiuntivo VSTO può essere disabilitato impostando il valore su due. Per altre informazioni, vedere la tabella intitolata valori di LoadBehavior in [voci del Registro di sistema per componenti aggiuntivi VSTO](../vsto/registry-entries-for-vsto-add-ins.md).|  
|**Nome chiave**|Obbligatorio. Questo valore corrisponde al nome della chiave del Registro di sistema che verrà usata dall'applicazione per il caricamento del componente aggiuntivo VSTO. Per altre informazioni, vedere [voci del Registro di sistema per componenti aggiuntivi VSTO](../vsto/registry-entries-for-vsto-add-ins.md).|  
  
 Il **appAddin** elemento ha i seguenti elementi figlio.  
  
### <a name="friendlyname"></a>friendlyName  
 Facoltativo. Il **friendlyName** elemento viene descritto [ &#60;friendlyName&#62; elemento &#40;sviluppo per Office in Visual Studio&#41;](../vsto/friendlyname-element-office-development-in-visual-studio.md).  
  
### <a name="description"></a>Descrizione  
 Facoltativo. Il **description** elemento viene descritto [ &#60;descrizione&#62; elemento &#40;sviluppo per Office in Visual Studio&#41;](../vsto/description-element-office-development-in-visual-studio.md).  
  
### <a name="formregions"></a>formRegions  
 Obbligatorio solo per i componenti aggiuntivi VSTO di Outlook che includono aree di modulo. Il **formRegions** elemento viene descritto [ &#60;formRegions&#62; elemento &#40;sviluppo per Office in Visual Studio&#41;](../vsto/formregions-element-office-development-in-visual-studio.md).  
  
## <a name="vsto-add-in-example"></a>Esempio di componente aggiuntivo VSTO  
  
### <a name="description"></a>Descrizione  
 L'esempio di codice seguente illustra **appAddin** elementi in una soluzione Outlook distribuita con [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Questo esempio di codice è parte di un esempio più esaustivo disponibile nel [manifesti dell'applicazione per le soluzioni Office](../vsto/application-manifests-for-office-solutions.md).  
  
### <a name="code"></a>Codice  
  
```xml  
<vstov4:appAddIn   
  application="Outlook"   
  loadBehavior="3"   
  keyName="ContosoOutlookAddIn">  
  <vstov4:friendlyName>  
    ContosoOutlookAddIn  
  </vstov4:friendlyName>  
  <vstov4:description>  
    ContosoOutlookAddIn - Outlook VSTO Add-in   
    created with Visual Studio Tools for Office  
  </vstov4:description>  
  <vstov4:formRegions>  
    <vstov4:formRegion  
        name="OutlookAddIn1.FormRegion1">  
      <vstov4:messageClass name="IPM.Note" />  
      <vstov4:messageClass name="IPM.Contact" />  
      <vstov4:messageClass name="IPM.Appointment" />  
    </vstov4:formRegion>  
  </vstov4:formRegions>  
</vstov4:appAddIn>  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Manifesti dell'applicazione per le soluzioni Office](../vsto/application-manifests-for-office-solutions.md)   
 [Manifesti della distribuzione per le soluzioni Office](../vsto/deployment-manifests-for-office-solutions.md)   
 [Manifesto dell'applicazione ClickOnce](/visualstudio/deployment/clickonce-application-manifest)  
  
  