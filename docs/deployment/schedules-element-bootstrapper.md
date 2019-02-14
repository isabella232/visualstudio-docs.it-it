---
title: '&lt;Le pianificazioni&gt; elemento (programma di avvio automatico) | Microsoft Docs'
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
ms.openlocfilehash: ccba6de5795dd461c2a68f6aeeb593314ceede09
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "54962482"
---
# <a name="ltschedulesgt-element-bootstrapper"></a>&lt;Le pianificazioni&gt; elemento (programma di avvio automatico)
Il `Schedules` elemento contiene `Schedule` gli elementi, che definiscono l'ora specifica a quali comandi definiti dal `Command` elemento deve essere eseguito.  
  
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
 Il `Schedules` elemento è figlio di `Product` elemento. Ciascuna `Product` potrebbe avere al massimo un elemento `Schedules` elemento. L'elemento `Schedules` non ha attributi.  
  
## <a name="schedule"></a>Pianificazione  
 Il `Schedule` elemento è figlio di `Schedules` elemento. Oggetto `Schedules` deve avere almeno un elemento `Schedule` elemento.  
  
 `Schedule` ha l'attributo seguente.  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|`Name`|Obbligatorio. Il nome dell'elemento di pianificazione. Ciò corrisponde alla `ScheduleName` proprietà del `Command` elemento. Quando un `Command` fa riferimento alla pianificazione specificata, verrà eseguito solo nell'orario indicato da tale `Schedule` elemento. Le pianificazioni inoltre possono essere associate le `FailIf` e `BypassIf` elementi, che limitano l'esecuzione in base alla pianificazione specificata questi test condizionale. Per altre informazioni, vedere [ \<comandi > elemento](../deployment/commands-element-bootstrapper.md).|  
  
 Una determinata `Schedule` elemento può avere uno dei seguenti elementi figlio.  
  
## <a name="buildlist"></a>BuildList  
 Il `BuildList` elemento indica il programma di installazione per eseguire un comando immediatamente dopo l'avvio automatico dell'applicazione viene avviata.  
  
## <a name="beforepackage"></a>BeforePackage  
 Il `BeforePackage` elemento indica il programma di installazione per eseguire un comando prima di installata il pacchetto specificato.  
  
## <a name="afterpackage"></a>AfterPackage  
 Il `AfterPackage` elemento indica il programma di installazione per eseguire un comando dopo aver installato il pacchetto specificato.  
  
## <a name="see-also"></a>Vedere anche  
 [\<Product > elemento](../deployment/product-element-bootstrapper.md)   
 [Riferimenti dello schema di prodotti e package](../deployment/product-and-package-schema-reference.md)