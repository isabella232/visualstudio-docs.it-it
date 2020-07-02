---
title: '&lt;&gt;elemento customization (sviluppo per Office in Visual Studio)'
titleSuffix: ''
ms.custom: seodec18
ms.date: 02/02/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application manifests [Office development in Visual Studio], <customization> element
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 1239c6749f25bf4bce7a1f5cc89a2a8430c98a4d
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/30/2020
ms.locfileid: "85544872"
---
# <a name="ltcustomizationgt-element-office-development-in-visual-studio"></a>&lt;&gt;elemento customization (sviluppo per Office in Visual Studio)
  L'elemento `customization` dello spazio dei nomi `vstov4` descrive una specifica soluzione Office. Gli elementi figlio sono diversi per le personalizzazioni a livello di documento e i componenti aggiuntivi VSTO.

## <a name="syntax-for-document-level-customizations"></a>Sintassi per le personalizzazioni a livello di documento

```xml
<customization
  id
  <document
    solutionId
  />
</customization>
```

## <a name="syntax-for-vsto-add-ins"></a>Sintassi per i componenti aggiuntivi VSTO

```xml
<customization
  id
  <appAddin
    application
    loadBehavior
    keyName>
  <friendlyName></friendlyName>
  <description></description>
  <formRegions></formRegions>
</customization>
```

## <a name="elements-and-attributes"></a>Elementi e attributi
 L'elemento `customization` contiene informazioni specifiche della personalizzazione. Questo elemento deve essere presente nello spazio dei nomi seguente: `vstov4=urn:schemas-microsoft-com:vsto.v4`. Esiste un elemento `customization` per ogni soluzione Office. Ad esempio, se si distribuiscono tre soluzioni Office in una distribuzione multiprogetto, nel manifesto dell'applicazione sono presenti tre elementi `customization` .

 In questo spazio dei nomi devono essere inclusi anche gli elementi figlio dell'assembly.

 L'elemento `customization` presenta l'attributo seguente:

|Attributo|Descrizione|
|---------------|-----------------|
|`id`|Necessario per la distribuzione multiprogetto. L'elemento `id` identifica in modo univoco una soluzione Office.|

### <a name="document-level-customizations"></a>Personalizzazioni a livello di documento
 L'elemento `customization` ha l'elemento figlio seguente.

#### <a name="document"></a>documento
 L' `document` elemento nello `vstov4` spazio dei nomi è definito in [&#60;elemento&#62; documento &#40;sviluppo per Office in Visual Studio&#41;](../vsto/document-element-office-development-in-visual-studio.md).

### <a name="vsto-add-ins"></a>Componenti aggiuntivi VSTO
 L'elemento `customization` ha l'elemento figlio seguente.

#### <a name="appaddin"></a>appAddin
 L' `appAddin` elemento nello `vstov4` spazio dei nomi è definito in [&#60;elemento appAddin&#62; &#40;sviluppo per Office in Visual Studio&#41;](../vsto/appaddin-element-office-development-in-visual-studio.md).

## <a name="example-of-a-document-level-customization"></a>Esempio di personalizzazione a livello di documento

### <a name="description"></a>Descrizione
 L'esempio di codice seguente illustra l'elemento `customization` per una personalizzazione a livello di documento. Questo esempio di codice fa parte di un esempio più ampio fornito nei [manifesti dell'applicazione per le soluzioni Office](../vsto/application-manifests-for-office-solutions.md).

### <a name="code"></a>Codice

```xml
<vstov4:customization>
  <vstov4:document
    solutionId="73e" />
</vstov4:customization>
```

## <a name="example-of-a-vsto-add-in"></a>Esempio di componente aggiuntivo VSTO

### <a name="description"></a>Descrizione
 L'esempio di codice seguente illustra l' `customization` elemento per un componente aggiuntivo VSTO. Si tratta di un componente aggiuntivo VSTO per Outlook che include aree del modulo. Questo esempio di codice fa parte di un esempio più ampio fornito nei [manifesti dell'applicazione per le soluzioni Office](../vsto/application-manifests-for-office-solutions.md).

### <a name="code"></a>Codice

```xml
<vstov4:customization>
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
</vstov4:customization>
```

## <a name="see-also"></a>Vedere anche

- [Manifesti dell'applicazione per le soluzioni Office](../vsto/application-manifests-for-office-solutions.md)
- [Manifesti della distribuzione per le soluzioni Office](../vsto/deployment-manifests-for-office-solutions.md)
- [Manifesto dell'applicazione ClickOnce](../deployment/clickonce-application-manifest.md)