---
title: Abilitazione del debug di un programma | Microsoft Docs
description: Informazioni su come avviare il motore di debug o collegare il motore di debug a un programma esistente per eseguire il debug di un programma.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], enabling for programs
ms.assetid: 61d24820-0cd9-48b6-8674-6813f7493237
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 2c09fd6f9862fb3c3426b74bb7c0f62e947bc6050ea02edcbc81990f283bee58
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121343012"
---
# <a name="enable-a-program-to-be-debugged"></a>Abilitare il debug di un programma
Prima che il motore di debug possa eseguire il debug di un programma, è necessario avviare DE o collegarlo a un programma esistente.

## <a name="in-this-section"></a>Contenuto della sezione
 [Ottenere una porta](../../extensibility/debugger/getting-a-port.md) Viene illustrato come ottenere una porta come primo passaggio per abilitare il debug di un programma.

 [Registrare il programma](../../extensibility/debugger/registering-the-program.md) Viene illustrato il passaggio successivo per abilitare il debug di un programma: la registrazione con la porta. Dopo la registrazione, è possibile eseguire il debug del programma tramite il processo di connessione o il debug JIT(Just-In-Time).

 [Collegarsi al programma](../../extensibility/debugger/attaching-to-the-program.md) Viene illustrato il passaggio successivo: collegamento del debugger al programma.

 [Collegamento basato su avvio](../../extensibility/debugger/launch-based-attachment.md) Descrive l'allegato basato sul lancio a un programma, che è automatico all'avvio da parte di SDM.

 [Inviare gli eventi necessari](../../extensibility/debugger/sending-the-required-events.md) Illustra gli eventi necessari quando si crea un motore di debug e lo si collega a un programma.

## <a name="related-sections"></a>Sezioni correlate
 [Creazione di un motore di debug personalizzato](../../extensibility/debugger/creating-a-custom-debug-engine.md) Definisce un motore di debug e descrive i servizi implementati tramite le interfacce DE e il modo in cui possono causare la transizione del debugger tra modalità operative diverse.
