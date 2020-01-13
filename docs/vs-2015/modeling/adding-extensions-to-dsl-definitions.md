---
title: Aggiunta di estensioni alle definizioni DSL | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: 07e133be-92ab-4936-a02b-45d2012bd0a6
caps.latest.revision: 8
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 5fab56a7738ed7b52760cf20a5bfcc8542ee5a23
ms.sourcegitcommit: 939407118f978162a590379997cb33076c57a707
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/13/2020
ms.locfileid: "75919065"
---
# <a name="adding-extensions-to-dsl-definitions"></a>Aggiunta di estensioni alle definizioni DSL
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

L'estensione di definizione DSL consente di creare un pacchetto di estensioni a un linguaggio specifico di dominio (DSL). L'estensione DSL, che è contenuta in un progetto VSIX (Visual Studio Integration Extension), può essere installata nel computer di un utente in modo analogo a un linguaggio DSL. Le funzionalità aggiuntive possono essere abilitate e disabilitate in modo dinamico in fase di esecuzione. DSLs non devono essere progettati in modo esplicito per l'estensione e le estensioni possono essere progettate in un secondo momento o da terze parti senza modificare il linguaggio DSL esteso.

 Le funzionalità aggiuntive possono includere quanto segue:

- Proprietà per gli elementi del modello e della presentazione

- Elementi Decorator per forme e connettori

- Classi, relazioni, forme e connettori

- Vincoli di convalida

- Elementi e schede della casella degli strumenti

  Un utente di un linguaggio DSL esteso può creare e salvare un modello che contiene istanze delle funzionalità aggiuntive, che possono essere lette da altri utenti che hanno installato l'estensione appropriata. Gli utenti che non hanno installato l'estensione non possono usare le funzionalità aggiuntive, ma possono aggiornare e salvare un modello senza perdere le funzionalità aggiuntive.

  Per il codice di esempio e altre informazioni su questa funzionalità, vedere il sito Web dell' [SDK di visualizzazione e modellazione di Visual Studio](https://www.microsoft.com/en-us/download/details.aspx?id=48148) .

## <a name="see-also"></a>Vedere anche
 [SDK di visualizzazione e modellazione di Visual Studio](https://www.microsoft.com/en-us/download/details.aspx?id=48148)
