---
title: Aggiunta di estensioni alle definizioni DSL
ms.date: 11/04/2016
ms.topic: conceptual
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 767973705d004a46644a51ba20ad9292ab80cb39
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72654361"
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
