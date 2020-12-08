---
title: '&lt;elemento customizations &gt; (sviluppo per Office in Visual Studio)'
description: Informazioni su come l'elemento customizations dello spazio dei nomi vstov4 contiene tutte le informazioni sull'installazione e sul caricamento di ogni soluzione Office.
titleSuffix: ''
ms.custom: seodec18, SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- <customizations> element
- customizations element
- application manifests [Office development in Visual Studio], <customizations> element
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: cc1f33101346d334d08d2bd2d7795961ea33011e
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/08/2020
ms.locfileid: "96844036"
---
# <a name="ltcustomizationsgt-element-office-development-in-visual-studio"></a>&lt;elemento customizations &gt; (sviluppo per Office in Visual Studio)
  L'elemento `customizations` dello spazio dei nomi `vstov4` contiene tutte le informazioni sull'installazione e sul caricamento di ogni soluzione Office.

## <a name="syntax-for-document-level-customizations"></a>Sintassi per le personalizzazioni a livello di documento

```xml
<customizations>
  <customization
    id
    <document
      solutionId
    />
  </customization>
</customizations>
```

## <a name="syntax-for-vsto-add-ins"></a>Sintassi per i componenti aggiuntivi VSTO

```xml
<customizations>
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
</customizations>
```

## <a name="elements-and-attributes"></a>Elementi e attributi
 L'elemento `customizations` contiene informazioni specifiche su ogni soluzione Office. Questo elemento deve essere presente nello spazio dei nomi seguente: `vstov4=urn:schemas-microsoft-com:vsto.v4`. In questo spazio dei nomi devono essere inclusi anche gli elementi figlio dell'assembly.

 L'elemento `customizations` non ha attributi.

 L'elemento `customizations` ha l'elemento figlio seguente.

### <a name="customization"></a>Personalizzazione
 Obbligatorio. L' `customization` elemento nello `vstov4` spazio dei nomi è definito in [&#60;elemento&#62; di personalizzazione &#40;sviluppo per Office in Visual Studio&#41;](../vsto/customization-element-office-development-in-visual-studio.md).

## <a name="example-of-a-document-level-customization"></a>Esempio di personalizzazione a livello di documento

### <a name="description"></a>Descrizione
 L'esempio di codice seguente illustra l'elemento `customizations` per una personalizzazione a livello di documento.

> [!NOTE]
> Questo esempio di codice fa parte di un esempio più ampio fornito nei [manifesti dell'applicazione per le soluzioni Office](../vsto/application-manifests-for-office-solutions.md).

### <a name="code"></a>Codice

```xml
<vstov4:customizations
  xmlns:vstov4="urn:schemas-microsoft-com:vsto.v4">
  <vstov4:customization>
    <vstov4:document
      solutionId="73e" />
  </vstov4:customization>
</vstov4:customizations>
```

## <a name="example-of-a-vsto-add-in"></a>Esempio di componente aggiuntivo VSTO

### <a name="description"></a>Descrizione
 L'esempio di codice seguente illustra l' `customizations` elemento per un componente aggiuntivo VSTO. Si tratta di un componente aggiuntivo VSTO per Outlook che include aree del modulo. Questo esempio di codice fa parte di un esempio più ampio fornito nei [manifesti dell'applicazione per le soluzioni Office](../vsto/application-manifests-for-office-solutions.md).

### <a name="code"></a>Codice

```xml
<vstov4:customizations
  xmlns:vstov4="urn:schemas-microsoft-com:vsto.v4">
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
</vstov4:customizations>
```

## <a name="see-also"></a>Vedi anche

- [Manifesti dell'applicazione per le soluzioni Office](../vsto/application-manifests-for-office-solutions.md)
- [Manifesti della distribuzione per le soluzioni Office](../vsto/deployment-manifests-for-office-solutions.md)
- [Manifesto dell'applicazione ClickOnce](../deployment/clickonce-application-manifest.md)