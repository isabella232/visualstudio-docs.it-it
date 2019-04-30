---
title: '&lt;le personalizzazioni&gt; elemento (sviluppo per Office in Visual Studio)'
titleSuffix: ''
ms.custom: seodec18
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
ms.openlocfilehash: 58d88f865e5f220000bf021b548e4b9c4b8745f6
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63445501"
---
# <a name="ltcustomizationsgt-element-office-development-in-visual-studio"></a>&lt;le personalizzazioni&gt; elemento (sviluppo per Office in Visual Studio)
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
 Obbligatorio. Il `customization` elemento il `vstov4` dello spazio dei nomi definito in [ &#60;personalizzazione&#62; elemento &#40;sviluppo per Office in Visual Studio&#41;](../vsto/customization-element-office-development-in-visual-studio.md).

## <a name="example-of-a-document-level-customization"></a>Esempio di una personalizzazione a livello di documento

### <a name="description"></a>Descrizione
 L'esempio di codice seguente illustra l'elemento `customizations` per una personalizzazione a livello di documento.

> [!NOTE]
> Questo esempio di codice è parte di un esempio più esaustivo disponibile nel [manifesti dell'applicazione per le soluzioni Office](../vsto/application-manifests-for-office-solutions.md).

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

## <a name="example-of-a-vsto-add-in"></a>Esempio di un componente aggiuntivo VSTO

### <a name="description"></a>Descrizione
 L'esempio di codice seguente illustra il `customizations` (elemento) per un componente aggiuntivo VSTO. Si tratta di un componente aggiuntivo VSTO per Outlook che include aree del modulo. Questo esempio di codice è parte di un esempio più esaustivo disponibile nel [manifesti dell'applicazione per le soluzioni Office](../vsto/application-manifests-for-office-solutions.md).

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

## <a name="see-also"></a>Vedere anche

- [Manifesti dell'applicazione per le soluzioni Office](../vsto/application-manifests-for-office-solutions.md)
- [Manifesti della distribuzione per le soluzioni Office](../vsto/deployment-manifests-for-office-solutions.md)
- [Manifesto dell'applicazione ClickOnce](../deployment/clickonce-application-manifest.md)