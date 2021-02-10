---
title: '&lt;&gt;elemento formRegions (sviluppo per Office in Visual Studio)'
titleSuffix: ''
ms.custom: seodec18
ms.date: 02/02/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- formRegions element
- <formRegions> element
- application manifests [Office development in Visual Studio], <formRegions> element
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: a1a718c6a247528788d91e9c1f30ad636acb7ab9
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99970335"
---
# <a name="ltformregionsgt-element-office-development-in-visual-studio"></a>&lt;&gt;elemento formRegions (sviluppo per Office in Visual Studio)
  L' `formRegions` elemento dello `vstov4` spazio dei nomi contiene le aree del modulo di Microsoft Office Outlook associate a un componente aggiuntivo VSTO.

## <a name="syntax"></a>Sintassi

```xml
<formRegions>
  <formRegion>
  </formRegion>
</formRegions>
```

## <a name="elements-and-attributes"></a>Elementi e attributi
 L'elemento `formRegions` dello spazio dei nomi `vstov4` contiene tutti gli elementi `formRegion` per un componente aggiuntivo VSTO di Outlook. È obbligatorio solo per i componenti aggiuntivi VSTO di Outlook che includono aree del modulo.

 Può essere definito un solo elemento `formRegions` in un manifesto dell'applicazione.

 L'elemento `formRegions` non ha attributi.

 L'elemento `formRegions` presenta l'elemento seguente.

### <a name="formregion"></a>formRegion
 Obbligatorio per i componenti aggiuntivi VSTO di Outlook che includono aree del modulo. L' `formRegion` elemento è definito in [&#60;elemento&#62; FormRegion &#40;sviluppo per Office in Visual Studio&#41;](../vsto/formregion-element-office-development-in-visual-studio.md).

## <a name="vsto-add-in-example"></a>Esempio di componente aggiuntivo VSTO

### <a name="description"></a>Descrizione
 L'esempio di codice seguente illustra un elemento `formRegions` in un manifesto dell'applicazione per una soluzione Office a livello di applicazione distribuita con [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Questo esempio di codice fa parte di un esempio più ampio fornito nei [manifesti dell'applicazione per le soluzioni Office](../vsto/application-manifests-for-office-solutions.md).

### <a name="code"></a>Codice

```xml
<vstov4:formRegions>
  <vstov4:formRegion
      name="OutlookAddIn1.FormRegion1">
    <vstov4:messageClass name="IPM.Note" />
    <vstov4:messageClass name="IPM.Contact" />
    <vstov4:messageClass name="IPM.Appointment" />
  </vstov4:formRegion>
</vstov4:formRegions>
```

## <a name="see-also"></a>Vedi anche

- [Manifesti dell'applicazione per le soluzioni Office](../vsto/application-manifests-for-office-solutions.md)
- [Manifesti della distribuzione per le soluzioni Office](../vsto/deployment-manifests-for-office-solutions.md)
- [Manifesto dell'applicazione ClickOnce](../deployment/clickonce-application-manifest.md)