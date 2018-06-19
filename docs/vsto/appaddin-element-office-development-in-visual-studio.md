---
title: '&lt;appAddin&gt; elemento (sviluppo per Office in Visual Studio)'
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
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 0defe437e0778ee9d3c134148a3ca7e4b4cd2ef9
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/17/2018
ms.locfileid: "34264662"
---
# <a name="ltappaddingt-element-office-development-in-visual-studio"></a>&lt;appAddin&gt; elemento (sviluppo per Office in Visual Studio)
  Il **appAddin** elemento del `vstov4` dello spazio dei nomi archivia le informazioni specifiche della personalizzazione per componenti aggiuntivi VSTO.  
  
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
  
## <a name="elements-and-attributes"></a>Elementi e attributi  
 Il **appAddin** elemento è obbligatorio e si trova il `vstov4` dello spazio dei nomi. È presente una sola **appAddin** elemento definito in un manifesto dell'applicazione.  
  
 Il **appAddin** elemento presenta gli attributi seguenti.  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|**Applicazione**|Obbligatorio. Identifica l'applicazione di Microsoft Office. Il valore può essere uno dei seguenti: Excel, InfoPath, Outlook, PowerPoint, Project, Visio o Word.|  
|**loadBehavior**|Facoltativo. Per impostazione predefinita, il **loadBehavior** è abilitato impostando questo valore su. Per il debug, il componente aggiuntivo VSTO può essere disabilitato impostando il valore su due. Per altre informazioni, vedere la tabella intitolata valori di LoadBehavior in [voci del Registro di sistema per componenti aggiuntivi VSTO](../vsto/registry-entries-for-vsto-add-ins.md).|  
|**keyName**|Obbligatorio. Questo valore corrisponde al nome della chiave del Registro di sistema che verrà usata dall'applicazione per il caricamento del componente aggiuntivo VSTO. Per altre informazioni, vedere [voci del Registro di sistema per componenti aggiuntivi VSTO](../vsto/registry-entries-for-vsto-add-ins.md).|  
  
 Il **appAddin** elemento presenta gli elementi figlio seguenti.  
  
### <a name="friendlyname"></a>friendlyName  
 Facoltativo. Il **friendlyName** elemento è descritto [ &#60;friendlyName&#62; elemento &#40;sviluppo per Office in Visual Studio&#41;](../vsto/friendlyname-element-office-development-in-visual-studio.md).  
  
### <a name="description"></a>Descrizione  
 Facoltativo. Il **descrizione** elemento è descritto [ &#60;description&#62; elemento &#40;sviluppo per Office in Visual Studio&#41;](../vsto/description-element-office-development-in-visual-studio.md).  
  
### <a name="formregions"></a>formRegions  
 Obbligatorio solo per i componenti aggiuntivi VSTO di Outlook che includono aree di modulo. Il **formRegions** elemento è descritto [ &#60;formRegions&#62; elemento &#40;sviluppo per Office in Visual Studio&#41;](../vsto/formregions-element-office-development-in-visual-studio.md).  
  
## <a name="vsto-add-in-example"></a>Esempio di componente aggiuntivo VSTO  
  
### <a name="description"></a>Descrizione  
 L'esempio di codice seguente illustra **appAddin** elementi in una soluzione Outlook distribuita con [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Questo esempio di codice fa parte di un esempio più esaustivo disponibile [manifesti dell'applicazione per le soluzioni Office](../vsto/application-manifests-for-office-solutions.md).  
  
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
  
  