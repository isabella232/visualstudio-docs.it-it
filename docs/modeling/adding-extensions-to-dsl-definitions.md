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
ms.openlocfilehash: 9e4c80dee056d559822006627c86f4b4884942c8
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53991136"
---
# <a name="add-extensions-to-dsl-definitions"></a>Aggiungere estensioni alle definizioni DSL

Estensione di definizione DSL consente di creare un pacchetto di estensioni da un linguaggio specifico di dominio (DSL). L'estensione del linguaggio DSL, incluso in Visual Studio Integration Extension (VSIX), può essere installato nel computer dell'utente nello stesso modo come un linguaggio DSL. Le funzionalità aggiuntive possono essere abilitate e disabilitate in fase di esecuzione in modo dinamico. Linguaggi specifici di dominio non devono essere progettate in modo esplicito per l'estensione e le estensioni possono essere progettate in un secondo momento o da terze parti, senza alterare il DSL esteso.

Le estensioni di linguaggio specifico di dominio possono includere le funzionalità seguenti:

-   Proprietà degli elementi di modello e la presentazione

-   Elementi Decorator per forme e connettori

-   Le classi, le relazioni, forme e connettori

-   Vincoli di convalida

-   Schede ed elementi della casella degli strumenti

Un utente di un DSL estesa può creare e salvare un modello che contiene le istanze delle funzionalità aggiuntive. Il modello può essere letto da altri utenti che hanno installato l'estensione corretta. Gli utenti che non hanno installato l'estensione non è possibile usare le funzionalità aggiuntive, ma possono aggiornare e salvare un modello senza perdere le funzionalità aggiuntive.

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

## <a name="see-also"></a>Vedere anche

- [Post di blog correlati](https://blogs.msdn.microsoft.com/visualstudioalm/tag/code-index/)
