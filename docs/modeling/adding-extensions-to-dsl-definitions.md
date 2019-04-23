---
title: Aggiunta di estensioni alle definizioni DSL
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fa5c02fc28e7ffec4765d94758c838ab149e7ac3
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60064193"
---
# <a name="add-extensions-to-dsl-definitions"></a>Aggiungere estensioni alle definizioni DSL

Estensione di definizione DSL consente di creare un pacchetto di estensioni da un linguaggio specifico di dominio (DSL). L'estensione del linguaggio DSL, incluso in Visual Studio Integration Extension (VSIX), può essere installato nel computer dell'utente nello stesso modo come un linguaggio DSL. Le funzionalità aggiuntive possono essere abilitate e disabilitate in fase di esecuzione in modo dinamico. Linguaggi specifici di dominio non devono essere progettate in modo esplicito per l'estensione e le estensioni possono essere progettate in un secondo momento o da terze parti, senza alterare il DSL esteso.

Le estensioni di linguaggio specifico di dominio possono includere le funzionalità seguenti:

- Proprietà degli elementi di modello e la presentazione

- Elementi Decorator per forme e connettori

- Le classi, le relazioni, forme e connettori

- Vincoli di convalida

- Schede ed elementi della casella degli strumenti

Un utente di un DSL estesa può creare e salvare un modello che contiene le istanze delle funzionalità aggiuntive. Il modello può essere letto da altri utenti che hanno installato l'estensione corretta. Gli utenti che non hanno installato l'estensione non è possibile usare le funzionalità aggiuntive, ma possono aggiornare e salvare un modello senza perdere le funzionalità aggiuntive.

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

## <a name="see-also"></a>Vedere anche

- [Post di blog correlati](https://devblogs.microsoft.com/devops/the-visual-studio-modeling-sdk-is-now-available-with-visual-studio-2017/)
