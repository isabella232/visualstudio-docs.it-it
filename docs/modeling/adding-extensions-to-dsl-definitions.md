---
title: Aggiunta di estensioni alle definizioni DSL
description: Informazioni su come l'estensione DSL Definition consente di creare un pacchetto di estensioni per un linguaggio specifico di dominio (DSL).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 4d9f1c92ebb879517d497af41fe98cec4492bd95
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2021
ms.locfileid: "112384889"
---
# <a name="add-extensions-to-dsl-definitions"></a>Aggiungere estensioni alle definizioni DSL

L'estensione DSL Definition consente di creare un pacchetto di estensioni per un linguaggio specifico di dominio (DSL). L'estensione DSL, contenuta in un'estensione VSIX (Visual Studio Integration Extension), può essere installata nel computer di un utente allo stesso modo di un DSL. Le funzionalità aggiuntive possono essere abilitate e disabilitate dinamicamente in fase di esecuzione. Le DSL non devono essere progettate in modo esplicito per l'estensione e le estensioni possono essere progettate in un secondo momento o da terze parti, senza modificare il linguaggio DSL esteso.

Le estensioni DSL possono includere le funzionalità seguenti:

- Proprietà per gli elementi del modello e della presentazione

- Elementi Decorator per forme e connettori

- Classi, relazioni, forme e connettori

- Vincoli di convalida

- Schede e elementi della casella degli strumenti

Un utente di un DSL esteso può creare e salvare un modello che contiene istanze delle funzionalità aggiuntive. Il modello può essere letto da altri utenti che hanno installato l'estensione appropriata. Gli utenti che non hanno installato l'estensione non possono usare le funzionalità aggiuntive, ma possono aggiornare e salvare un modello senza perdere le funzionalità aggiuntive.

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

## <a name="see-also"></a>Vedi anche

- [Post di blog correlati](https://devblogs.microsoft.com/devops/the-visual-studio-modeling-sdk-is-now-available-with-visual-studio-2017/)
