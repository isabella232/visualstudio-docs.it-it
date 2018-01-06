---
title: Aggiunta di estensioni a definizioni DSL | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 07e133be-92ab-4936-a02b-45d2012bd0a6
caps.latest.revision: "6"
author: alancameronwills
ms.author: awills
manager: douge
ms.workload: multiple
ms.openlocfilehash: 77a631d7f245dfe6d324e2b392349b559447212f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="adding-extensions-to-dsl-definitions"></a>Aggiunta di estensioni alle definizioni DSL
Definizione DSL estensione consente di creare un pacchetto di estensioni da un linguaggio specifico di dominio (DSL). L'estensione del linguaggio DSL, incluso in Visual Studio Integration Extension (VSIX), può essere installato nel computer dell'utente nello stesso modo come un linguaggio DSL. Le funzionalità aggiuntive possono essere abilitate e disabilitate in fase di esecuzione in modo dinamico. DSL non deve essere progettato in modo esplicito per l'estensione e le estensioni possono essere progettate in un secondo momento o da terzi senza alterare il DSL estesa.  
  
 Le funzionalità aggiuntive possono includere quanto segue:  
  
-   Proprietà degli elementi di modello e la presentazione  
  
-   Elementi Decorator di forme e connettori  
  
-   Classi, le relazioni, forme e connettori  
  
-   Vincoli di convalida  
  
-   Schede e gli elementi della casella degli strumenti  
  
 Un utente di un'estesa DSL può creare e salvare un modello che contiene le istanze di funzionalità aggiuntive, e questi possono essere letti da altri utenti che hanno installato l'estensione appropriata. Gli utenti che non hanno installato l'estensione non è possibile utilizzare le funzionalità aggiuntive, ma possono aggiornare e salvare un modello senza perdere le funzionalità aggiuntive.  

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

## <a name="see-also"></a>Vedere anche  
 [Post di blog correlati](https://blogs.msdn.microsoft.com/visualstudioalm/tag/code-index/)
