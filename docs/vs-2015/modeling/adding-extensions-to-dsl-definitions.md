---
title: Aggiunta di estensioni alle definizioni DSL | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 07e133be-92ab-4936-a02b-45d2012bd0a6
caps.latest.revision: 8
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: e3b8cb28edb6959511a0cfdf157e323d6706e5f6
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47526068"
---
# <a name="adding-extensions-to-dsl-definitions"></a>Aggiunta di estensioni alle definizioni DSL
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [aggiunta di estensioni alle definizioni DSL](https://docs.microsoft.com/visualstudio/modeling/adding-extensions-to-dsl-definitions).  
  
Estensione di definizione DSL consente di creare un pacchetto di estensioni da un linguaggio specifico di dominio (DSL). L'estensione del linguaggio DSL, incluso in Visual Studio Integration Extension (VSIX), può essere installato nel computer dell'utente nello stesso modo come un linguaggio DSL. Le funzionalità aggiuntive possono essere abilitate e disabilitate in fase di esecuzione in modo dinamico. Linguaggi specifici di dominio non devono essere progettate in modo esplicito per l'estensione e le estensioni possono essere progettate in un secondo momento o da terze parti senza alterare il DSL esteso.  
  
 Le funzionalità aggiuntive possono includere quanto segue:  
  
-   Proprietà degli elementi di modello e la presentazione  
  
-   Elementi Decorator per forme e connettori  
  
-   Le classi, le relazioni, forme e connettori  
  
-   Vincoli di convalida  
  
-   Schede ed elementi della casella degli strumenti  
  
 Un utente di un DSL estesa può creare e salvare un modello che contiene le istanze delle funzionalità aggiuntive e possono essere letti da altri utenti che hanno installato l'estensione corretta. Gli utenti che non hanno installato l'estensione non è possibile usare le funzionalità aggiuntive, ma possono aggiornare e salvare un modello senza perdere le funzionalità aggiuntive.  
  
 Per codice di esempio e altre informazioni su questa funzionalità, vedere la [Visual Studio Visualization and Modeling SDK](http://go.microsoft.com/fwlink/?LinkID=186128) sito Web.  
  
## <a name="see-also"></a>Vedere anche  
 [Visual Studio Visualization and Modeling SDK](http://go.microsoft.com/fwlink/?LinkID=186128)



