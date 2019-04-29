---
title: '&lt;formRegion&gt; elemento (sviluppo per Office in Visual Studio)'
titleSuffix: ''
ms.custom: seodec18
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application manifests [Office development in Visual Studio], <formRegion> element
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 33bc2ce58f90f37a1219427558a01bd13e5654df
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62414533"
---
# <a name="ltformregiongt-element-office-development-in-visual-studio"></a>&lt;formRegion&gt; elemento (sviluppo per Office in Visual Studio)
  Il `formRegion` elemento di `vstov4` dello spazio dei nomi identifica un'area del modulo Microsoft Office Outlook associata a un componente aggiuntivo VSTO.

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
 L'esempio di codice seguente illustra un elemento `formRegion` in un manifesto dell'applicazione per un componente aggiuntivo VSTO di Outlook distribuito con [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Esistono tre classi di messaggi associate a questa unica area del modulo. Questo esempio di codice è parte di un esempio più esaustivo disponibile nel [manifesti dell'applicazione per le soluzioni Office](../vsto/application-manifests-for-office-solutions.md).

```xml
<vstov4:formRegion
    name="OutlookAddIn1.FormRegion1">
  <vstov4:messageClass name="IPM.Note" />
  <vstov4:messageClass name="IPM.Contact" />
  <vstov4:messageClass name="IPM.Appointment" />
</vstov4:formRegion>
```

## <a name="see-also"></a>Vedere anche

- [Creare aree del modulo di Outlook](../vsto/creating-outlook-form-regions.md)
- [Manifesti dell'applicazione per le soluzioni Office](../vsto/application-manifests-for-office-solutions.md)
- [Manifesti della distribuzione per le soluzioni Office](../vsto/deployment-manifests-for-office-solutions.md)
- [Manifesto dell'applicazione ClickOnce](../deployment/clickonce-application-manifest.md)