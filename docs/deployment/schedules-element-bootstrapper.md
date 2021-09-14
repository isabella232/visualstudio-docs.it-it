---
title: '&lt;Elemento &gt; Schedules (programma di avvio automatico) | Microsoft Docs'
description: L'elemento Schedules contiene gli elementi Schedule, che definiscono orari specifici in cui devono essere eseguiti i comandi definiti dall'elemento Command.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- <Schedules> element [bootstrapper]
ms.assetid: 28d094cf-64f5-42b1-bd8a-3697082aab4f
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-deployment
ms.workload:
- multiple
ms.openlocfilehash: 8f9430dd814ba76f0a8e688d6a198c8715fc4d99
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126627744"
---
# <a name="ltschedulesgt-element-bootstrapper"></a>&lt;Elemento Schedules &gt; (programma di avvio automatico)
`Schedules`L'elemento contiene elementi che definiscono orari specifici in cui devono essere eseguiti i comandi definiti `Schedule` `Command` dall'elemento .

## <a name="syntax"></a>Sintassi

```xml
<Schedules>
    <Schedule
        Name
    >
        <BuildList />
        <BeforePackage />
        <AfterPackage />
    </Schedule>
</Schedules>
```

## <a name="elements-and-attributes"></a>Elementi e attributi
 `Schedules`L'elemento è figlio `Product` dell'elemento . Ogni `Product` elemento può avere al massimo un elemento `Schedules` . L'elemento `Schedules` non ha attributi.

## <a name="schedule"></a>Pianifica
 `Schedule`L'elemento è figlio `Schedules` dell'elemento . Un `Schedules` elemento deve avere almeno un elemento `Schedule` .

 `Schedule` ha l'attributo seguente.

|Attributo|Descrizione|
|---------------|-----------------|
|`Name`|Obbligatorio. Nome dell'elemento di pianificazione. Corrisponde alla proprietà `ScheduleName` `Command` dell'elemento . Quando un `Command` oggetto fa riferimento alla pianificazione denominata, verrà eseguita solo all'ora indicata dall'elemento. `Schedule` Le pianificazioni possono anche essere associate agli elementi e , che limitano questi `FailIf` `BypassIf` test condizionali all'esecuzione in base alla pianificazione specificata. Per altre informazioni, vedere [ \<Commands> Elemento](../deployment/commands-element-bootstrapper.md).|

 Un determinato `Schedule` elemento può avere esattamente uno degli elementi figlio seguenti.

## <a name="buildlist"></a>BuildList
 `BuildList`L'elemento indica al programma di installazione di eseguire un comando immediatamente dopo l'avvio dell'applicazione di bootstrap.

## <a name="beforepackage"></a>BeforePackage
 `BeforePackage`L'elemento indica al programma di installazione di eseguire un comando prima dell'installazione del pacchetto specificato.

## <a name="afterpackage"></a>AfterPackage
 `AfterPackage`L'elemento indica al programma di installazione di eseguire un comando dopo l'installazione del pacchetto specificato.

## <a name="see-also"></a>Vedi anche
- [\<Product> Elemento](../deployment/product-element-bootstrapper.md)
- [Informazioni di riferimento sullo schema di prodotti e pacchetti](../deployment/product-and-package-schema-reference.md)