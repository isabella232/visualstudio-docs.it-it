---
title: Aggiunta di estensioni alle definizioni DSL
ms.date: 11/04/2016
ms.topic: conceptual
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f3e44c79783479c46247e4026788725d6ae16da7
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2019
ms.locfileid: "72747646"
---
# <a name="add-extensions-to-dsl-definitions"></a>Aggiungere estensioni alle definizioni DSL

L'estensione di definizione DSL consente di creare un pacchetto di estensioni a un linguaggio specifico di dominio (DSL). L'estensione DSL, che è contenuta in un progetto VSIX (Visual Studio Integration Extension), può essere installata nel computer di un utente in modo analogo a un linguaggio DSL. Le funzionalità aggiuntive possono essere abilitate e disabilitate in modo dinamico in fase di esecuzione. DSLs non devono essere progettati in modo esplicito per l'estensione e le estensioni possono essere progettate in un secondo momento o da terze parti senza alterare il linguaggio DSL esteso.

Le estensioni DSL possono includere le funzionalità seguenti:

- Proprietà per gli elementi del modello e della presentazione

- Elementi Decorator per forme e connettori

- Classi, relazioni, forme e connettori

- Vincoli di convalida

- Elementi e schede della casella degli strumenti

Un utente di un linguaggio DSL esteso può creare e salvare un modello che contiene istanze delle funzionalità aggiuntive. Il modello può essere letto da altri utenti che hanno installato l'estensione appropriata. Gli utenti che non hanno installato l'estensione non possono usare le funzionalità aggiuntive, ma possono aggiornare e salvare un modello senza perdere le funzionalità aggiuntive.

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

## <a name="see-also"></a>Vedere anche

- [Post di Blog correlati](https://devblogs.microsoft.com/devops/the-visual-studio-modeling-sdk-is-now-available-with-visual-studio-2017/)
