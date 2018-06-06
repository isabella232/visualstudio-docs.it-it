---
title: '&lt;Le pianificazioni&gt; elemento (programma di avvio automatico) | Documenti Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
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
ms.openlocfilehash: 9c551bc9335dc41f82800e2c3435d8508967a6db
ms.sourcegitcommit: 1b9c1e333c2f096d35cfc77e846116f8e5054557
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/06/2018
ms.locfileid: "34815470"
---
# <a name="ltschedulesgt-element-bootstrapper"></a>&lt;Le pianificazioni&gt; elemento (programma di avvio automatico)
Il `Schedules` elemento contiene `Schedule` elementi che definiscono l'ora specifica a quali comandi definiti per il `Command` elemento deve essere eseguito.  
  
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
 Il `Schedules` è un elemento figlio del `Product` elemento. Ogni `Product` elemento può contenere al massimo una `Schedules` elemento. Il `Schedules` elemento non ha attributi.  
  
## <a name="schedule"></a>Pianificazione  
 Il `Schedule` è un elemento figlio del `Schedules` elemento. Oggetto `Schedules` l'elemento deve avere almeno un `Schedule` elemento.  
  
 `Schedule` presenta l'attributo seguente.  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|`Name`|Obbligatorio. Il nome dell'elemento di pianificazione. Corrisponde alla `ScheduleName` proprietà del `Command` elemento. Quando un `Command` fa riferimento alla pianificazione specificata, verrà eseguito solo nell'orario indicato da tale `Schedule` elemento. Le pianificazioni possono anche essere associate le `FailIf` e `BypassIf` elementi, che limitano l'esecuzione in base alla pianificazione specificata questi test condizionale. Per ulteriori informazioni, vedere [ \<comandi > elemento](../deployment/commands-element-bootstrapper.md).|  
  
 Un determinato `Schedule` elemento può avere esattamente uno degli elementi figlio seguenti.  
  
## <a name="buildlist"></a>BuildList  
 Il `BuildList` elemento indica al programma di installazione per eseguire un comando, subito dopo l'avvio di applicazione di avvio automatico.  
  
## <a name="beforepackage"></a>BeforePackage  
 Il `BeforePackage` elemento indica al programma di installazione per eseguire un comando prima di installata il pacchetto specificato.  
  
## <a name="afterpackage"></a>AfterPackage  
 Il `AfterPackage` elemento indica al programma di installazione per eseguire un comando, dopo aver installato il pacchetto specificato.  
  
## <a name="see-also"></a>Vedere anche  
 [\<Prodotto > elemento](../deployment/product-element-bootstrapper.md)   
 [Riferimenti dello schema di prodotti e package](../deployment/product-and-package-schema-reference.md)