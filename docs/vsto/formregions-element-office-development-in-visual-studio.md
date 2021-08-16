---
description: L'elemento formRegions dello spazio dei nomi vstov4 contiene le Microsoft Office Outlook del modulo associate a un VSTO componente aggiuntivo.
title: '&lt;Elemento formRegions &gt; (Office sviluppo in Visual Studio)'
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
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: e1a4439f5c1dab78ce32c553a4bee98db6fa7da4f072152c3a046ba819222128
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121440864"
---
# <a name="ltformregionsgt-element-office-development-in-visual-studio"></a>&lt;Elemento formRegions &gt; (Office sviluppo in Visual Studio)
  L'elemento dello spazio dei nomi contiene Microsoft Office Outlook del modulo associate a un `formRegions` `vstov4` VSTO componente aggiuntivo.

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
 Obbligatorio per i componenti aggiuntivi VSTO di Outlook che includono aree del modulo. `formRegion`L'elemento è definito in&#60;[formRegion&#62;'elemento &#40;Office sviluppo in Visual Studio&#41;](../vsto/formregion-element-office-development-in-visual-studio.md).

## <a name="vsto-add-in-example"></a>VSTO Esempio di componente aggiuntivo

### <a name="description"></a>Descrizione
 L'esempio di codice seguente illustra un elemento `formRegions` in un manifesto dell'applicazione per una soluzione Office a livello di applicazione distribuita con [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Questo esempio di codice fa parte di un esempio più ampio fornito in [Manifesti dell'applicazione per Office soluzioni](../vsto/application-manifests-for-office-solutions.md).

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

- [Manifesti dell'applicazione per Office soluzioni](../vsto/application-manifests-for-office-solutions.md)
- [Manifesti di distribuzione per Office soluzioni](../vsto/deployment-manifests-for-office-solutions.md)
- [ClickOnce manifesto dell'applicazione](../deployment/clickonce-application-manifest.md)
