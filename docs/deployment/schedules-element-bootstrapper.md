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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 850c94274f783c306fe31fde4d86c9563c928adf
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53894298"
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
  
|Attributo|Description|  
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