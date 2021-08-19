---
description: L'elemento formRegion dello spazio dei nomi vstov4 identifica un'area Microsoft Office Outlook del modulo associata a un VSTO componente aggiuntivo.
title: '&lt;Elemento &gt; formRegion (Office sviluppo in Visual Studio)'
titleSuffix: ''
ms.custom: seodec18
ms.date: 02/02/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application manifests [Office development in Visual Studio], <formRegion> element
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: f78e6867afd4839dab329a9543fafe4015bf777f
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122156019"
---
# <a name="ltformregiongt-element-office-development-in-visual-studio"></a>&lt;Elemento &gt; formRegion (Office sviluppo in Visual Studio)
  L'elemento dello spazio dei nomi identifica Microsoft Office Outlook'area del modulo associata a un `formRegion` VSTO componente `vstov4` aggiuntivo.

## <a name="syntax"></a>Sintassi

```xml
<formRegion
  name>
  <messageClass
    name/>
</formRegion>
```

## <a name="elements-and-attributes"></a>Elementi e attributi
 L'elemento `formRegion` dello spazio dei nomi `vstov4` identifica un'area del modulo associata a un componente aggiuntivo VSTO di Outlook. È obbligatorio solo per i componenti aggiuntivi VSTO di Outlook che includono aree del modulo.

 Possono esserci più elementi `formRegion` definiti all'interno di un elemento `formRegions` per un componente aggiuntivo VSTO singolo.

 L'elemento `formRegion` presenta l'attributo seguente:

|Attributo|Descrizione|
|---------------|-----------------|
|`name`|Obbligatorio. Identifica il nome dell'area del modulo.|

 L'elemento `formRegion` ha gli elementi figlio seguenti.

### <a name="messageclass"></a>messageClass
 L'elemento `messageClass` identifica il modulo di Outlook associato all'area del modulo.

 L'elemento `messageClass` presenta l'attributo seguente:

|Attributo|Descrizione|
|---------------|-----------------|
|`name`|Obbligatorio. Identifica il modulo associato all'area del modulo.|

## <a name="example"></a>Esempio
 L'esempio di codice seguente illustra un elemento `formRegion` in un manifesto dell'applicazione per un componente aggiuntivo VSTO di Outlook distribuito con [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Esistono tre classi di messaggi associate a questa unica area del modulo. Questo esempio di codice fa parte di un esempio più ampio fornito nei [manifesti dell'applicazione per Office soluzioni](../vsto/application-manifests-for-office-solutions.md).

```xml
<vstov4:formRegion
    name="OutlookAddIn1.FormRegion1">
  <vstov4:messageClass name="IPM.Note" />
  <vstov4:messageClass name="IPM.Contact" />
  <vstov4:messageClass name="IPM.Appointment" />
</vstov4:formRegion>
```

## <a name="see-also"></a>Vedi anche

- [Creare aree Outlook modulo](../vsto/creating-outlook-form-regions.md)
- [Manifesti dell'applicazione per Office soluzioni](../vsto/application-manifests-for-office-solutions.md)
- [Manifesti di distribuzione per Office soluzioni](../vsto/deployment-manifests-for-office-solutions.md)
- [ClickOnce manifesto dell'applicazione](../deployment/clickonce-application-manifest.md)
