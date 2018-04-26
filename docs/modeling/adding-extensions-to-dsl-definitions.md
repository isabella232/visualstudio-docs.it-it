---
title: Aggiunta di estensioni alle definizioni DSL
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: dc764df3037baeba36666ce896549018d86c2a21
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2018
---
# <a name="add-extensions-to-dsl-definitions"></a>Aggiungere estensioni alle definizioni di DSL

Definizione DSL estensione consente di creare un pacchetto di estensioni da un linguaggio specifico di dominio (DSL). L'estensione del linguaggio DSL, incluso in Visual Studio Integration Extension (VSIX), può essere installato nel computer dell'utente nello stesso modo come un linguaggio DSL. Le funzionalità aggiuntive possono essere abilitate e disabilitate in fase di esecuzione in modo dinamico. DSL che debbano essere progettate in modo esplicito per l'estensione e le estensioni possono essere progettate in un secondo momento o da terze parti, senza alterare il DSL estesa.

Le estensioni del linguaggio DSL può includere le funzionalità seguenti:

-   Proprietà degli elementi di modello e la presentazione

-   Elementi Decorator di forme e connettori

-   Le classi, le relazioni, forme e connettori

-   Vincoli di convalida

-   Schede e gli elementi della casella degli strumenti

Un utente di un'estesa DSL possa creare e salvare un modello che contiene istanze delle caratteristiche aggiuntive. Il modello può essere letti da altri utenti che hanno installato l'estensione appropriato. Gli utenti che non hanno installato l'estensione non è possibile utilizzare le funzionalità aggiuntive, ma possono aggiornare e salvare un modello senza perdere le funzionalità aggiuntive.

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

## <a name="see-also"></a>Vedere anche

- [Post di blog correlati](https://blogs.msdn.microsoft.com/visualstudioalm/tag/code-index/)
