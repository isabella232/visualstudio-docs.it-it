---
title: '&lt;Elemento Schedules (programma di &gt; avvio automatico) | Microsoft Docs'
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a2f6e4ae90dbd36dab4f4df7f72d5ecf57ee04b1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "62927332"
---
# <a name="ltschedulesgt-element-bootstrapper"></a>&lt;Elemento Schedules (programma di &gt; avvio automatico)
L' `Schedules` elemento contiene `Schedule` elementi che definiscono orari specifici in cui devono essere eseguiti i comandi definiti dall' `Command` elemento.

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
 L' `Schedules` elemento è un elemento figlio dell' `Product` elemento. Ogni `Product` elemento può contenere al massimo un `Schedules` elemento. L'elemento `Schedules` non ha attributi.

## <a name="schedule"></a>Pianifica
 L' `Schedule` elemento è un elemento figlio dell' `Schedules` elemento. Un `Schedules` elemento deve contenere almeno un `Schedule` elemento.

 `Schedule` ha l'attributo seguente.

|Attributo|Descrizione|
|---------------|-----------------|
|`Name`|Obbligatorio. Nome dell'elemento di pianificazione. Corrisponde alla `ScheduleName` proprietà dell' `Command` elemento. Quando un oggetto `Command` fa riferimento alla pianificazione denominata, viene eseguita solo nel momento indicato da tale `Schedule` elemento. Le pianificazioni possono anche essere associate agli `FailIf` `BypassIf` elementi e, che limitano l'esecuzione di questi test condizionali alla pianificazione specificata. Per ulteriori informazioni, vedere [ \<Commands> elemento](../deployment/commands-element-bootstrapper.md).|

 Un dato `Schedule` elemento può avere esattamente uno dei seguenti elementi figlio.

## <a name="buildlist"></a>BuildList
 L' `BuildList` elemento indica al programma di installazione di eseguire un comando immediatamente dopo l'avvio dell'applicazione.

## <a name="beforepackage"></a>BeforePackage
 L' `BeforePackage` elemento indica al programma di installazione di eseguire un comando prima di installare il pacchetto specificato.

## <a name="afterpackage"></a>AfterPackage
 L' `AfterPackage` elemento indica al programma di installazione di eseguire un comando dopo l'installazione del pacchetto specificato.

## <a name="see-also"></a>Vedere anche
- [\<Product> elemento](../deployment/product-element-bootstrapper.md)
- [Riferimento allo schema del prodotto e del pacchetto](../deployment/product-and-package-schema-reference.md)