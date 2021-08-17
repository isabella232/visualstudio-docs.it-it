---
title: '&lt;Elemento customization &gt; (Office sviluppo in Visual Studio)'
description: Informazioni su come l'elemento di personalizzazione dello spazio dei nomi vstov4 descrive una soluzione Office specifica.
titleSuffix: ''
ms.custom: seodec18, SEO-VS-2020
ms.date: 02/02/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application manifests [Office development in Visual Studio], <customization> element
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 2a2744e82fc1012e40257cb23371584eb7792aea9b24562ff1de9e66acbee1a9
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121394784"
---
# <a name="ltcustomizationgt-element-office-development-in-visual-studio"></a>&lt;Elemento customization &gt; (Office sviluppo in Visual Studio)
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

### <a name="document-level-customizations"></a>Document-Level personalizzazioni
 L'elemento `customization` ha l'elemento figlio seguente.

#### <a name="document"></a>documento
 L'elemento nello spazio dei nomi è definito&#60;documento&#62; di &#40;Office `document` `vstov4` sviluppo in [Visual Studio&#41;](../vsto/document-element-office-development-in-visual-studio.md).

### <a name="vsto-add-ins"></a>Componenti aggiuntivi VSTO
 L'elemento `customization` ha l'elemento figlio seguente.

#### <a name="appaddin"></a>appAddin
 L'elemento nello spazio dei nomi `appAddin` è definito in&#60;`vstov4` [appAddin&#62;'elemento &#40;Office sviluppo in Visual Studio&#41;](../vsto/appaddin-element-office-development-in-visual-studio.md).

## <a name="example-of-a-document-level-customization"></a>Esempio di personalizzazione a livello di documento

### <a name="description"></a>Descrizione
 L'esempio di codice seguente illustra l'elemento `customization` per una personalizzazione a livello di documento. Questo esempio di codice fa parte di un esempio più ampio fornito nei [manifesti dell'applicazione per Office soluzioni](../vsto/application-manifests-for-office-solutions.md).

### <a name="code"></a>Codice

```xml
<vstov4:customization>
  <vstov4:document
    solutionId="73e" />
</vstov4:customization>
```

## <a name="example-of-a-vsto-add-in"></a>Esempio di VSTO componente aggiuntivo

### <a name="description"></a>Descrizione
 L'esempio di codice seguente illustra `customization` l'elemento per un VSTO componente aggiuntivo. Si tratta di un componente aggiuntivo VSTO per Outlook che include aree del modulo. Questo esempio di codice fa parte di un esempio più ampio fornito nei [manifesti dell'applicazione per Office soluzioni](../vsto/application-manifests-for-office-solutions.md).

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

## <a name="see-also"></a>Vedi anche

- [Manifesti dell'applicazione per Office soluzioni](../vsto/application-manifests-for-office-solutions.md)
- [Manifesti di distribuzione per Office soluzioni](../vsto/deployment-manifests-for-office-solutions.md)
- [ClickOnce manifesto dell'applicazione](../deployment/clickonce-application-manifest.md)