---
title: SDK di modellazione per Visual Studio (linguaggi specifici di dominio)
description: Si apprenderà che, usando Modeling SDK per Visual Studio, è possibile creare potenti strumenti di sviluppo basati su modello che è possibile integrare in Visual Studio.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language Tools
- Domain-Specific Language
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.technology: vs-ide-modeling
ms.workload:
- multiple
ms.openlocfilehash: 00e140b3191ef6d40fbd0ee519580dee46345e17
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122047816"
---
# <a name="modeling-sdk-for-visual-studio---domain-specific-languages"></a>SDK di modellazione per Visual Studio (linguaggi specifici di dominio)

Usando Modeling SDK per Visual Studio, è possibile creare potenti strumenti di sviluppo basati su modello che è possibile integrare in Visual Studio. Analogamente, è possibile creare una o più definizioni di modello e integrarle in un set di strumenti.

MSDK è basato sulla definizione di un modello creato per rappresentare i concetti nella propria area aziendale. È possibile racchiudere il modello in un'ampia gamma di strumenti, ad esempio una visualizzazione diagrammatica, la possibilità di generare codice e altri elementi, i comandi per trasformare il modello e la possibilità di interagire con il codice e altri oggetti in Visual Studio. Quando si sviluppa il modello, è possibile combinarlo con altri modelli e strumenti per formare un potente set di strumenti avanzati incentrati sulla propria attività di sviluppo.

MSDK consente di compilare rapidamente un modello nel formato di linguaggio specifico di dominio (DSL). Iniziare utilizzando un editor specifico per definire uno schema o una sintassi astratta insieme a una notazione grafica. Utilizzando questa definizione, VMSDK genera:

- Implementazione di modello con un'API fortemente tipizzata eseguita in un archivio basato sulle transazioni.

- Finestra di esplorazione ad albero.

- Editor grafico in cui gli utenti possono visualizzare il modello o parti definite.

- Metodi di serializzazione che salvano i modelli in XML leggibile.

- Funzionalità per generare codice di programma e altri elementi utilizzando il modello di testo.

Tutte queste funzionalità possono essere personalizzate ed estese. Le estensioni sono integrate in modo che sia comunque possibile aggiornare la definizione DSL e rigenerare le funzionalità senza perdere le estensioni.

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

[Post di blog correlati](https://devblogs.microsoft.com/devops/the-visual-studio-modeling-sdk-is-now-available-with-visual-studio-2017/)
