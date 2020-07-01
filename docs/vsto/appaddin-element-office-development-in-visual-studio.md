---
title: '&lt;&gt;elemento appAddin (sviluppo per Office in Visual Studio)'
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 1bf9ea990d12bd24adee3f6a24a39fa43c74fb71
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/30/2020
ms.locfileid: "85531638"
---
# <a name="ltappaddingt-element-office-development-in-visual-studio"></a>&lt;&gt;elemento appAddin (sviluppo per Office in Visual Studio)
  L'elemento **appAddin** dello `vstov4` spazio dei nomi archivia informazioni specifiche della personalizzazione per i componenti aggiuntivi VSTO.

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
 L'elemento **appAddin** è obbligatorio e si trova nello `vstov4` spazio dei nomi. È presente un solo elemento **appAddin** definito in un manifesto dell'applicazione.

 L'elemento **appAddin** ha gli attributi seguenti.

|Attributo|Descrizione|
|---------------|-----------------|
|**applicazione**|Obbligatorio. Identifica l'applicazione di Microsoft Office. Il valore può essere uno dei seguenti: Excel, InfoPath, Outlook, PowerPoint, Project, Visio o Word.|
|**loadBehavior**|Facoltativa. Per impostazione predefinita, **LoadBehavior** viene abilitato impostando questo valore su. Per il debug, il componente aggiuntivo VSTO può essere disabilitato impostando il valore su due. Per altre informazioni, vedere la tabella intitolata LoadBehavior values in [Registry Entries for VSTO Add-ins](../vsto/registry-entries-for-vsto-add-ins.md).|
|**keyName**|Obbligatorio. Questo valore corrisponde al nome della chiave del Registro di sistema che verrà usata dall'applicazione per il caricamento del componente aggiuntivo VSTO. Per altre informazioni, vedere [voci del registro di sistema per i componenti aggiuntivi VSTO](../vsto/registry-entries-for-vsto-add-ins.md).|

 L'elemento **appAddin** ha gli elementi figlio seguenti.

### <a name="friendlyname"></a>friendlyName
 Facoltativa. L'elemento **FriendlyName** è illustrato nell' [elemento&#60;friendlyname&#62; &#40;sviluppo per Office in Visual Studio&#41;](../vsto/friendlyname-element-office-development-in-visual-studio.md).

### <a name="description"></a>description
 Facoltativa. L'elemento **Description** è illustrato in [&#60;description&#62; elemento &#40;sviluppo per Office in Visual Studio&#41;](../vsto/description-element-office-development-in-visual-studio.md).

### <a name="formregions"></a>formRegions
 Obbligatorio solo per i componenti aggiuntivi VSTO di Outlook che includono aree di modulo. L'elemento **formRegions** è illustrato in [&#60;elemento formRegions&#62; &#40;sviluppo per Office in Visual Studio&#41;](../vsto/formregions-element-office-development-in-visual-studio.md).

## <a name="vsto-add-in-example"></a>Esempio di componente aggiuntivo VSTO

### <a name="description"></a>Descrizione
 Nell'esempio di codice seguente vengono illustrati gli elementi **appAddin** in una soluzione Outlook distribuita con [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] . Questo esempio di codice fa parte di un esempio più ampio fornito nei [manifesti dell'applicazione per le soluzioni Office](../vsto/application-manifests-for-office-solutions.md).

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

- [Manifesti dell'applicazione per le soluzioni Office](../vsto/application-manifests-for-office-solutions.md)
- [Manifesti della distribuzione per le soluzioni Office](../vsto/deployment-manifests-for-office-solutions.md)
- [Manifesto dell'applicazione ClickOnce](../deployment/clickonce-application-manifest.md)