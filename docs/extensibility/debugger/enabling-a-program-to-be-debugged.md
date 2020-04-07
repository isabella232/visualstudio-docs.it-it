---
title: Abilitazione di un programma per il debug Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], enabling for programs
ms.assetid: 61d24820-0cd9-48b6-8674-6813f7493237
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 17c6218cd0b25c0cf0134351fd5efd7490b6a1f3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738889"
---
# <a name="enable-a-program-to-be-debugged"></a>Abilitare il debug di un programmaEnable a program to be debugged
Prima che il motore di debug (DE) possa eseguire il debug di un programma, è necessario avviare il DE o collegarlo a un programma esistente.

## <a name="in-this-section"></a>Contenuto della sezione
 [Ottenere una portaGet a port](../../extensibility/debugger/getting-a-port.md) Viene illustrato come ottenere una porta come primo passaggio per consentire il debug di un programma.

 [Registrare il programma](../../extensibility/debugger/registering-the-program.md) Viene illustrato il passaggio successivo nell'abilitazione di un programma da sottoporre a debug: la registrazione con la porta. Una volta registrato, il programma può essere sottoposto a debug dal processo di collegamento o jIT (Just-In-Time) di debug.

 [Collegamento al programma](../../extensibility/debugger/attaching-to-the-program.md) Viene illustrato il passaggio successivo: collegamento del debugger al programma.

 [Collegamento basato sul lancio](../../extensibility/debugger/launch-based-attachment.md) Descrive l'allegato basato sul lancio di un programma, che viene automatico all'avvio da parte del modello SDM.

 [Inviare gli eventi richiesti](../../extensibility/debugger/sending-the-required-events.md) Vengono dettagliati gli eventi necessari durante la creazione di un motore di debug (DE) e il collegamento a un programma.

## <a name="related-sections"></a>Sezioni correlate
 [Creazione di un motore di debug personalizzatoCreating a custom debug engine](../../extensibility/debugger/creating-a-custom-debug-engine.md) Definisce un motore di debug (DE) e descrive i servizi implementati tramite le interfacce DE e come possono causare la transizione del debugger tra diverse modalità operative.
