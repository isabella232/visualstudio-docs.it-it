---
title: '&lt;Elemento appAddin &gt; (Office sviluppo in Visual Studio)'
description: Informazioni su come l'elemento appAddin dello spazio dei nomi vstov4 archivia le informazioni specifiche della personalizzazione VSTO componenti aggiuntivi.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application manifests [Office development in Visual Studio], <appAddin> element
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 3ccde6860ac1ef0935346669b20c07e8c434549bc0b878a1b801b3153fe38168
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121440890"
---
# <a name="ltappaddingt-element-office-development-in-visual-studio"></a>&lt;Elemento appAddin &gt; (Office sviluppo in Visual Studio)
  **L'elemento appAddin** dello spazio dei nomi archivia le informazioni specifiche della `vstov4` personalizzazione VSTO componenti aggiuntivi.

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
 **L'elemento appAddin** è obbligatorio e si trova nello spazio dei `vstov4` nomi . In un manifesto dell'applicazione è definito un solo elemento **appAddin.**

 **L'elemento appAddin** ha gli attributi seguenti.

|Attributo|Descrizione|
|---------------|-----------------|
|**applicazione**|Obbligatorio. Identifica l'applicazione di Microsoft Office. Il valore può essere uno dei seguenti: Excel, InfoPath, Outlook, PowerPoint, Project, Visio o Word.|
|**Loadbehavior**|facoltativo. Per impostazione predefinita, **loadBehavior** viene abilitato impostando questo valore su . Per il debug, il componente aggiuntivo VSTO può essere disabilitato impostando il valore su due. Per altre informazioni, vedere la tabella intitolata LoadBehavior Values in [Registry entries for VSTO Add-ins](../vsto/registry-entries-for-vsto-add-ins.md).|
|**Keyname**|Obbligatorio. Questo valore corrisponde al nome della chiave del Registro di sistema che verrà usata dall'applicazione per il caricamento del componente aggiuntivo VSTO. Per altre informazioni, vedere [Voci del Registro di sistema VSTO componenti aggiuntivi](../vsto/registry-entries-for-vsto-add-ins.md).|

 **L'elemento appAddin** ha gli elementi figlio seguenti.

### <a name="friendlyname"></a>friendlyName
 facoltativo. **L'elemento friendlyName** è illustrato in [&#60;elemento friendlyName&#62; lo &#40;Office sviluppo in Visual Studio&#41;](../vsto/friendlyname-element-office-development-in-visual-studio.md).

### <a name="description"></a>description
 facoltativo. **L'elemento description** è illustrato nella [&#60;descrizione&#62;'elemento &#40;Office sviluppo in Visual Studio&#41;](../vsto/description-element-office-development-in-visual-studio.md).

### <a name="formregions"></a>formRegions
 Obbligatorio solo per i componenti aggiuntivi VSTO di Outlook che includono aree di modulo. **L'elemento formRegions** è illustrato&#60;[formRegions&#62;'elemento &#40;Office sviluppo in Visual Studio&#41;](../vsto/formregions-element-office-development-in-visual-studio.md).

## <a name="vsto-add-in-example"></a>VSTO Esempio di componente aggiuntivo

### <a name="description"></a>Descrizione
 L'esempio di codice seguente illustra **gli elementi appAddin** in una Outlook distribuita tramite [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] . Questo esempio di codice fa parte di un esempio più ampio fornito in [Manifesti dell'applicazione per Office soluzioni](../vsto/application-manifests-for-office-solutions.md).

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

## <a name="see-also"></a>Vedi anche

- [Manifesti dell'applicazione per Office soluzioni](../vsto/application-manifests-for-office-solutions.md)
- [Manifesti di distribuzione per Office soluzioni](../vsto/deployment-manifests-for-office-solutions.md)
- [ClickOnce manifesto dell'applicazione](../deployment/clickonce-application-manifest.md)